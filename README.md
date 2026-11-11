# Expense Tracker

A Java and Spring Boot project scaffold for an expense tracker. The supplied project archive currently contains the Spring Boot application entry point and database configuration, but it does not include expense model, repository, controller, or web template implementations. The README describes only what is present in that archive.

## Table of Contents

- [Overview](#overview)
- [Implemented Features](#implemented-features)
- [Technology Stack](#technology-stack)
- [Architecture](#architecture)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Database Setup](#database-setup)
- [Installation and Run](#installation-and-run)
- [Screenshots](#screenshots)
- [Future Improvements](#future-improvements)
- [Author](#author)

## Overview

The project is configured as a Spring Boot web application named `expense-tracker`. It includes dependencies for Spring MVC, Thymeleaf, validation, Spring Data JPA, and the MySQL JDBC driver. The current archive does not yet contain expense-tracking screens or expense-management code.

## Implemented Features

- Spring Boot application entry point in package `com.expensetracker.expense_tracker`.
- MySQL datasource configuration targeting the `expense_tracker` database.
- Hibernate schema update mode and SQL logging configuration.
- A Spring Boot context-load test.

Expense creation, listing, editing, deletion, dashboard totals, and expense tables are not implemented in the supplied archive and are not documented as existing features.

## Technology Stack

| Technology | Project configuration |
| --- | --- |
| Java | 25 (as configured in `pom.xml`) |
| Spring Boot | 4.1.1 (as configured in `pom.xml`) |
| Build tool | Maven, with Maven Wrapper scripts included |
| Persistence | Spring Data JPA / Hibernate |
| Database driver | MySQL Connector/J |
| Web | Spring MVC and Thymeleaf |
| Validation | Spring Boot Validation |
| Test support | Spring Boot test dependencies and JUnit 5 |

## Architecture

The application uses Spring Boot's standard application bootstrap. The main class starts the embedded web server; the configured dependencies provide MVC, template rendering, validation, and persistence support. The archive does not contain application-specific controller, entity, repository, or template layers yet.

## Project Structure

```text
expense-tracker/
├── .mvn/
│   └── wrapper/
│       └── maven-wrapper.properties
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/expensetracker/expense_tracker/
│   │   │       └── ExpenseTrackerApplication.java
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── static/       # Present, currently empty
│   │       └── templates/    # Present, currently empty
│   └── test/
│       └── java/com/expensetracker/expense_tracker/
│           └── ExpenseTrackerApplicationTests.java
├── .gitattributes
├── .gitignore
├── HELP.md
├── mvnw
├── mvnw.cmd
└── pom.xml
```

## Prerequisites

- JDK 25, matching the version configured in the Maven project.
- MySQL Server and a database user with permission to connect and create/update tables.
- A terminal (PowerShell or Command Prompt on Windows; shell on macOS/Linux).

The project configuration specifies a MySQL connection but does not enforce a particular MySQL server release. Use the MySQL version installed in your environment.

## Database Setup

Create the database before starting the application:

```sql
CREATE DATABASE expense_tracker;
```

Open `src/main/resources/application.properties` and set the MySQL username and password for your local environment. The supplied password value is a placeholder and must be replaced:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/expense_tracker
spring.datasource.username=root
spring.datasource.password=YOUR_MYSQL_PASSWORD
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

`spring.jpa.hibernate.ddl-auto=update` lets Hibernate update the schema based on mapped entities. No expense entity or table definition is included in the supplied archive, so no expense table is currently specified by the project.

For a local project, avoid committing real database credentials. Use environment-specific configuration or environment variables before sharing the repository.

## Installation and Run

1. Clone or extract the project and open a terminal at the directory containing `pom.xml`.
2. Confirm that JDK 25 is installed and available on your `PATH`.
3. Create the `expense_tracker` database and configure the datasource credentials as described above.
4. Start the application with the Maven Wrapper.

Windows PowerShell or Command Prompt:

```powershell
.\mvnw.cmd spring-boot:run
```

macOS or Linux:

```bash
./mvnw spring-boot:run
```

The application uses Spring Boot's default HTTP port, `8080`, because no custom port is set in the supplied configuration. The archive contains no page templates, so a usable expense-tracker page is not currently provided.

To build the project instead of running it:

```powershell
.\mvnw.cmd clean package
```

On macOS or Linux, run `./mvnw clean package`.

## Author

**Author:** Vaibhav Gupta

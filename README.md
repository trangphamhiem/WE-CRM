# WE-CRM

## Summary
This is a reference project elaborated by the students step-by-step in every FHNW web engineering lecture.

## Process

### Analysis

#### Scenario
WE-CRM (Web Engineering Customer-Relationship-Management) is the smallest possible and lightweight demonstration tool that allows agents to manage their customer data. Agents have an own access to their customer data. Besides, agents can email themselves an complete extract or create a PDF of their customers.

#### Use Case

![](modelling/images/WE-CRM-Use-Case.png)

- UC-1 [Login on WE-CRM]: Agents can log-in by entering an email address and password. As an extension, new agents my register first.
- UC-2 [Register on WE-CRM]: Agents can register to get an account (profile) to access the WE-CRM system.
- UC-3 [Edit a customer]: Agents can create, update and delete customers.
- UC-4 [Show a customer list]: Agents can get an overview over their customers based on a customer list. As an extension they can create, update and delete customers (UC-3), generate a PDF (UC-5) or send an email (UC-6).
- UC-5 [Generate a PDF customer list]: Agents can generate a PDF containing a list of their customers.
- UC-6 [Send customer list via email]: Agents can send an email containing a list of their customers to their own inbox.

### Design

#### Domain Model

![](modelling/images/WE-CRM-Domain-Model.png)

#### ERD

![](modelling/images/WE-CRM-ERD.png)

### Implementation

#### SQL

##### MySQL
```SQL
CREATE TABLE Customer (
  ID      int(10) NOT NULL AUTO_INCREMENT, 
  Name    varchar(255), 
  Email   varchar(255), 
  Mobile  varchar(255), 
  AgentID int(10) NOT NULL, 
  PRIMARY KEY (ID));
CREATE TABLE Agent (
  ID       int(10) NOT NULL AUTO_INCREMENT, 
  Email    varchar(255), 
  Password varchar(255), 
  PRIMARY KEY (ID));
ALTER TABLE Customer ADD INDEX AgentCustomers (AgentID), ADD CONSTRAINT AgentCustomers FOREIGN KEY (AgentID) REFERENCES Agent (ID);
```

##### PostgreSQL
```SQL
CREATE TABLE Customer (
  ID      SERIAL NOT NULL, 
  Name    varchar(255), 
  Email   varchar(255), 
  Mobile  varchar(255), 
  AgentID int4 NOT NULL, 
  PRIMARY KEY (ID));
CREATE TABLE Agent (
  ID       SERIAL NOT NULL, 
  Email    varchar(255), 
  Password varchar(255), 
  PRIMARY KEY (ID));
ALTER TABLE Customer ADD CONSTRAINT AgentCustomers FOREIGN KEY (AgentID) REFERENCES Agent (ID);
```


#### Stage 1: Building a Static Website with Bootstrap

### Evaluation and Deployment

## Releases

### 1.0.0

- Initial version

## Maintainer

- [Andreas Martin](https://github.com/andreasmartin)

## License

- [Apache License, Version 2.0](LICENSE)

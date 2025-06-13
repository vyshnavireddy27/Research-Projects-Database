# 📊 Research Projects Database

This project is a relational database designed to manage and track research projects, employees involved, funding agencies, and managerial responsibilities. The database schema is modeled using an Entity-Relationship approach and implemented in SQL.



## 🏗️ Database Tables Overview

### 📁 `project` Table
| Column Name | Data Type      | Description                       |
|-------------|----------------|-----------------------------------|
| Project_ID  | INT (PK)       | Unique ID of the project          |
| Name        | VARCHAR(100)   | Name of the project               |
| Duration    | INT            | Duration of the project (months)  |
| Budget      | DECIMAL(12,2)  | Budget allocated to the project   |



### 📁 `fundingagency` Table
| Column Name | Data Type      | Description                       |
|-------------|----------------|-----------------------------------|
| Agency_ID   | INT (PK)       | Unique ID of the agency           |
| Name        | VARCHAR(100)   | Name of the funding agency        |
| Address     | VARCHAR(255)   | Address of the funding agency     |



### 📁 `employee` Table
| Column Name | Data Type      | Description                       |
|-------------|----------------|-----------------------------------|
| SSN         | INT (PK)       | Social Security Number (Primary Key) |
| Emp_Name    | VARCHAR(50)    | Name of the employee              |
| Salary      | DECIMAL(10,0)  | Employee's salary                 |



### 📁 `employee_project` Table
> Junction table to track which employee works on which project and their project manager.

| Column Name | Data Type | Description                        |
|-------------|-----------|------------------------------------|
| SSN         | INT (FK)  | Refers to `employee.SSN`           |
| Project_ID  | INT (FK)  | Refers to `project.Project_ID`     |
| Manager_SSN | INT       | Manager’s SSN (FK to `employee.SSN`) |



### 📁 `project_manager` Table
> Tracks which employee manages which project.

| Column Name | Data Type | Description                        |
|-------------|-----------|------------------------------------|
| Project_ID  | INT (FK)  | Refers to `project.Project_ID`     |
| Manager_SSN | INT (FK)  | Refers to `employee.SSN`           |



## 🔗 Relationships

- An **employee** can work on multiple **projects** (M:N via `employee_project`)
- A **project** has one **manager** (1:1 via `project_manager`)
- A **funding agency** can fund multiple **projects**, but each **project** is funded by exactly one **agency**
- Project names are **unique within each agency**



## 🛠️ SQL Features Used
- Primary & Foreign Key constraints
- Composite keys (via `employee_project`)
- Normalized schema
- One-to-one and many-to-many relationship modeling



## 🚀 Sample Data Included
Sample `INSERT` statements are provided for:
- Employees
- Funding Agencies
- Projects
- Employee-Project assignments
- Project Managers
![image](https://github.com/user-attachments/assets/f13d0d12-277d-40d0-bbdd-a9a119b71021)




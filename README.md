SQL Analysis 

### **README for SQL Practice Portfolio**

#### **Introduction**
This SQL script demonstrates the creation, manipulation, and querying of a relational database. It focuses on an employee-company-department scenario to explore key SQL concepts like table creation, data insertion, updates, filtering, and advanced queries. This project is ideal for beginners to intermediates looking to strengthen their understanding of SQL.

---

#### **Database Structure**
The script operates on three primary tables:
1. **Employee**:
   - Attributes: `id`, `name`, `city`, `department_id`, `salary`
   - Foreign Key: `department_id` references `department(id)`

2. **Department**:
   - Attributes: `id`, `name`

3. **Company**:
   - Attributes: `id`, `name`, `revenue`

---

#### **SQL Operations in the Script**

1. **Table Creation**:
   - Ensures relationships using **Primary Keys** and **Foreign Keys**.
   - Utilizes `AUTO_INCREMENT` for auto-generating unique `id`s.

2. **Data Insertion**:
   - Populates tables with sample data for employees, departments, and companies.

3. **Data Manipulation**:
   - **Update Operations**:
     - Example: Rename a department.
   - **Delete Operations**:
     - Example: Remove employees with salaries greater than 100,000.

4. **Queries**:
   - **Basic Retrieval**:
     - Query all rows from tables (`SELECT *`).
   - **Filtering**:
     - Use of conditions like `WHERE`, `BETWEEN`, and `LIKE` to filter results.
   - **Aggregate Functions**:
     - Example: Select companies with revenue greater than a threshold.
   - **Joins**:
     - Example: Query employee names alongside department names using both implicit and explicit joins.
   - **Nested Queries**:
     - Example: Retrieve employees working in the same department as another specific employee.

5. **Advanced SQL Techniques**:
   - **DISTINCT**:
     - Query unique department names.
   - **Self Joins**:
     - Example: Pair companies in a list of combinations.
   - **Column Renaming**:
     - Example: Rename query result column as "Company."
   - **EXCEPT (PostgreSQL)**:
     - Exclude specific data from the query result (PostgreSQL-specific).

---

#### **Key Examples from the Script**

1. **Query Employees by Salary Range**:
   - Using `BETWEEN`:
     ```sql
     SELECT * FROM employee WHERE salary BETWEEN 50000 AND 70000;
     ```
   - Without `BETWEEN`:
     ```sql
     SELECT * FROM employee WHERE salary >= 50000 AND salary <= 70000;
     ```

2. **Nested Query Example**:
   Query employees who work in the same department as Peter:
   ```sql
   SELECT * FROM employee
   WHERE department_id IN (
       SELECT department_id FROM employee WHERE name LIKE 'Peter'
   )
   AND name NOT LIKE 'Peter';
   ```

3. **Joins to Link Tables**:
   Query employee names along with their department names:
   ```sql
   SELECT emp.name, dep.name
   FROM employee emp
   JOIN department dep ON emp.department_id = dep.id;
   ```

4. **Advanced Combinations**:
   Pair companies for comparative analysis:
   ```sql
   SELECT com1.name, com2.name
   FROM company com1, company com2
   WHERE com1.name <> com2.name;
   ```

---

#### **Usage Instructions**
1. Run this script on any SQL database (MySQL, PostgreSQL, etc.).
2. Modify table structure or sample data to match specific use cases.
3. Use the provided queries for practice or as templates for real-world applications.

---

#### **Learning Outcomes**
- Creating and managing relational database tables.
- Using constraints like `FOREIGN KEY` and `PRIMARY KEY`.
- Writing queries with filters, joins, and nested subqueries.
- Performing data manipulations like updates and deletes.
- Applying advanced SQL features for real-world scenarios.

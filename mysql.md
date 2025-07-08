Great! Here's a **complete set of MySQL interview questions with clear answers** that are often asked in **Data Science interviews**.

---

## 🔹 **1. What is MySQL? How is it different from SQL?**

**Answer:**

- **MySQL** is an open-source relational database management system (RDBMS).
- **SQL (Structured Query Language)** is the standard language used to interact with relational databases like MySQL.
- Think of SQL as the **language**, and MySQL as the **tool** that uses the language.

---

## 🔹 **2. What are the different data types in MySQL?**

**Answer:**

- **Numeric**: INT, FLOAT, DOUBLE, DECIMAL
- **Date/Time**: DATE, DATETIME, TIMESTAMP, TIME
- **String**: VARCHAR, CHAR, TEXT, BLOB
- **Boolean**: BOOL or BOOLEAN (internally stored as TINYINT)

---

## 🔹 **3. What is a Primary Key and Foreign Key?**

**Answer:**

- **Primary Key**: Uniquely identifies each row in a table. Cannot be NULL.
- **Foreign Key**: A field in one table that refers to the **primary key in another table**, creating a relationship between them.

---

## 🔹 **4. What are the different types of JOINs?**

**Answer:**

- **INNER JOIN**: Returns records with matching values in both tables.
- **LEFT JOIN**: All records from the left table + matching ones from right.
- **RIGHT JOIN**: All records from the right table + matching ones from left.
- **FULL OUTER JOIN**: All records from both tables (not directly supported in MySQL, can be simulated using UNION).

Example:

```sql
SELECT *
FROM employees e
INNER JOIN departments d ON e.dept_id = d.id;
```

---

## 🔹 **5. What is the difference between WHERE and HAVING clause?**

**Answer:**

- **WHERE** filters rows **before** grouping.
- **HAVING** filters groups **after** aggregation (GROUP BY).

Example:

```sql
-- WHERE
SELECT * FROM employees WHERE salary > 50000;

-- HAVING
SELECT dept_id, COUNT(*)
FROM employees
GROUP BY dept_id
HAVING COUNT(*) > 10;
```

---

## 🔹 **6. What is the difference between DELETE, TRUNCATE, and DROP?**

**Answer:**

- `DELETE`: Removes specific rows. Can use WHERE. Slow but recoverable.
- `TRUNCATE`: Removes all rows. Faster, cannot rollback.
- `DROP`: Deletes entire table structure and data.

---

## 🔹 **7. How do you use GROUP BY and ORDER BY?**

**Answer:**

- `GROUP BY`: Groups rows by column values for aggregation.
- `ORDER BY`: Sorts rows by column(s) ascending (ASC) or descending (DESC).

Example:

```sql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id
ORDER BY AVG(salary) DESC;
```

---

## 🔹 **8. What are aggregate functions in MySQL?**

**Answer:**
Functions that return a single value from multiple rows:

- `COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`

---

## 🔹 **9. Find the second highest salary from a table.**

**Answer:**

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

## 🔹 **10. Calculate running total (cumulative sum) of salaries.**

**Answer:**

```sql
SELECT
  employee_id,
  salary,
  SUM(salary) OVER (ORDER BY employee_id) AS running_total
FROM employees;
```

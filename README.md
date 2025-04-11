# task-3-of-elevate-labs
 Objective
The goal of this task is to use SQL to extract, join, and analyze data from a relational e-commerce database. This includes filtering, aggregating, and optimizing queries for better performance.

## 🗂 Dataset Structure
A simulated **E-commerce** database containing 4 main tables:
- `customers`: Customer info (ID, name, email)
- `orders`: Order transactions linked to customers
- `products`: Product catalog with price
- `order_items`: Items per order with quantities

## ✅ SQL Concepts Applied

### 1. Basic SELECT & WHERE
```sql
SELECT name, email FROM customers WHERE name LIKE 'A%';
```

### 2. INNER JOIN
```sql
SELECT c.name, o.order_date, o.total_amount
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id;
```

### 3. LEFT JOIN
```sql
SELECT c.name, o.order_id
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```

### 4. Aggregates
```sql
SELECT customer_id, COUNT(*) AS total_orders, SUM(total_amount) AS total_spent
FROM orders
GROUP BY customer_id
ORDER BY total_spent DESC;
```

### 5. Subquery
```sql
SELECT name FROM customers
WHERE customer_id IN (
    SELECT customer_id FROM orders
    WHERE total_amount > (SELECT AVG(total_amount) FROM orders)
);
```

### 6. View Creation
```sql
CREATE VIEW high_value_customers AS
SELECT customer_id, SUM(total_amount) AS total_spent
FROM orders
GROUP BY customer_id
HAVING total_spent > 200;
```

### 7. Query Optimization
```sql
CREATE INDEX idx_customer_id ON orders(customer_id);
```

## 📸 Screenshots
(Sample screenshots are  added here manually)

## 📁 Files Included
- `task3_queries.sql` — All SQL queries written and tested
- `README.md` — Task overview and explanation

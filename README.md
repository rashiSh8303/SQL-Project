# Project Title 
# Online Book Store Management System
## Table of Contents
   Business Task 
   Entity Relationship Diagram
   Question & Solutions
# Business Task 
The Online Book Store SQL project aims to efficiently manage book sales, customer interactions, and inventory. It provides a structured SQL database to streamline operations for an online book store. 🚀
## Entity Relationship Diagram
(https://github.com/user-attachments/assets/c89b8bbc-1241-4096-b17b-e7b29c418148)
# Questions & Solution 
## Basic Questions 
## 1. Retrieve all books in the "Fiction" genre
## Solution :
           SELECT * FROM Books 
           WHERE Genre='Fiction'; 
## 2.Find books published after the year 1950 
## Solution : 
     SELECT * FROM Books 
     WHERE published_year > 1950;
## 3. List all customers from the Canada  
## Solution : 
    SELECT * FROM customers
    WHERE country = 'Canada';
## 4. Show orders placed in November 2023 
## Solution : 
    SELECT * FROM orders 
    WHERE order_date BETWEEN '2023-11-01' AND '2023-11-30';
## 5. Retrieve the total stock of books available 
    SELECT SUM(stock_quantity) AS total_stock FROM books;
## 6. Find the details of the most expensive book 
## Solution : 
    Select * from Books 
    Order by price DESC LIMIT 1 ;
## 7. Show all customers who ordered more than 1 quantity of a book 
## Solution : 
    Select * from orders
    Where quantity > 1;
## 8. Retrieve all orders where the total amount exceeds $20 
## Solution : 
    Select * from orders 
    Where total_amount > 20;
## 9. Find the book with lowest stock 
## Solution : 
    Select * from Books 
    ORDER BY stock;
## 10. Calculate the total revenue generated from all orders 
## Solution :
    Select SUM(total_amount) AS Revenue FROM Orders; 
## Advance Questions
## 1. Retrieve the total number of books sold for each genre
## Solution : 
     select books.genre, SUM(orders.quantity) AS Total_book_sold
     FROM Orders
     JOIN books ON orders.book_id = books.book_id
    - GROUP BY books.genre; 
## 2. List Customers Who have placed at least 2 orders 
## Solution :
    select orders.customer_id, customers.name, COUNT(orders.order_id) AS order_count
     FROM orders
     JOIN customers ON orders.customer_id = customers.customer_id
     GROUP BY orders.customer_id, customers.name
     HAVING COUNT(order_id) >=2;

## 3. Find the most Frequentily ordered Book
## Solution : 
     SELECT orders.book_id, books.title, COUNT(orders.order_id) AS order_count
     FROM orders
     JOIN books ON orders.book_id = books.book_id
     GROUP BY orders.book_id, books.title
     ORDER BY order_count DESC LIMIT 1;
## 4. Show the top 3 most expensive of 'Fantasy' Genre 
## Solution :
    SELECT * FROM books
    WHERE genre = 'Fantasy'
    ORDER BY price DESC LIMIT 3;
## 5. Retrive the total quantity of books sold by each author
## Solution :
    SELECT books.author, SUM(orders.quantity) AS total_books_sold
    from orders
    join books ON orders.book_id = books.book_id
    GROUP BY books.author;
 
## 6. List the cities where customers who spent over $30 are
## Solution :
    select DISTINCT customers.city, total_amount
     from orders
     join customers ON orders.customer_id = customers.customer_id
     WHERE orders.total_amount > 30;
## 7. Find the customer who spent the most on erders
## Solution :
    select customers.customer_id, customers.name, SUM(orders.total_amount) AS total_spent
     FROM orders
     JOIN customers ON orders.customer_id = customers.customer_id
     GROUP BY customers.customer_id, customers.name
     ORDER BY total_spent DESC LIMIT 1 ;
 

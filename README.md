# Stock Management System: 

## Overview

The Stock Management System is a comprehensive tool designed to manage products, purchases, sales, and users efficiently. This system utilizes a MySQL database for storing and retrieving information related to products, orders, sales, and user accounts. The project includes functionalities for adding, updating, listing, and deleting records in each of these categories, along with the ability to create and manage the database schema.

## Features

1. **Product Management**
   - Add New Product
   - List Products
   - Update Product
   - Delete Product

2. **Purchase Management**
   - Add Order
   - List Orders

3. **Sales Management**
   - Sale Items
   - List Sales

4. **User Management**
   - Add User
   - List Users

5. **Database Setup**
   - Create Database Tables
   - List Database Tables

## Requirements

- Python 3.x
- MySQL Connector for Python (`mysql-connector-python`)

## Setup Instructions

1. **Install MySQL Connector**
   ```bash
   pip install mysql-connector-python
   ```

2. **Database Configuration**
   - Ensure MySQL server is running.
   - Update the MySQL connection details (`host`, `user`, `passwd`, `database`) in the code as per your setup.

3. **Running the Application**
   - Save the provided script into a Python file (e.g., `stock_management.py`).
   - Run the script using Python:
     ```bash
     python stock_management.py
     ```

## Usage Instructions

1. **Main Menu**
   - The main menu provides options for product management, purchase management, sales management, user management, and database setup.

2. **Product Management**
   - Add New Product: Prompts for product details and adds a new product to the database.
   - List Product: Displays all products or allows filtering by product code or category.
   - Update Product: Updates the quantity of an existing product.
   - Delete Product: Deletes a product from the database.

3. **Purchase Management**
   - Add Order: Adds a new order to the database, including product details and supplier information.
   - List Order: Displays all orders with details.

4. **Sales Management**
   - Sale Items: Records a sale, updates product quantity, and logs the transaction.
   - List Sales: Displays all sales transactions with details.

5. **User Management**
   - Add User: Adds a new user to the system.
   - List Users: Displays all users with their details.

6. **Database Setup**
   - Create Database Tables: Creates the necessary tables (`product`, `orders`, `sales`, `user`) if they do not already exist.
   - List Database Tables: Lists all tables in the database.

## Database Schema

- **Product Table**
  ```sql
  CREATE TABLE if not exists product (
      pcode int(4) PRIMARY KEY,
      pname char(30) NOT NULL,
      pprice float(8,2),
      pqty int(4),
      pcat char(30)
  );
  ```

- **Orders Table**
  ```sql
  CREATE TABLE if not exists orders (
      orderid int(4) PRIMARY KEY,
      orderdate DATE,
      pcode char(30) NOT NULL,
      pprice float(8,2),
      pqty int(4),
      supplier char(50),
      pcat char(30)
  );
  ```

- **Sales Table**
  ```sql
  CREATE TABLE if not exists sales (
      salesid int(4) PRIMARY KEY,
      salesdate DATE,
      pcode char(30) references product(pcode),
      pprice float(8,2),
      pqty int(4),
      Total double(8,2)
  );
  ```

- **User Table**
  ```sql
  CREATE TABLE if not exists user (
      uid char(6) PRIMARY KEY,
      uname char(30) NOT NULL,
      upwd char(30)
  );
  ```

## Additional Information

- **Clear Screen Function**
  - The `clrscr()` function is used to clear the console screen for better readability of outputs.
  - Adjust the implementation based on the operating system (e.g., `os.system('cls')` for Windows, `os.system('clear')` for Unix-based systems).

- **Date and Time Handling**
  - The current date and time are used for generating unique order IDs and logging timestamps for orders and sales.

- **Error Handling and Validation**
  - Ensure proper validation and error handling for user inputs and database operations for a robust system.


---

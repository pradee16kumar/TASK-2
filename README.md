1. Customer Table

   CREATE TABLE customers (
    id INT AUTO_INCREMENT PRIMARY KEY
);                 
2. Orders Table
   CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES customers(id)

);

3. Order Lines
   CREATE TABLE order_lines (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product CHAR(1),          
    quantity INT NOT NULL,
    backordered INT DEFAULT 0, 
    FOREIGN KEY (order_id) REFERENCES orders(id)
);
4. Inventory Table
   CREATE TABLE inventory (
    product CHAR(1) PRIMARY KEY, 
    quantity INT NOT NULL
);


INSERT INTO inventory (product, quantity) VALUES
('A', 15),
('B', 15),
('C', 10),
('D', 10),
('E', 20);


5. Order Report Table

CREATE TABLE order_report (
    product CHAR(1) PRIMARY KEY,  
    initial_quantity INT NOT NULL,
    total_order INT DEFAULT 0,     
    total_backorder INT DEFAULT 0 
);


INSERT INTO order_report (product, initial_quantity) VALUES
('A', 15),
('B', 15),
('C', 10),
('D', 10),
('E', 20);

6. Customer Report Table
   CREATE TABLE customer_report (
    customer_id INT PRIMARY KEY,  
    order_count_a INT DEFAULT 0,   
    order_count_b INT DEFAULT 0,  
    order_count_c INT DEFAULT 0,   
    order_count_d INT DEFAULT 0,   
    order_count_e INT DEFAULT 0   
);



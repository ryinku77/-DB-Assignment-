# Answers to Questions

## 1. Explain the relationship between the "Product" and "Product_Category" entities.
In the schema, the "Product" entity contains a foreign key column named "category_id," which references the primary key of the "Product_Category" entity. This establishes a one-to-many relationship between products and categories, where each product belongs to one category, but each category can have multiple products associated with it.

## 2. How could you ensure that each product in the "Product" table has a valid category assigned to it?
To ensure that each product in the "Product" table has a valid category assigned to it, you can enforce referential integrity using a foreign key constraint. 
By creating a foreign key constraint on the "category_id" column in the "Product" table, referencing the primary key of the "Product_Category" table, the database will ensure that only valid category IDsc
an be assigned to products. Any attempt to insert or update a product with an invalid category ID will result in a constraint violation error, preventing the operation from completing.

Answer:-
-- Create Product_Category table
CREATE TABLE Product_Category (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create Product table
CREATE TABLE Product (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    category_id INT REFERENCES Product_Category(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

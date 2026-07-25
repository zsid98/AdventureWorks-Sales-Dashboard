# AdventureWorks Sales Dashboard

## Overview
This project demonstrates the development of an interactive sales dashboard in Power BI using the AdventureWorks Dataset for Data Analysis. The focus was on building a clean data model, creating DAX measures, and presenting key business metrics through an executive-style dashboard.

## Data Source
- **Dataset:** Adventureworks Dataset for Data Analysis
- **Source:** Maven Analytics
- **Format:** CSV
- **Period:** 2020–2022
- **Files Used:**
  - Sales (2020–2022, appended into a single fact table)
  - Products
  - Customers
  - Territories
  - Calendar
  - Product Categories
  - Product Subcategories
 - **Source:** https://www.kaggle.com/datasets/shaikhshoeb/adventureworks-dataset-for-data-analysis

## Objectives
- Build a star schema from multiple CSV files.
- Create reusable DAX measures for key sales metrics.
- Design an executive dashboard summarizing sales performance from 2020–2022.
- Analyze sales trends, profitability, and regional performance.

## Data Preparation
The source files required minimal cleaning before analysis. The following transformations were performed in Power Query:
- Reviewed source tables and verified data structure.
- Removed unnecessary blank values where applicable.
- Corrected data types for numerical fields and dates.
- Appended yearly sales files (2020–2022) into a single Sales fact table.
- Removed the Product Description column from the Products table as it was not required for analysis.
- Disabled loading of intermediate yearly sales queries to maintain a clean data model.


## Data Model
The dataset was modeled using a star schema with Sales as the central fact table and Calendar, Customers, Products, and Territories as dimension tables.
The product dimension contains a hierarchy through Product Subcategories and Product Categories, creating a small snowflake structure for product analysis.
The Sales fact table contained multiple date fields. OrderDate was selected as the active relationship because the report focuses on sales performance. StockDate was not included in the current model as it represents a separate operational process.

<img width="1205" height="625" alt="image" src="https://github.com/user-attachments/assets/d2e03197-092b-4595-824d-72c6a2d511be" />


## DAX Measures
The following measures were created to support sales performance and profitability analysis.
The Sales table uses an order-line level grain, meaning each row represents an individual product line within an order rather than the entire order. For example, an order containing multiple products will appear as multiple rows. This distinction is important when calculating metrics such as total orders and units sold.

### Sales and Profitability Metrics

- **Total Sales**  
  Calculates total revenue generated from all order lines.

- **Total Cost**  
  Calculates the total product cost associated with sold items.

- **Gross Profit**  
  Represents the difference between total sales and total cost.

- **Gross Margin %**  
  Shows gross profit as a percentage of total sales.

### Order Metrics

- **Total Orders**  
  Counts unique orders using the order identifier rather than counting individual order lines.

- **Average Order Value**  
  Calculates the average revenue generated per order by dividing total sales by the number of unique orders.

- **Units Sold**  
  Calculates the total quantity of individual items sold across all order lines.

## Dashboard

## Key Business Insights

Introduction of accessories and clothing beginning in 2021 coincided with a noticeable increase in overall gross margin. While bikes continued to generate the vast majority of revenue, accessories contributed significantly to unit sales and exhibited the highest gross margin percentage.

## Skills Demonstrated

## Future Improvements

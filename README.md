# Business Problem

This project was built for the HCL Hackathon using the Superstore dataset.

The goal was to solve key business challenges like:
- Inconsistent profit calculations
- Lack of interactive dashboards
- High discount causing losses
- Identifying top and low-performing products
- Monitoring delivery performance

The solution focuses on building a reliable and interactive Power BI report.
# Data Description

Dataset: Sample Superstore

Includes:
- Orders, Products, Customers, Regions
- Metrics: Sales, Profit, Quantity, Discount
- Dates: Order Date, Ship Date

Used for sales, profitability, and trend analysis.
# Data Model

- Used a simple star schema
- Orders as fact table
- Product, Region, Date as dimension tables

This helps in:
- Better performance
- Accurate calculations
- # Key DAX Measures

Total Sales = SUM(Orders[Sales])  
Total Profit = SUM(Orders[Profit])  

Product Rank = RANKX(ALL(Orders[Product Name]), [Total Sales], , DESC)

Rolling 12M Sales =  
CALCULATE([Total Sales], DATESINPERIOD('Date'[Date], MAX('Date'[Date]), -12, MONTH))

Shipping Days = DATEDIFF(Orders[Order Date], Orders[Ship Date], DAY)

 # Key Insights

- High discounts lead to losses in some regions
- Few products generate most of the revenue (Pareto)
- Some regions have delayed shipping
- Stable KPIs improve trust in reports

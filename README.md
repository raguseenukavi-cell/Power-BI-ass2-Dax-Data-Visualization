# E-Commerce Sales Performance Analysis | Power BI

## Project Overview
This project analyzes E-Commerce sales performance using Microsoft Power BI and DAX (Data Analysis Expressions). It builds on an earlier data preparation and modeling assignment to examine revenue, profitability, sales targets, order patterns, and geographic sales performance.

The project demonstrates data modeling, DAX calculations, interactive dashboard development, and business intelligence reporting.

## Project Objectives
- Analyze total sales, profit, and order counts.
- Compare actual sales against sales targets.
- Identify profitable product categories and sub-categories.
- Monitor monthly sales trends and year-to-date sales.
- Evaluate geographic sales performance.
- Create interactive visualizations to support business decisions.

## Tools and Technologies
- Microsoft Power BI Desktop
- Power Query Editor
- DAX (Data Analysis Expressions)
- CSV datasets
- Data modeling and visualization
- GitHub

## Dataset Description
The project uses three related datasets:

1. List of Orders: Order ID, Order Date, CustomerName, State, City.
2. Order Details: Order ID, Amount, Profit, Quantity, Category, Sub-Category.
3. Sales Target: Category, Month of Order Date, Target.

The uploaded List of Orders dataset contains 560 records and Order Details contains 1,500 line items. The previous assignment requires restricting List of Orders to the first 500 records.

## Data Preparation and Modeling
- Imported source files into Power BI.
- Cleaned and formatted data in Power Query.
- Corrected data types and handled missing values.
- Created relationships between relevant tables.
- Prepared a model for DAX calculations and reporting.
- Reviewed date and category relationships for target comparisons.

## DAX Calculated Columns

### Category Type
```dax
Category Type = 'Order Details'[Category] & " - " & 'Order Details'[Sub-Category]
```

### Revenue per Order Line
```dax
Revenue per Order = 'Order Details'[Amount] * 'Order Details'[Quantity]
```

### Sales Category
```dax
Sales Category =
IF(
    'Order Details'[Amount] > CALCULATE(AVERAGE('Order Details'[Amount]), ALL('Order Details')),
    "Above Average",
    "Below Average"
)
```

## DAX Measures

### Order Count
```dax
Order Count = DISTINCTCOUNT('Order Details'[Order ID])
```

### Total Sales
```dax
Total Sales = SUM('Order Details'[Amount])
```

### Total Profit
```dax
Total Profit = SUM('Order Details'[Profit])
```

### Total Quantity
```dax
Total Quantity = SUM('Order Details'[Quantity])
```

### Average Profit in Delhi
```dax
Average Profit in Delhi =
CALCULATE(
    AVERAGE('Order Details'[Profit]),
    'List of Orders'[City] = "Delhi"
)
```

### YTD Sales
```dax
YTD Sales = TOTALYTD([Total Sales], 'Calendar'[Date])
```

### Total Sales Target
```dax
Total Sales Target = SUM('Sales Target'[Target])
```

### Sales Target Achievement
```dax
Target Achievement % = DIVIDE([Total Sales], [Total Sales Target], 0)
```

### Profit Margin
```dax
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
```

### Maximum Profit Margin
```dax
Max Profit Margin % =
MAXX(
    'Order Details',
    DIVIDE('Order Details'[Profit], 'Order Details'[Amount])
)
```

### Minimum Target
```dax
Minimum Target = MIN('Sales Target'[Target])
```

## Dashboard Visualizations

| Visualization | Business Purpose |
|---|---|
| Clustered Column Chart | Compare actual sales and sales targets by category |
| Donut Chart | Analyze maximum profit margin by sub-category |
| Line Chart | Track monthly sales trends |
| Scatter Chart | Compare profit and quantity by sub-category |
| KPI Cards | Display total sales and total target |
| Multi-Row Card | Show minimum targets by category |
| Matrix | Compare category-wise and monthly sales against targets |
| Map | Analyze geographic sales performance by city |
| Treemap | Examine sales distribution across sub-categories |
| Funnel Chart | Analyze order counts by state |

## Business Insights to Investigate
- Which product categories generate the highest sales?
- Which sub-categories have the strongest profit margins?
- Which months record higher or lower sales?
- Which categories meet or miss their sales targets?
- Which cities and states contribute the most orders and revenue?
- How does quantity sold relate to profitability?

## Project Deliverables
- Power BI report (.pbix)
- Dashboard screenshots
- DAX formula screenshots
- PDF report explaining visualizations and insights
- Source CSV datasets

## Skills Demonstrated
Power BI | Power Query | DAX | Data Cleaning | Data Modeling | Data Visualization | KPI Analysis | Business Intelligence | Sales Analytics | Dashboard Design

## Conclusion
This project demonstrates practical Power BI skills by transforming E-Commerce data into interactive analytical reports. It supports business performance monitoring through sales, profit, target, geographic, and product-level analysis.

## Author
Aspiring Data Analyst | Power BI | Excel | SQL | Python

## Project Status
Portfolio project — update the dashboard screenshots, results, and report files after completing and validating the Power BI report.
# Power-BI-ass2-Dax-Data-Visualization

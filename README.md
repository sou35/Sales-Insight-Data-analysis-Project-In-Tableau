# Sales-Insight-Data-analysis-Project-In-Tableau
This project will give you a feel of how data analysis projects are executed in big companies. Our case study is based on a computer hardware business which is facing challenges in dynamically changing market. we will plug MySQL database with tableau. we will directly use mysql database. We will do sales analysis.

You can See the [Sales Insight Analysis Data Project](https://public.tableau.com/views/SalesInsight_16339747843400/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link)

## Instructions to setup mysql on your local computer
1. Follow step in this Documentation to install mysql on your local computer [MySQL Installation Guide](https://dev.mysql.com/doc/mysql-installation-excerpt/5.7/en/)

2. SQL database dump is in db_dump.sql file above. Download [db_dump.sql](db_dump.sql) file to your local computer and import it .

## Instructions: How to connect Tableau to a MySQL database and set up the data source.
This article describes how to connect Tableau to a MySQL database and set up the data source.[Make the connection and set up the data source](https://help.tableau.com/current/pro/desktop/en-us/examples_mysql.ht)

## Data Analysis Using SQL
### Show all customer records
```
SELECT * FROM customers;
```

### Show total number of customers
```
SELECT count(*) FROM customers;
```

### Show transactions for Chennai market (market code for chennai is Mark001)
```
SELECT * FROM transactions where market_code='Mark001';
```
### Show distrinct product codes that were sold in chennai
```
SELECT distinct product_code FROM transactions where market_code='Mark001';
```
### Show transactions where currency is US dollars
```
SELECT * from transactions where currency="USD"
```

### Show transactions in 2020 join by date table
```
SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;
```
### Show total revenue in year 2020,
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date
 where date.year=2020 and transactions.currency='INR\r' or transactions.currency='USD\r';
```
### Show total revenue in year 2020, January Month,
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");
```
### Show total revenue in year 2020 in Chennai
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

```

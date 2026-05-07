# 🛍️ Customer Behaviour Analysis

A comprehensive end-to-end data analytics project that explores customer shopping behaviour using **SQL (SQL Server)** and **Power BI**. The project uncovers actionable insights around purchasing patterns, customer segmentation, discount effectiveness, subscription behaviour, and revenue attribution across demographics.

---

## 📌 Project Overview

This project analyzes a retail customer dataset to answer key business questions such as:
- Which product categories and items drive the most revenue?
- Do discounts actually increase purchase value?
- Are subscribed customers more valuable than non-subscribers?
- How do demographics (age, gender) influence spending?
- Which customers are loyal vs. new vs. returning?

---

## 🗂️ Repository Structure

```
customer_behaviour_analysis/
│
├── customer_behaviour_analysis.sql   # All SQL queries (12 business questions)
├── customer_shopping.pbix            # Power BI dashboard
└── README.md                         # Project documentation
```

---

## 🧰 Tech Stack

| Tool | Purpose |
|------|---------|
| **SQL Server (T-SQL)** | Data querying, aggregation, segmentation |
| **Power BI** | Interactive dashboard and data visualization |
| **CTEs & Window Functions** | Advanced SQL analysis |

---

## 📊 Dataset

**Table:** `customer_behaviour_analysis`  
**Database:** `ecom_sales`

The dataset contains transactional and demographic data for retail customers, including:

| Column | Description |
|--------|-------------|
| `customer_id` | Unique identifier for each customer |
| `age` | Customer's age |
| `gender` | Customer's gender |
| `item_purchased` | Name of the purchased product |
| `category` | Product category |
| `purchase_amount` | Transaction value (USD) |
| `review_rating` | Customer review score |
| `subscription_status` | Whether customer has an active subscription |
| `discount_applied` | Whether a discount was used (`Yes` / `No`) |
| `shipping_type` | Shipping method (e.g., Express, Standard) |
| `previous_purchases` | Number of prior transactions |

---

## 🔍 SQL Analysis — Business Questions Answered

### 1. 📦 Highest Revenue by Category
Identifies which product categories generate the most sales revenue using `SUM(purchase_amount)` grouped by category.

### 2. 🏷️ Discount Impact on Revenue
Compares total revenue between discounted and non-discounted purchases to determine if discounts are driving more spend.

### 3. 👥 Revenue by Gender
Breaks down total revenue contribution by male and female customers.

### 4. 💡 High Spenders Who Used Discounts
Uses a **subquery** to find customers who applied a discount but still spent above the average purchase amount — identifying high-value, deal-seeking customers.

### 5. ⭐ Top & Bottom 5 Products by Review Rating
Uses `TOP 5` with `AVG(review_rating)` to surface both highest and lowest rated products — useful for quality and marketing decisions.

### 6. 🚚 Average Purchase by Shipping Type
Compares average order value and total customers between **Express** and **Standard** shipping to understand fulfilment preference patterns.

### 7. 📋 Subscriber vs. Non-Subscriber Spend
Compares average purchase amount and total revenue across subscription tiers to evaluate the value of the subscription program.

### 8. 🎯 Top 5 Products with Highest Discount Usage
Calculates discount usage rate per product using conditional `COUNT(CASE WHEN ...)` and percentage calculation — identifying products most reliant on promotions.

### 9. 🧩 Customer Segmentation
Segments customers into three groups using a `CASE` statement:
- **New Customers** — 0 previous purchases
- **Returning Customers** — 1 to 15 previous purchases
- **Loyal Customers** — 16+ previous purchases

### 10. 🏆 Top 3 Products Per Category
Uses a **CTE + RANK() window function** partitioned by category to surface the 3 best-selling items in each product category.

### 11. 🔁 Frequent Buyers & Subscription Likelihood
Examines whether customers with more than 5 previous purchases are more likely to hold an active subscription — linking loyalty with subscription conversion.

### 12. 📅 Revenue by Age Group
Segments customers into age bands (18–25, 26–35, 36–50, 51+) and calculates total revenue per group to guide age-targeted marketing strategies.

---

## 📈 Power BI Dashboard

The `customer_shopping.pbix` file contains an interactive dashboard built on the same dataset, providing visual representations of:
- Revenue trends by category and product
- Customer segmentation breakdown
- Gender and age-based spending comparisons
- Discount effectiveness visuals
- Subscription vs. non-subscription revenue

> Open with **Power BI Desktop** (free download from [Microsoft](https://powerbi.microsoft.com/desktop/)).

---

## 🚀 Getting Started

### Prerequisites
- SQL Server (any edition) or Azure Data Studio
- Power BI Desktop

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/sumran58/customer_behaviour_analysis.git
   cd customer_behaviour_analysis
   ```

2. **Create the database and load data**
   ```sql
   CREATE DATABASE ecom_sales;
   USE ecom_sales;
   -- Import the dataset into the table: customer_behaviour_analysis
   ```

3. **Run the SQL queries**
   Open `customer_behaviour_analysis.sql` in SQL Server Management Studio (SSMS) or Azure Data Studio and execute the queries.

4. **Open the Power BI Dashboard**
   Open `customer_shopping.pbix` in Power BI Desktop. Connect to your SQL Server instance if prompted.

---

## 💡 Key Insights

- Certain product categories consistently outperform others in revenue generation.
- Discounts do not always lead to higher total spend — non-discounted purchases may generate comparable or higher revenue.
- Subscribed customers show meaningfully different spending behaviour compared to non-subscribers.
- The 36–50 age group tends to be the highest revenue-contributing demographic.
- A significant portion of customers fall in the "returning" segment, indicating moderate retention.

---

## 🙋 Author

**Sumran**  
GitHub: [@sumran58](https://github.com/sumran58)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

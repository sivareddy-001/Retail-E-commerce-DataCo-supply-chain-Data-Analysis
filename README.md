# Retail E-Commerce Data – Supply Chain Data Analysis

## 📌 Project Overview

This project focuses on the analysis and preprocessing of retail e-commerce supply chain data.

The objective is to transform raw supply chain data into a clean, consistent, and analysis-ready dataset. The project covers data inspection, data cleaning, missing-value treatment, duplicate checking, data-type conversion, standardization, and validation.

The cleaned dataset can be used for further Exploratory Data Analysis (EDA), Business Intelligence, Data Visualization, and Power BI dashboard development.

---

## 🎯 Project Objectives

The main objectives of this project are:

- Understand the structure of the raw supply chain dataset.
- Explore available columns and data types.
- Identify missing and incomplete values.
- Handle missing values appropriately.
- Identify and remove duplicate records.
- Standardize inconsistent column names and categorical values.
- Convert date columns into proper datetime format.
- Validate the cleaned dataset.
- Prepare a reliable dataset for further analysis.
- Support Power BI dashboard and visualization development.

---

## 📋 Problem Statement

Retail and e-commerce organizations generate large amounts of operational data from orders, customers, products, sales, inventory, shipping, and logistics activities.

Raw operational data may contain:

- Missing values
- Duplicate records
- Inconsistent category names
- Incorrect data types
- Date formatting issues
- Inconsistent column names
- Data-quality problems

If these issues are not addressed, they can affect analysis and lead to incorrect business conclusions.

Therefore, this project focuses on preprocessing the DataCo supply chain dataset and creating a clean and reliable dataset that can be used for further analytical activities.

---

## 📊 Dataset Overview

The project uses a Supply Chain Raw Dataset containing order-level information related to retail and e-commerce operations.

The dataset includes information related to:

- Orders
- Customers
- Products
- Product categories
- Sales
- Profit
- Inventory
- Shipping
- Delivery
- Customer segments
- Geographic markets
- Order dates
- Shipping dates

The dataset covers multiple global markets and contains operational and financial information that can be used to evaluate supply chain and e-commerce performance.

---

## 🗂️ Important Dataset Columns

| Column | Description |
|---|---|
| Order ID | Unique identifier associated with an order |
| Type | Order or transaction type |
| Order Status | Current status of the order |
| Days for shipping (real) | Actual number of days taken for shipping |
| Days for shipment (scheduled) | Scheduled shipping duration |
| Delivery Status | Status of delivery |
| Late delivery risk | Indicates potential delivery delay |
| Category Name | Product category |
| Product Name | Name of the product |
| Department Name | Product department |
| Customer Segment | Customer classification |
| Customer City | Customer location |
| Market | Geographic market |
| Order Region | Region associated with the order |
| Order Country | Country associated with the order |
| Sales | Sales amount |
| Unit Price | Price per product unit |
| Order Item Total | Total value of the order item |
| Order Profit Per Order | Profit generated from the order |
| Order Date | Date when the order was placed |
| Shipping Date | Date when the order was shipped |
| Shipping Mode | Shipping method |
| Inventory Stock | Available inventory units |

---

## 🛠️ Technologies Used

### Programming Language

- Python

### Libraries

- Pandas
- NumPy
- Matplotlib
- Seaborn

### Development Environment

- Jupyter Notebook
- Google Colab

### Data Storage

- Microsoft Excel

### Business Intelligence

- Power BI

---

## 📚 Python Libraries

### Pandas

Pandas is used for:

- Loading Excel data
- Data manipulation
- Data cleaning
- Handling missing values
- Removing duplicates
- Data transformation
- Data validation
- Exporting the cleaned dataset

### NumPy

NumPy is used for:

- Numerical operations
- Handling numerical data
- Supporting data transformation and analysis

### Matplotlib

Matplotlib can be used for:

- Data visualization
- Trend analysis
- Distribution analysis
- Exploratory charts

### Seaborn

Seaborn can be used for:

- Statistical visualization
- Distribution plots
- Boxplots
- Correlation analysis

---

## 🔄 Project Workflow

The complete project workflow is:

```text
Raw Supply Chain Dataset
          ↓
Data Loading
          ↓
Data Inspection
          ↓
Data Quality Checking
          ↓
Missing Value Analysis
          ↓
Missing Value Treatment
          ↓
Duplicate Checking
          ↓
Data Type Conversion
          ↓
Column Standardization
          ↓
Category Standardization
          ↓
Outlier Analysis
          ↓
Data Validation
          ↓
Cleaned Dataset
          ↓
Exploratory Data Analysis
          ↓
Power BI / Visualization
          ↓
Business Insights
1️⃣ Data Loading

The raw Excel dataset is loaded into Python using Pandas.

import pandas as pd
import numpy as np

df = pd.read_excel("Supply_Chain_Raw_Dataset.xlsx")

print(df.head())
print(df.shape)
print(df.dtypes)

The initial inspection helps understand the structure of the dataset before performing transformations.

2️⃣ Data Inspection

After loading the dataset, different inspection techniques are performed.

Checking the first records
df.head()
Checking the last records
df.tail()
Checking dataset dimensions
df.shape
Checking column information
df.info()
Checking data types
df.dtypes

This step helps identify:

Number of rows
Number of columns
Column names
Data types
Missing values
Potential data-quality issues
3️⃣ Missing Value Analysis

Missing values are identified before performing further analysis.

df.isnull().sum()

The percentage of missing values can also be calculated:

df.isnull().mean() * 100

This helps determine which columns require data-quality treatment.

4️⃣ Handling Missing Values

Missing values are handled based on the type of data.

Numerical Columns

Numerical columns such as Sales, Order Item Total, Inventory Stock, and Profit can be treated using statistical methods such as median or mean.

Example:

df["Sales"] = df["Sales"].fillna(df["Sales"].median())
Categorical Columns

Categorical columns can be handled using the most frequently occurring value.

Example:

df["Category Name"] = df["Category Name"].fillna(
    df["Category Name"].mode()[0]
)
5️⃣ Duplicate Record Checking

Duplicate records can affect analysis by causing values to be counted more than once.

Duplicates are checked using:

df.duplicated().sum()

Duplicate records can be removed using:

df.drop_duplicates(inplace=True)

After removing duplicates, the dataset is checked again to confirm that duplicate records have been handled.

6️⃣ Data Type Conversion

Correct data types are important for accurate analysis.

Date columns such as Order Date and Shipping Date are converted into datetime format.

df["Order Date"] = pd.to_datetime(df["Order Date"])
df["Shipping Date"] = pd.to_datetime(df["Shipping Date"])

This allows the dates to be used for:

Date-based analysis
Trend analysis
Time intelligence
Power BI reporting
7️⃣ Column Name Standardization

Column names are standardized to improve readability and consistency.

df.columns = df.columns.str.strip()

Columns can also be renamed where required.

df.rename(
    columns={
        "order date": "Order Date",
        "shipping date": "Shipping Date"
    },
    inplace=True
)

Standardized column names make the dataset easier to work with in Python and Power BI.

8️⃣ Category Standardization

Categorical values are reviewed for inconsistencies.

Values representing the same category may appear with:

Different capitalization
Leading or trailing spaces
Different spellings
Different naming conventions

Whitespace can be removed using:

df["Category Name"] = df["Category Name"].str.strip()

Text standardization ensures that identical categories are treated consistently during analysis.

9️⃣ Outlier Analysis

Outliers can be reviewed to identify unusual values in numerical columns.

Important columns for outlier analysis may include:

Sales
Unit Price
Order Item Total
Order Profit Per Order
Inventory Stock
Shipping Days

Boxplots can be used to visualize potential outliers.

import matplotlib.pyplot as plt
import seaborn as sns

sns.boxplot(x=df["Sales"])
plt.show()

Outliers should be investigated before deciding whether they represent errors or legitimate business transactions.

🔟 Data Validation

After preprocessing, the dataset is validated again.

df.isnull().sum()
df.duplicated().sum()
df.dtypes

The cleaned dataset is checked to ensure:

Missing values have been addressed where required.
Duplicate records have been handled.
Date columns have correct data types.
Column names are standardized.
Categorical values are consistent.
Numerical fields are suitable for analysis.
📁 Project Files

The GitHub repository contains the following files:

Retail-E-commerce-DataCo-Supply-chain-Data-Analysis/
│
├── DataCo_Supply_Chain_Analytics_Documentation...
│
├── LICENSE
│
├── Preprocessing_Code_file.ipynb
│
├── README.md
│
├── Supply_Chain_Raw_Dataset.xlsx
│
└── cleaned_data.xlsx
📓 Jupyter Notebook

The main preprocessing code is available in:

Preprocessing_Code_file.ipynb

The notebook contains the Python-based preprocessing workflow, including:

Dataset loading
Dataset inspection
Missing-value analysis
Missing-value treatment
Duplicate checking
Date conversion
Data standardization
Data validation
📄 Raw Dataset

The original dataset is stored as:

Supply_Chain_Raw_Dataset.xlsx

This file represents the source data before preprocessing.

The raw dataset contains information related to:

Orders
Customers
Products
Sales
Profit
Shipping
Delivery
Inventory
Geographic markets
📄 Cleaned Dataset

The processed dataset is stored as:

cleaned_data.xlsx

This dataset is intended to serve as the analysis-ready version of the raw data.

The cleaned dataset can be used for:

Exploratory Data Analysis
Business analysis
Data visualization
Power BI dashboards
Supply chain performance analysis
📊 Business Analysis Areas
Sales Analysis

Possible analysis includes:

Total sales
Sales by product
Sales by category
Sales by market
Sales by region
Sales trends
Order value
Product Analysis

Possible analysis includes:

Best-performing products
Low-performing products
Product categories
Product revenue
Product profitability
Product demand
Customer Analysis

Possible analysis includes:

Customer segments
Customer locations
Orders by customer segment
Sales by customer segment
Regional customer distribution
Shipping Analysis

Possible analysis includes:

Actual shipping days
Scheduled shipping days
Shipping mode
Delivery status
Late delivery risk
Shipping performance
Inventory Analysis

Possible analysis includes:

Inventory stock levels
Product availability
Stock distribution
Products with low inventory
Inventory-related supply chain issues
Profitability Analysis

Possible analysis includes:

Total profit
Profit by product
Profit by category
Profit by market
Profit per order
High-profit and low-profit products
📈 Power BI Dashboard

The cleaned dataset can be imported into Power BI to create an interactive supply chain dashboard.

Potential dashboard KPIs include:

Total Sales
Total Orders
Total Profit
Average Order Value
Total Products
Inventory Stock
Late Delivery Count
On-Time Delivery Rate
Average Shipping Days

Potential visualizations include:

Sales by Market
Sales by Category
Profit by Product
Orders by Region
Shipping Performance
Delivery Status
Inventory Analysis
Monthly Sales Trends
💡 Expected Business Insights

The analysis can help organizations understand:

Which products generate the highest sales.
Which categories perform better.
Which regions generate more revenue.
Which customer segments contribute more sales.
Which products generate higher profit.
Where delivery delays occur.
Which shipping modes perform better.
Which products may require inventory attention.
Where supply chain efficiency can be improved.

These insights can support better decision-making related to inventory planning, logistics, sales strategy, and supply chain operations.

🔍 Data Quality Improvements

The preprocessing stage focuses on improving the overall quality of the dataset.

Missing Values

Missing numerical and categorical values are identified and treated using appropriate statistical approaches.

Duplicate Records

Duplicate records are checked and removed where necessary.

Data Types

Incorrect date formats are converted into proper datetime values.

Standardization

Column names and categorical values are standardized for consistency.

Validation

The final dataset is reviewed to confirm that the preprocessing steps have been successfully applied.

🚀 How to Run the Project
Step 1: Clone the Repository
git clone <your-github-repository-url>
Step 2: Open the Project

Navigate to the project directory:

cd Retail-E-commerce-DataCo-Supply-chain-Data-Analysis
Step 3: Install Required Libraries
pip install pandas numpy matplotlib seaborn openpyxl
Step 4: Open the Notebook

Open:

Preprocessing_Code_file.ipynb

using:

Jupyter Notebook
JupyterLab
Google Colab
Visual Studio Code
Step 5: Run the Notebook

Run the notebook cells sequentially.

The notebook will load the raw Excel dataset, perform preprocessing, validate the data, and generate the cleaned dataset.

🧪 Data Processing Example

A simplified version of the preprocessing workflow is:

import pandas as pd
import numpy as np

# Load dataset
df = pd.read_excel("Supply_Chain_Raw_Dataset.xlsx")

# Inspect dataset
print(df.shape)
print(df.info())

# Check missing values
print(df.isnull().sum())

# Remove duplicates
df.drop_duplicates(inplace=True)

# Convert dates
df["Order Date"] = pd.to_datetime(df["Order Date"])
df["Shipping Date"] = pd.to_datetime(df["Shipping Date"])

# Numerical missing-value treatment
df["Sales"] = df["Sales"].fillna(df["Sales"].median())

# Categorical missing-value treatment
df["Category Name"] = df["Category Name"].fillna(
    df["Category Name"].mode()[0]
)

# Validate
print(df.isnull().sum())
print(df.duplicated().sum())

# Export cleaned dataset
df.to_excel("cleaned_data.xlsx", index=False)
📌 Project Outcome

The main outcome of this project is a structured and cleaned supply chain dataset that can be used for further analysis.

The preprocessing process helps improve:

Data consistency
Data reliability
Data usability
Analysis accuracy
Visualization quality
Business reporting

The cleaned dataset provides a strong foundation for further EDA, Power BI dashboard development, and business intelligence analysis.

🔮 Future Scope

The project can be extended in several ways.

1. Exploratory Data Analysis

Perform deeper analysis to identify trends and relationships between:

Sales
Profit
Products
Customers
Shipping
Inventory
2. Power BI Dashboard

Develop an interactive dashboard containing:

Executive KPIs
Sales analysis
Profit analysis
Shipping analysis
Inventory analysis
Geographic analysis
3. Advanced Analytics

Machine learning techniques can be applied for:

Demand forecasting
Sales prediction
Delivery-risk prediction
Inventory forecasting
Customer segmentation
4. Automated Data Pipeline

The preprocessing process can be automated so that new supply chain data can be cleaned and transformed automatically.

5. Advanced Business Intelligence

The cleaned dataset can be integrated into a larger BI solution for continuous monitoring of supply chain performance.

👥 Team Members

This project was developed as part of the Infosys Springboard Virtual Internship.

Team Members:

Vaishnavi
Shreya
Pujitha
Siva Reddy
Imam Khasim
🎓 Project Context

This project was developed as part of an Infosys Springboard Virtual Internship and focuses on practical data preprocessing and supply chain analytics.

The project demonstrates the importance of data quality in supply chain management and prepares raw operational data for reliable analysis and business decision-making.

📚 Documentation

Additional project documentation is available in the repository:

DataCo_Supply_Chain_Analytics_Documentation

The documentation provides additional details about:

Project objectives
Dataset
Data preprocessing
Data cleaning
Python implementation
Preprocessing outcome
✅ Conclusion

This project demonstrates an end-to-end approach to preparing retail e-commerce supply chain data for analytics.

The project begins with a raw supply chain dataset and applies systematic preprocessing techniques including:

Data Loading
      ↓
Data Inspection
      ↓
Missing Value Handling
      ↓
Duplicate Checking
      ↓
Data Type Conversion
      ↓
Standardization
      ↓
Data Validation
      ↓
Cleaned Dataset
      ↓
Further Analysis

By completing these preprocessing activities, the raw dataset is transformed into a more reliable and consistent dataset suitable for further analytical and business intelligence applications.

The cleaned data can serve as a foundation for Exploratory Data Analysis, Power BI dashboards, supply chain performance analysis, and future predictive analytics.

📜 License

This project is licensed under the MIT License.

See the LICENSE file for more information.

⭐ Acknowledgement

Special thanks to Infosys Springboard for providing the learning and project environment through the Virtual Internship program.

👤 Author

Siva Reddy

Data Analytics / Data Analysis Project

Skills Demonstrated
Python
Pandas
NumPy
Excel
Data Cleaning
Data Preprocessing
Exploratory Data Analysis
Power BI
Supply Chain Analytics

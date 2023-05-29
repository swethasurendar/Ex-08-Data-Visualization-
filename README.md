# Ex-08-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
#Import required libraries

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

#Load the dataset

df = pd.read_csv('Superstore2.csv', encoding='unicode_escape')

#Data Cleaning: Drop unnecessary columns

df.drop(['Row ID', 'Order ID', 'Ship Date', 'Customer ID', 'Postal Code', 'Product ID'], axis=1, inplace=True)

#Feature Generation: Extract Year and Month from Order Date

df['Year'] = pd.DatetimeIndex(df['Order Date']).year

df['Month'] = pd.DatetimeIndex(df['Order Date']).month_name()

#1. Which Segment has Highest sales?

segment_sales = df.groupby('Segment')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales)

plt.title('Segment-wise Sales')

plt.show()

#2. Which City has Highest profit?

city_profit = df.groupby('City')['Profit'].sum().reset_index().sort_values(by='Profit', ascending=False)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Profit', data=city_profit.head(10))

plt.title('Top 10 Cities by Profit')

plt.show()

#3. Which ship mode is profitable?

shipmode_profit = df.groupby('Ship Mode')['Profit'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Ship Mode', y='Profit', data=shipmode_profit)

plt.title('Ship Mode-wise Profit')

plt.show()

#4. Sales of the product based on region

region_sales = df.groupby('Region')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Region', y='Sales', data=region_sales)

plt.title('Region-wise Sales')

plt.show()

#5. Find the relation between sales and profit

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', data=df)

plt.title('Sales vs. Profit')

plt.show()

#6. Find the relation between sales and profit based on the following category.

#i) Segment

segment_sales_profit = df.groupby('Segment')['Sales', 'Profit'].mean().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='Segment', y='Profit', data=segment_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Segment-wise Sales and Profit')

plt.legend()

plt.show()

#ii) City

city_sales_profit = df.groupby('City')['Sales', 'Profit'].mean().reset_index().sort_values(by='Profit', ascending=False).head(10)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Sales', data=city_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='City', y='Profit', data=city_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Top 10 Cities by Sales and Profit')

plt.legend()

plt.show()

#iii) States

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='State', data=df)

plt.title('Sales vs. Profit based on State')

plt.show()

#iv) Segment and Ship Mode

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', data=df)

plt.title('Sales vs. Profit based on Segment and Ship Mode')

plt.show()

#v) Segment, Ship mode and Region
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/dbcf96af-4845-41be-8715-6e4a19bffe00)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/431b861c-895f-4ddb-8ca3-319141b11404)

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', size='Region', data=df)

plt.title('Sales vs. Profit based on Segment, Ship Mode and Region')

plt.show()
```
# OUPUT
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/37198d5f-d32d-4555-97ae-6c81cd66dbaa)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/b1581e1b-578f-40ee-8db6-419cb23addfd)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/84391f80-a15b-4978-a3a8-9e909a5444ad)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/e8cf0fbf-0849-4c96-8e89-b149f2fd54fa)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/1242855a-a93e-41c2-9aa4-1ea1c9c1db63)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/bac623bb-7efd-465b-82a8-7c3bed6d939d)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/1952a55d-aae0-42be-a38e-7c3a5872510f)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/2ab2ede9-8212-40b5-8105-1048382fa436)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/d4aec213-a194-4159-84b5-e7cdcd780768)
![image](https://github.com/swethasurendar/Ex-08-Data-Visualization-/assets/133625914/0f84ad9d-6ecd-4aee-87ef-363df4927e01)

# RESULT:
Thus, to Perform Data Visualization on the given dataset and save the data to a file has been successfully performed.

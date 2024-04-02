# Retail Customer Segmentation Report

## Introduction

The following report details the analytical process undertaken to understand customer behavior for a retail dataset. The goal was to segment customers based on their purchasing patterns using K-means clustering and to provide marketing strategy recommendations for each segment.

## Data Sourcing

The data was sourced from an online repository and contained several attributes related to retail purchases, including 'TotalSales', 'Discount', 'InvoiceID', 'ProductID', 'CustomerID', and 'Date'.

## Exploratory Data Analysis (EDA)

Initial EDA involved inspecting the first few rows of the dataset and checking data types. We identified the need to:

- Convert the 'Date' column to datetime format.
- Drop the redundant 'Unnamed: 0' column.
- Change 'InvoiceID', 'ProductID', and 'CustomerID' data types to string.

We then performed a descriptive analysis, where we generated summary statistics for the dataset and created box plots to visually inspect for outliers. Notable findings included a range of 'TotalSales' and 'Discount' values, with some outliers present in these features.

## Data Preprocessing

During preprocessing, we:

- Aggregated sales data by 'CustomerID' to create a new DataFrame with 'Recency', 'Frequency', and 'TotalSales_capped'.
- Scaled these features using StandardScaler to prepare for clustering.

## Elbow Method Analysis

We applied the Elbow Method to determine the optimal number of clusters for K-means. Plotting Within-Cluster-Sum-of-Squares (WCSS) against the number of clusters revealed an elbow at four clusters, which we chose as the optimal count.

## KMeans Clustering

With the optimal number of clusters identified, we applied K-means clustering and added a 'Cluster' column to the DataFrame to reflect the segment each customer belongs to.

We calculated mean 'Recency', 'Frequency', and 'TotalSales_capped' for each cluster, which provided insights into the characteristics of each customer segment.

## Customer Segments

Analysis of each cluster revealed distinct purchasing patterns:

- **Cluster 0**: Lower average 'TotalSales_capped' (approx. 754.76) and a moderate average 'Discount_capped' (approx. 134.47). This aligns with the idea of Cluster 0 being more moderate in sales and discounting, potentially representing occasional shoppers or those attracted by moderate promotions.
- **Cluster 1**: Higher average 'TotalSales_capped' (approx. 3584.21) and a significant average 'Discount_capped' (approx. 639.55). Contrary to the initial analysis, this suggests that Cluster 1 may consist of more engaged customers who respond well to discounting strategies and contribute a higher sales volume.
- **Cluster 2**: The highest average 'TotalSales_capped' (approx. 5725.73) and the highest average 'Discount_capped' (approx. 1020.52). This suggests that Cluster 2 may represent premium customers or bulk buyers who contribute significantly to sales and receive substantial discounts, possibly due to the volume or value of their purchases.
- **Cluster 3**: Moderate average 'TotalSales_capped' (approx. 1935.12) and 'Discount_capped' (approx. 344.55). This segment could represent a middle ground between casual and bulk buyers, potentially regular customers who make consistent but not the largest purchases.

## Visualizations

Visualizations included box plots and scatter plots. The box plots were utilized for outlier detection in 'TotalSales' and 'Discounts', and scatter plots with Altair helped to visualize the relationship between these two features across clusters.

## Marketing Strategy Recommendations

Based on our findings, we suggest the following strategies for each customer segment:

- **Cluster 0**: Attract with small-scale promotions.
- **Cluster 1**: Focus on maintaining loyalty with these high-value customers.
- **Cluster 2**: Continue to incentivize bulk buying or value-based purchases with competitive discounts.
- **Cluster 3**: Engage with moderate promotions and focus on increasing the transaction size.

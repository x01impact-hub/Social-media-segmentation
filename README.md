SOCIAL  MEDIA SEGMENTATION

This project analyzes social media user behavior and groups users into meaningful segments using unsupervised machine learning, primarily K-Means clustering on engineered engagement features.[file:1]

## Overview

The notebook loads a social media behavior CSV file in Google Colab, inspects the dataset, engineers new behavioral features, standardizes selected variables, and applies clustering to identify distinct user groups.[file:1]
The workflow also evaluates the optimal number of clusters with the elbow method and silhouette score, profiles each cluster, and visualizes the final segmentation with PCA-based plots.[file:1]

## Dataset

The notebook works with a dataset of 25,000 rows and 45 columns, with no missing values reported in the initial inspection stage.[file:1]
Example fields shown in the notebook include daily screen time, likes per day, comments per day, shares per week, engagement rate, weekly sessions, and addiction level.[file:1]

## Feature Engineering

The notebook creates four derived features to improve segmentation quality.[file:1]

- `engagementintensity`: combines likes, comments, and shares into a single interaction score.[file:1]
- `videoratio`: measures video consumption relative to daily screen time.[file:1]
- `postingrate`: estimates posting frequency relative to weekly sessions.[file:1]
- `logfollowers`: applies `log1p` to follower count to reduce skew.[file:1]

## Modeling Pipeline

Eight features are selected for clustering: daily screen time, weekly sessions, engagement intensity, video ratio, posting rate, log followers, addiction level, and monthly social spending.[file:1]
These features are standardized with `StandardScaler` before clustering so variables with different scales contribute more evenly.[file:1]
The notebook then tests `k` values from 2 to 10 using both inertia and silhouette score, and ultimately trains a final K-Means model with `k = 5` clusters.[file:1]

## Cluster Output

The final K-Means model produces five user segments with the following cluster sizes: 5,882; 7,088; 1,142; 8,183; and 2,705 users.[file:1]
The notebook assigns descriptive labels to these groups in the PCA visualization: Casual Non-Video Users, Light Video Consumers, Micro Creators, Heavy Addicted Users, and Social Shoppers.[file:1]

## Visualizations

The notebook generates:

- An elbow curve to inspect inertia across candidate cluster counts.[file:1]
- A silhouette score plot to compare clustering quality across `k` values.[file:1]
- A 2D PCA scatter plot showing cluster separation and cluster centers.[file:1]

Saved figures referenced in the notebook include `elbow_silhouette.png` and `clusters.png`.[file:1]

## Libraries Used

The notebook imports and uses the following core libraries and tools.[file:1]

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `sklearn.preprocessing.StandardScaler`
- `sklearn.cluster.KMeans`
- `sklearn.metrics.silhouette_score`
- `sklearn.decomposition.PCA`
- `PIL`

## How to Run

1. Open the notebook in Google Colab or a local Jupyter environment compatible with the imported libraries.[file:1]
2. Upload the CSV dataset when prompted by the file upload cell.[file:1]
3. Run the cells in order so that feature engineering, scaling, model evaluation, clustering, and visualizations are created correctly.[file:1]
4. Review the cluster profile table and PCA plot to interpret the discovered user segments.[file:1]

## Project Structure

The notebook is organized roughly as follows.[file:1]

- Library imports.[file:1]
- CSV upload and data loading.[file:1]
- Initial dataset inspection.[file:1]
- Feature engineering.[file:1]
- Feature scaling.[file:1]
- Cluster count evaluation with elbow and silhouette methods.[file:1]
- Final K-Means training with 5 clusters.[file:1]
- Cluster profiling by feature averages.[file:1]
- PCA-based visualization of segment separation.[file:1]

## Notes

The notebook appears to be designed as an exploratory segmentation project for understanding different types of social media users based on behavior, activity, content consumption, and spending patterns.[file:1]
Because the dataset is uploaded interactively in Colab, the exact CSV filename may need adjustment if the uploaded file name differs from the one used in later cells.[file:1]

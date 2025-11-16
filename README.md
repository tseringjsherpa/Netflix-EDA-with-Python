# Netflix Content Analysis & Predictive Modeling

## Overview

This project performs exploratory data analysis and predictive modeling on Netflix's content catalog. The analysis examines content distribution patterns, ratings, temporal trends, and genre preferences across different regions. A multiple linear regression model is implemented to predict movie duration based on content attributes.

---

## Dataset

**Source:** Shivam Bansal. (2021). *Netflix Movies and TV Shows* [Data set]. Kaggle. https://www.kaggle.com/datasets/shivamb/netflix-shows

**Size:** 8,807 records  
**Coverage:** Content available on Netflix through 2021

### Dataset Structure

| Column | Description |
|--------|-------------|
| `show_id` | Unique identifier for each title |
| `type` | Movie or TV Show |
| `title` | Name of the content |
| `director` | Director(s) of the title |
| `cast` | Main actors/actresses |
| `country` | Country(ies) of production |
| `date_added` | Date added to Netflix |
| `release_year` | Original release year |
| `rating` | Maturity rating (e.g., PG, R, TV-MA) |
| `duration` | Minutes for movies; seasons for TV shows |
| `listed_in` | Genre categories |
| `description` | Brief synopsis |

---

## Project Structure

```
netflix-data-analysis/
│
├── netflix_movies(1).csv           # Dataset
├── netflix_analysis.ipynb          # Main analysis notebook
├── requirements.txt                # Python dependencies
└── README.md                       # Project documentation
```

---

## Analysis Overview

### 1. Data Exploration
- Dataset inspection (8,807 records, 12 columns)
- Missing value analysis and handling
- Data cleaning and type conversions
- Feature extraction from dates

### 2. Univariate Analysis

**Key Questions Answered:**
- Content range: 2008-2021
- Content type distribution: 70.4% Movies, 29.6% TV Shows
- Top 10 directors, cast members, and countries by content volume
- Rating distribution (TV-MA most common with 3,183 titles)
- Top 10 genres (International Movies leads with 2,752 titles)
- Average movie duration: 99.58 minutes
- Average TV show length: 1.69 seasons
- Content addition patterns by month and day

**Notable Findings:**
- Longest movie: *Black Mirror: Bandersnatch* (312 minutes)
- Longest TV show: *Grey's Anatomy* (17 seasons)
- United States produces the most content (3,639 titles)
- Anupam Kher appears most frequently (43 titles)

### 3. Multivariate Analysis

**Relationships Explored:**
- Content ratings by type (Movies vs TV Shows)
- Content addition trends over time by type
- Genre popularity trends across years
- Most popular genres by country
- Movie duration variation by genre
- TV show length variation by genre
- Average season count trends over time
- Movie duration trends over release years
- Correlation between release year, duration, and year added

**Key Insights:**
- Dramas most popular in the United States (835 titles)
- International Movies dominate in India (864 titles)
- Content addition peaked in 2019 with 1,999 titles
- No significant trend in average movie duration over time

### 4. Machine Learning: Linear Regression

**Objective:** Predict movie duration

**Features:**
- `release_year`: Year the movie was released
- `year`: Year added to Netflix
- `rating`: Content rating (one-hot encoded)
- `type`: Content type (one-hot encoded)

**Target Variable:** `movie_duration` (minutes)

**Model Performance:**

| Metric | Training Set | Test Set |
|--------|-------------|----------|
| R² Score | 0.2060 | 0.2198 |
| RMSE | 24.80 min | 26.51 min |
| MAE | 18.18 min | 19.37 min |

**Interpretation:** The model explains ~22% of variance in movie duration. The moderate R² score suggests that movie duration is influenced by factors beyond the features used, such as genre, director preferences, or production constraints.

---

## Technology Stack

| Component | Technology |
|-----------|-----------|
| **Language** | Python 3.x |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Machine Learning** | Scikit-learn |
| **Development Environment** | Jupyter Notebook |

---

## Key Visualizations

The notebook includes:
- Pie charts for content type distribution
- Bar plots for top directors, cast, countries, ratings, and genres
- Histograms for duration distributions
- Line plots for temporal trends
- Box plots for duration by genre
- Pair plots for feature relationships
- Scatter plots for actual vs predicted values

---

## Data Preprocessing

**Steps Performed:**
1. Handled missing values (filled with 'Not Available' or dropped)
2. Converted `date_added` to datetime and extracted day, month, year
3. Converted `type` and `rating` to category datatype
4. Split comma-separated values in `director`, `cast`, `country`, `listed_in`
5. Standardized text formatting (title case, strip whitespace)
6. Created numeric duration columns for analysis

---

## Future Enhancements

- Implement ensemble models (Random Forest, Gradient Boosting) for better predictions
- Add feature engineering (genre combinations, director popularity metrics)
- Perform natural language processing on descriptions
- Develop content recommendation system using clustering
- Time series forecasting for content addition trends
- Sentiment analysis on descriptions
- Classification model for rating prediction

---

## References

Shivam Bansal. (2021). *Netflix Movies and TV Shows* [Data set]. Kaggle. https://www.kaggle.com/datasets/shivamb/netflix-shows

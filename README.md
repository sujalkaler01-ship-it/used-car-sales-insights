# Used Car Sales Insights

Exploratory Data Analysis (EDA) of about 122,000 used car sales, built in Python. The project cleans a messy real-world dataset, visualizes it with 15 charts, and turns the results into pricing and inventory recommendations for a used-car business.

## Problem Statement

Used car buyers and sellers find it hard to know which factors really drive a car's selling price. This project analyzes used car sales to find the patterns behind price, demand and inventory, so that pricing and stocking decisions can be based on data.

## Objectives

- Load, inspect and understand the dataset
- Clean data errors and handle missing values
- Find which factors affect selling price (mileage, age, body type, drive type, engine size, brand)
- Identify the most common brands, models and locations
- Turn the findings into business recommendations

## Dataset

`used_car_sales.csv` has 122,144 rows and 13 columns:

| Column | Meaning |
|---|---|
| `ID` | Row identifier |
| `pricesold` | Selling price |
| `yearsold` | Year the car was sold (2018-2020) |
| `zipcode` | Location (some values are masked, e.g. `928**`) |
| `Mileage` | Distance driven |
| `Make`, `Model`, `Trim` | Brand, model and variant |
| `Year` | Manufacturing year |
| `Engine` | Engine description |
| `BodyType` | Sedan, SUV, Coupe, Convertible, pickup types, etc. |
| `NumCylinders` | Number of engine cylinders |
| `DriveType` | AWD, 4WD, RWD, FWD, 2WD |

Add the link to where you downloaded the dataset here: `<dataset source link>`

## Data Cleaning

The raw data has serious quality problems that hide real patterns, so cleaning was a major part of the project:

- Removed 40 duplicate rows (found by ignoring the `ID` column)
- Filled missing categorical values with "Unknown"
- Cleaned `BodyType` and reduced `DriveType` from about 2,800 messy labels to 6 clean values
- Created a new feature, `Car_Age = yearsold - Year`
- Removed impossible or erroneous rows: non-positive prices, negative age, `Year` before 1950 (including `Year = 0`), and mileage of 1,000,000 or more (the maximum was 1.2 billion)
- Treated `NumCylinders` values of 0 or above 16 as missing instead of deleting the rows
- Capped prices at the 99th percentile (about $63,000)

Result: 116,623 of 122,144 rows (95.5%) kept.

## Visualizations

15 charts, organized as univariate, bivariate and multivariate analysis:

- Top 10 brands and top 10 models by count
- Distribution of selling price and of car age
- Mileage vs selling price (scatter plot)
- Average price by body type, drive type, number of cylinders and manufacturing year
- Top 10 zipcodes by car count
- Price comparison of the top 5 brands (box plot) and their market share (pie chart)
- Average mileage by brand
- Correlation heatmap and pair plot

## Key Findings

- Ford and Chevrolet make up 34.6% of all cars, and the top 5 brands make up 50.3%.
- The median selling price is $6,250, and 78.7% of cars sell for $15,000 or less.
- Higher mileage tends to mean a lower price (correlation -0.30). More cylinders tends to mean a higher price (correlation 0.21).
- Crew Cab Pickups ($14,837 average) and Coupes ($12,684) are priced highest, while Sedans ($6,554) are among the lowest.
- AWD and 4WD cars average about $11,100-$11,700, roughly double the FWD average of $5,042.
- Price is not a straight line with age: cars 11-40 years old are the cheapest, while cars 0-5 years old (about $21,800) and cars over 40 years old (about $12,200) cost more.
- Price varies widely inside every brand, so brand averages are not enough for pricing.

## Limitations

- About 25% of cars have an unknown drive type and about 24% have no valid cylinder count.
- About 31% of zipcodes are masked.
- The data covers sales from 2018 to 2020 only.
- This is an exploratory analysis. It shows relationships, not causes, and it does not include a prediction model.

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Google Colab / Jupyter Notebook

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/sujalkaler01-ship-it/used-car-sales-insights.git
cd used-car-sales-insights
```

2. Install the libraries:

```bash
pip install pandas numpy matplotlib jupyter
```

3. Put `used_car_sales.csv` in the same folder as the notebook, open `Used_car_sales_insights_fixed.ipynb` in Jupyter, and run all cells.

**In Google Colab:** upload the notebook, then upload `used_car_sales.csv` to the `/content` folder (Files pane on the left) and choose Runtime > Run all.

## Author

Sujal Kaler, BCA (AI/ML), Lovely Professional University

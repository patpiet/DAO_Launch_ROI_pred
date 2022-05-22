# Data Science Return on Investment from DAO Maker launches Predictor: Project Overview
* Created a model that estimates ROI (MAE ~28x) of the projects that were launched on DAO Maker to help investors with their financial decisions.
* Scraped all publicly launched projects from [DAO Maker] (daomaker.com) using **Beatufil Soup** and [Coingecko] (https://www.coingecko.com/) API.
* Using **nltk** engineered features from the text of each project's description to find importance of certain words (e.g. 'marketing') when it comes to success of a project.
* Optimized **Lasso, Random Forest, and Support Vector Regressors** using GridsearchCV to reach the best model.
* Built a client facing API using Flask

# Code and Resources Used
* **Python Version:** 3.9
* **Packages:** pandas, numpy, sklearn, matplotlib, seaborn, BeautifulSoup, flask, json, pickle, pycoingecko, wordcloud
* **For Web Framework Requirements:** ```pip install -r requirements.txt```
* **Flask Productionization:** https://towardsdatascience.com/productionize-a-machine-learning-model-with-flask-and-heroku-8201260503d2

## Web Scraping
Gathered 93 launch samples with features. With each project, we got the following:
*   Project's name
*   All Time High Return on Investment
*   Money raised
*   Project's category
*   Venture Capital backing the project
*   Market Maker backing the project
*   Whether the cap is controlled
*   Whether the project is approved by DAO
*   Timestamp of the date of public launch
*   Chain project started on
*   Project's description

## Data Cleaning
After scraping the data, it needed to be cleaned up and engineered, so it was usable for machine learning process. The following changes were made: 
*   Parsed numeric data out of Money Raised and ROI
*   Filled NaN data by researching the Web
*   Column for description length
*   Tokenized, stemmed and counted commonly appeared words I thought could be interesting to explore
*   Calculated ratio - word frequency / description's length
*   Simplified the date into DD/MM/YY from Timestamp
*   Created column with Bitcoin Fear&Greed Index value on the day of the launch
*   Made column with just the month of the public launch
*   Grouped least appearing VCs and MMs as 'other'

## Exploratory Data Analysis

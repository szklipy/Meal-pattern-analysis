# Meal-pattern-analysis
This project analyzes six years of daily home-cooked lunch records to identify recurring meal patterns and evaluate whether probabilistic forecasting of meals is feasible.

## Project overview
This project is based on six years of manually recorded daily lunch data, including soup, main course, and side dish. The dataset reflects real-world human input, containing inconsistencies, missing values, and variations in naming.

The goal of the analysis is not to predict meals with certainty, but to examine whether such longitudinal data contains recurring patterns that allow for meaningful probabilistic forecasting. Through data cleaning, pattern analysis, and baseline predictive models, the project evaluates the achievable level of precision and highlights the limitations of forecasting daily meals based on historical consumption alone.


## Data source
The raw data originates from six handwritten household calendars covering the years 2020–2025, where daily home-cooked lunches were recorded manually. Each day may include up to three dish categories: soup, main course, and side dish.

Across 2,192 days, this results in a theoretical maximum of 6,572 dish entries. The final dataset contains 3,299 records, reflecting the realities of daily life. Meals without all dish categories, days with restaurant dining, ordered food, holidays, or leftovers were intentionally excluded to preserve a consistent definition of home-cooked meals and to avoid introducing dominant but analytically uninformative categories.

### Data structure
The dataset is organized into six spreadsheets, one per year, each sharing an identical schema. Rows represent individual calendar days, while columns correspond to recorded dish categories.

The columns include:

- date (YYYY-MM-DD)
- soup
- main_course
- side_dish

Each row contains the recorded lunch for a given date. Missing values are meaningful and indicate the absence of a particular dish category rather than missing data.


| date       | soup          | main_course                         | side_dish |
| ---------- | ------------- | ----------------------------------- | --------- |
| 2022-02-20 | karalábéleves | brassói                             |           |
| 2022-02-21 | karalábéleves | szarvasszelet erdei áfonyamártással | krokett   |
| 2022-02-22 |               | brassói                             |           |
| 2022-02-23 |               |                                     |           |
| 2022-02-24 |               | lazac roston                        | rizs      |
| 2022-02-25 |               | harasztos káposzta                  |           |

Dish names are recorded in Hungarian, reflecting the original source data. Column names are translated for clarity.

### Zero values and semantic meaning

Missing values in the dataset do not represent missing or corrupted data. They encode valid domain information about the structure of a home-cooked lunch.

For a given date, the absence of a dish category indicates that the meal did not include that category. This reflects real-world eating habits rather than data quality issues. As a result, missing values are treated as semantically meaningful and are not imputed by default.

Days without any home-cooked lunch (e.g. restaurant meals, holidays, eating leftovers) are intentionally excluded from the dataset to keep the scope limited to home-prepared meals and to avoid skewing frequency-based analyses.

In a small number of cases, missing values may originate from recording errors. Due to strong domain constraints (certain main courses are always served with a specific side dish), limited and deterministic restoration is possible. Such corrections are applied conservatively and only when the missing value can be inferred unambiguously.

#### Valid dish category combinations (row states)
- Three-course meal (soup, main course, side dish)
- Soup only
- Soup with main course
- Soup with side dish
- Main course with side dish
- Main course only
- No home-cooked lunch on that day

### Preparing data
Data preparation focused on standardization and semantic consistency rather than simple formatting. All dates were unified to a single format to enable time-based analysis across multiple years.

Meal names required additional normalization due to spelling variations and the presence of multiple synonyms in Hungarian cuisine. Several dishes can be referred to by numerous alternative names or word order variations without changing their meaning. Without unification, these variations would artificially fragment identical meals into separate categories and distort frequency-based analyses.

Spelling corrections and synonym mapping were therefore applied to ensure that semantically identical dishes were treated as a single category while preserving the original language of the data.


## How it works, Usage, Model performance
Currently under development.

## Licence
This project is licensed under the MIT License.

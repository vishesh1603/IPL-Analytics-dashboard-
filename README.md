# 🏏 IPL Data Analysis & Power BI Dashboard

An end-to-end **Indian Premier League (IPL) data analysis project** covering match and ball-by-ball data from **2008 to 2026**.

The project focuses on cleaning and preprocessing raw IPL datasets using **Python and Pandas**, performing exploratory and statistical analysis, engineering useful features, and creating dashboard-ready datasets for an interactive **Power BI dashboard**.

---

## 📌 Project Overview

The IPL generates a large amount of match and ball-by-ball data. Raw datasets often contain missing values, inconsistent team names, different season formats, and other data-quality issues.

This project transforms the raw IPL data into structured, analysis-ready datasets and uses them to explore:

* Team performance
* Match and season trends
* Toss impact
* Batting performance
* Bowling performance
* Wicket and dismissal patterns
* Venue statistics
* First-innings scoring trends

The final outputs include cleaned CSV datasets, a Python/Jupyter Notebook for data processing and analysis, and an interactive Power BI dashboard.

---

## 🎯 Objectives

* Clean and standardize raw IPL match data.
* Handle missing and inconsistent values.
* Standardize historical team names.
* Convert and correct data types.
* Engineer useful analytical features.
* Remove super-over deliveries from regular innings analysis.
* Combine match-level and ball-by-ball information.
* Generate dashboard-ready datasets.
* Analyze IPL trends across seasons.
* Build an interactive Power BI dashboard.

---

## 🗂️ Dataset

The project uses two primary datasets:

### `matches.csv`

Contains match-level information such as:

* Match ID
* Season
* Date
* City
* Venue
* Teams
* Toss winner
* Toss decision
* Match winner
* Result
* Result margin
* Target runs
* Target overs
* Player of the Match
* Super Over information

### `deliveries.csv`

Contains ball-by-ball information such as:

* Match ID
* Innings
* Over
* Batter
* Bowler
* Non-striker
* Batsman runs
* Extra runs
* Total runs
* Extra type
* Wicket information
* Dismissal type
* Fielder

---

## 🛠️ Technologies Used

| Technology           | Purpose                          |
| -------------------- | -------------------------------- |
| **Python**           | Data processing and analysis     |
| **Pandas**           | Data cleaning and transformation |
| **NumPy**            | Numerical operations             |
| **Matplotlib**       | Data visualization               |
| **Seaborn**          | Exploratory visualization        |
| **Jupyter Notebook** | Analysis workflow                |
| **Power BI**         | Interactive dashboard            |
| **CSV**              | Dataset storage                  |

---

## 🧹 Data Cleaning & Preprocessing

Several data-quality transformations were performed.

### Match Data

* Converted season values into a consistent 4-digit year format.
* Converted match dates to proper datetime format.
* Filled missing city values using venue information.
* Standardized historical team names.
* Handled missing result-related values.
* Converted `super_over` values into Boolean format.
* Replaced missing Player of the Match values.
* Created a `toss_won_match` feature.
* Renamed `id` to `match_id` for clarity.

### Delivery Data

* Standardized historical team names.
* Filled categorical missing values with `"none"`.
* Converted `is_wicket` into Boolean format.
* Renamed the original `over` column to `over_num`.
* Created a human-readable `over_display` column.
* Removed deliveries belonging to super overs.
* Merged season, date, city, and venue information from the match dataset.

---

## 📊 Feature Engineering

A number of additional features were created to make the data more useful for analysis.

### Toss Advantage

```python
matches['toss_won_match'] = matches['toss_winner'] == matches['winner']
```

This identifies whether the team winning the toss also won the match.

### Over Display

Since the original over numbering is zero-indexed, a human-readable over number was created:

```python
deliveries['over_display'] = deliveries['over_num'] + 1
```

### Match Context

Match-level information such as:

* Season
* Date
* City
* Venue

was merged into the delivery-level dataset to support season, venue, and time-based analysis.

---

## 📈 Analysis & Visualizations

The notebook contains several dashboard-oriented analyses.

### 1. Match Overview

* All-time IPL wins by team
* Toss winner vs match winner
* Season-wise toss impact

### 2. Batting Analysis

* Top 20 IPL run scorers
* Average runs per delivery by over
* Powerplay, middle-over, and death-over scoring patterns

### 3. Bowling Analysis

* Top 20 wicket takers
* Dismissal type distribution
* Bowler-specific wicket performance

### 4. Venue Analysis

* Top 10 venues by number of matches hosted

### 5. Season Trends

* Average first-innings score by IPL season
* Evolution of scoring patterns across seasons

---

## 📊 Power BI Dashboard

The cleaned datasets are used to create an interactive **IPL Power BI Dashboard**.

The dashboard is organized into five analytical areas:

### 🏆 Page 1 — Match Overview

Focuses on:

* Team wins
* Toss impact
* Match performance

### 🏏 Page 2 — Batting Analysis

Focuses on:

* Top run scorers
* Runs by over
* Batting trends

### 🎯 Page 3 — Bowling Analysis

Focuses on:

* Top wicket takers
* Dismissal types
* Bowling performance

### 🏟️ Page 4 — Venue Analysis

Focuses on:

* Matches hosted
* Venue popularity
* IPL venue distribution

### 📅 Page 5 — Season Trends

Focuses on:

* Average first-innings scores
* Season-wise scoring evolution
* Long-term IPL trends

---

## 📁 Project Structure

```text
Cricket/
│
├── data/
│   ├── Uncleaned/
│   │   ├── matches.csv
│   │   └── deliveries.csv
│   │
│   └── cleaned/
│       ├── matches_clean.csv
│       └── deliveries_clean.csv
│
├── IPL_Data_Cleaning_Dashboard.ipynb
│
├── IPL Dashboard.pbix
│
└── IPL Dashboard.pdf
```

---

## 📌 Output Dataset

After cleaning and preprocessing:

| Dataset                |    Rows | Columns |
| ---------------------- | ------: | ------: |
| `matches_clean.csv`    |   1,095 |      21 |
| `deliveries_clean.csv` | 260,759 |      22 |

The cleaned datasets are ready for further analysis and BI visualization.

---

## 🔍 Key Insights Explored

This project enables analysis of questions such as:

* Which IPL teams have the most wins?
* Does winning the toss provide a significant advantage?
* Who are the leading run scorers in IPL history?
* Who are the leading wicket takers?
* How does scoring vary between powerplay and death overs?
* Which venues have hosted the most IPL matches?
* How has average first-innings scoring changed over the seasons?
* What are the most common types of dismissals?

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd Cricket
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Open the notebook

```bash
jupyter notebook IPL_Data_Cleaning_Dashboard.ipynb
```

### 4. Run the notebook

Make sure the raw datasets are available in the expected data directory before running the notebook.

The notebook will:

1. Load the raw datasets.
2. Perform data-quality checks.
3. Clean and standardize the data.
4. Engineer analytical features.
5. Generate visualizations.
6. Export the cleaned datasets.

### 5. Open the Power BI Dashboard

Open:

```text
IPL Dashboard.pbix
```

using **Microsoft Power BI Desktop**.

---

## 💡 Skills Demonstrated

This project demonstrates practical experience with:

* Data Cleaning
* Data Preprocessing
* Exploratory Data Analysis (EDA)
* Feature Engineering
* Pandas
* NumPy
* Data Visualization
* Jupyter Notebook
* Power BI
* Dashboard Design
* Sports Analytics
* Business Intelligence

---

## 📌 Future Improvements

Possible extensions include:

* Player-level performance dashboards
* Team-vs-team head-to-head analysis
* Player strike-rate and economy analysis
* Venue-wise batting and bowling trends
* Win probability analysis
* Predictive match outcome models
* Player performance prediction
* Advanced Power BI DAX measures
* Interactive season and team filters

---

## 👨‍💻 Author

**Vishesh Chaturvedi**

Data Science | Machine Learning | Data Analytics

---

## ⭐ If you found this project useful

Feel free to ⭐ the repository and explore the notebook and Power BI dashboard.

# 🌍 CO2 Emissions Data Analysis and Visualization

## 📌 Project Overview

**This project performs exploratory data analysis and visualization of global CO2 emissions using Python.**

The main objective is to analyze CO2 emission patterns across different countries, regions, and years. The project uses data visualization techniques to identify emission trends, compare regions, discover high emitting countries, and examine changes in global CO2 emissions over time.

The analysis includes multiple graphs such as line charts, bar charts, heatmaps, and regional comparisons.

## 🎯 Objectives

**The main objectives of this project are:**

• Analyze total CO2 emissions over time

• Compare CO2 emissions across different regions

• Study the growth of CO2 emissions by continent

• Visualize CO2 emissions across countries and years

• Identify the top 20 countries with the highest total CO2 emissions

• Identify the top 5 CO2 emitting countries in each region

## 🛠️ Technologies Used

**The following Python libraries are used:**

• Python

• Pandas

• Matplotlib

• Seaborn

## 📊 Dataset Information

**The dataset contains information for approximately 215 countries and territories.**

**The dataset includes:**

| Column               | Description                       |
| -------------------- | --------------------------------- |
| Country Name         | Name of the country               |
| country_code         | Country identification code       |
| Region               | Geographic region                 |
| Indicator Name       | CO2 emission indicator            |
| 1990 to recent years | CO2 emission values for each year |

**The original dataset is in wide format, where every year is stored as a separate column.**

## 🔄 Data Preparation

**The dataset is transformed from wide format into long format using the Pandas `melt()` function.**

### Original Format

```text id="c3j9h1"
Country Name | Region | 1990 | 1991 | 1992 | 1993
Pakistan     | Asia   |  ... |  ... |  ... |  ...
```

### Transformed Format

```text id="7v0x9q"
Country Name | Region | Year | CO2 Emissions
Pakistan     | Asia   | 1990 | ...
Pakistan     | Asia   | 1991 | ...
Pakistan     | Asia   | 1992 | ...
```

**The following steps are performed:**

1. The dataset is loaded using Pandas.

2. The dataset structure is examined using `describe()`, `info()`, and `columns`.

3. The yearly columns are converted into a single `Year` column.

4. CO2 emission values are stored in a single `CO2 Emissions` column.

5. Invalid year values are converted to missing values.

6. Missing year values are removed.

7. The `Year` column is converted to integer format.

## 📈 Visualization 1: Total CO2 Emissions by Year

**A line graph is created to visualize the total CO2 emissions across all countries for each year.**

### Code

```python id="pl84zk"
total_emissions_by_year = data_melted.groupby('Year')['CO2 Emissions'].sum()
```

**The total emissions for each year are calculated by grouping all countries according to the year.**

### Visualization

```text id="pvtz66"
Total CO2 Emissions
        │
        │                    ●────●
        │              ●─────
        │        ●─────
        │   ●────
        │●
        └──────────────────────────
          1990        Year       Recent
```

### Result

**This graph helps identify the overall trend of global CO2 emissions over time.**

**Add your generated graph to the repository:**

```text id="e4kw3p"
results/total_emissions_by_year.png
```

Display it in GitHub:

```markdown id="ec1n3r"
![Total CO2 Emissions by Year](results/total_emissions_by_year.png)
```

## 📊 Visualization 2: Total CO2 Emissions by Region

**A bar chart is created to compare total CO2 emissions across different regions.**

### Code

```python id="q5cex8"
emissions_by_region = data_melted.groupby('Region')['CO2 Emissions'].sum().sort_values(ascending=False)
```

### Visualization

```text id="cr6tub"
CO2 Emissions
│
│ ████████████████████
│ ███████████████
│ ███████████
│ ███████
│ █████
└──────────────────────
  Region A  Region B  Region C
```

### Result

**The visualization ranks regions according to their total CO2 emissions and makes it easier to identify the regions contributing the most emissions in the dataset.**

```markdown id="8vywwj"
![CO2 Emissions by Region](results/emissions_by_region.png)
```

## 🌎 Visualization 3: Growth of CO2 Emissions by Continent

**A multi line graph is created to analyze CO2 emission trends across different regions.**

**Each region is represented by a separate line.**

### Visualization

```text id="wflmp6"
CO2 Emissions
│
│        ╱──── Region 1
│   ╱───╯
│  ╱         ╱──── Region 2
│ ╱     ╱───╯
│╱───── Region 3
└────────────────────────
         Year
```

### Result

**This visualization allows comparison of CO2 emission growth patterns between regions over time.**

**It can help identify:**

• Regions with increasing emissions

• Regions with decreasing emissions

• Regions with relatively stable emissions

• Differences in emission patterns between continents

```markdown id="t5yuxj"
![CO2 Growth by Region](results/co2_growth_by_region.png)
```

## 🔥 Visualization 4: Heatmap of CO2 Emissions

**A heatmap is generated to visualize CO2 emissions for different countries across multiple years.**

### Code

```python id="cxz0mv"
pivot_table = data_melted.pivot_table(
    index='Country Name',
    columns='Year',
    values='CO2 Emissions',
    aggfunc='sum',
    fill_value=0
)
```

### Visualization Concept

```text id="p88y8l"
             1990   1995   2000   2005
Country A    ░░░░   ▓▓▓░   ████   ████
Country B    ▓▓░░   ▓▓▓░   ▓▓▓▓   ███░
Country C    ░░░░   ░░░░   ▓▓░░   ▓▓▓░
```

**Different color intensities represent different CO2 emission levels.**

### Result

**The heatmap provides a detailed overview of:**

• High emitting countries

• Low emitting countries

• Changes in emissions over time

• Patterns across countries and years

```markdown id="zuw45v"
![CO2 Emissions Heatmap](results/co2_heatmap.png)
```

## 🏆 Visualization 5: Top 20 Countries by CO2 Emissions

**The program calculates total CO2 emissions for each country and selects the top 20 countries.**

### Code

```python id="hwvaf9"
total_emissions_by_country = data_melted.groupby('Country Name')['CO2 Emissions'].sum()

top_20_countries = total_emissions_by_country.sort_values(
    ascending=False
).head(20)
```

### Visualization

**A horizontal bar chart is used to display the top 20 countries.**

```text id="w0vjbo"
Country 1  ████████████████████
Country 2  █████████████████
Country 3  ██████████████
Country 4  ████████████
Country 5  ██████████
```

### Result

**This visualization identifies the countries with the highest cumulative CO2 emissions in the analyzed dataset.**

```markdown id="ggopjz"
![Top 20 Countries](results/top_20_countries.png)
```

## 🌐 Visualization 6: Top 5 Countries by CO2 Emissions in Each Region

**The final analysis groups countries according to their regions.**

**For each region, the program identifies the five countries with the highest total CO2 emissions.**

### Process

```text id="9o4ib2"
Global Dataset
      ↓
Group by Region
      ↓
Calculate Country Emissions
      ↓
Sort Countries
      ↓
Select Top 5 Countries
      ↓
Create Regional Bar Charts
```

### Result

**This analysis provides a detailed regional comparison and identifies the major CO2 emitting countries within each geographic region.**

```markdown id="doowt7"
![Top Countries by Region](results/top_countries_by_region.png)
```

# 📊 Key Results

**The analysis produces the following main results:**

| Analysis                  | Result                              |
| ------------------------- | ----------------------------------- |
| Dataset Size              | 215 countries and territories       |
| Total Analysis            | Global CO2 emissions                |
| Time Based Analysis       | CO2 emissions by year               |
| Regional Analysis         | Total emissions by region           |
| Trend Analysis            | CO2 emission growth over time       |
| Country Analysis          | Top 20 countries by total emissions |
| Regional Country Analysis | Top 5 countries in each region      |
| Detailed Visualization    | Country and year heatmap            |

## 📁 Project Structure

```text id="y2wkny"
CO2-Emission-Analysis/
│
├── co2_emission.ipynb
│
├── CO2_emission.csv
│
├── README.md
│
├── requirements.txt
│
└── results/
    │
    ├── total_emissions_by_year.png
    ├── emissions_by_region.png
    ├── co2_growth_by_region.png
    ├── co2_heatmap.png
    ├── top_20_countries.png
    └── top_countries_by_region.png
```

# 📦 Installation

**Install the required Python libraries:**

```python id="l0k5x7"
pip install pandas matplotlib seaborn
```

# 🚀 How to Run

1. Clone the repository.

2. Install the required libraries.

3. Place the dataset file in the project directory.

4. Open the Jupyter Notebook.

5. Run all cells.

6. Analyze the generated visualizations.

# 📌 Conclusion

**This project demonstrates how Python can be used for environmental data analysis and visualization.**

The dataset is transformed into a suitable format for analysis, and multiple visualization techniques are used to study CO2 emission patterns. The project provides insights into global emission trends, regional differences, country level emissions, and the countries with the highest total CO2 emissions.

The visualizations make complex environmental data easier to understand and provide a clear view of how CO2 emissions vary across countries, regions, and years.

## 👨‍💻 About the Developer

<div align="center">

# Shahid Azam

**Computer Science | Artificial Intelligence | Database Projects**

I am a Computer Science graduate with an interest in Artificial Intelligence, Machine Learning, Python development, and practical software projects.
This repository represents my work on a School Management System database project, demonstrating my interest in structured information management and database technologies.

</br>
<a href="https://github.com/shahidazam2020-oss">
<img src="https://img.shields.io/badge/GitHub-Follow%20My%20Profile-181717?style=for-the-badge&logo=github&logoColor=white" alt="Follow on GitHub">
</a>

<a href="https://www.linkedin.com/in/shahid-azam-mughal-787b58235">
<img src="https://img.shields.io/badge/LinkedIn-Connect%20With%20Me-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="Connect on LinkedIn">
</a>

<a href="https://github.com/shahidazam2020-oss">
<img src="https://img.shields.io/badge/Explore-My%20Repositories-238636?style=for-the-badge&logo=github&logoColor=white" alt="Explore repositories">
</a>

</div>


---
## 📜 License

A license has not been specified for this project.


If you intend to make the source and project available for reuse, consider adding an appropriate open-source license. Until then, do not assume that others have permission to redistribute or modify the project.


---
### ⭐ If you find this project interesting, consider starring the repository!

<div align="center">

**Built with Microsoft Access | Developed by Shahid Azam**

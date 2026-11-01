# FIFA World Cup – Matches Overview Dashboard (Excel)

An interactive Excel dashboard that summarizes **200 matches** across **5 competitions**, **5 seasons**, **10 stadiums** and **10 teams**. It is built with Power Query, the Power Pivot Data Model, PivotTables/PivotCharts and Slicers.

![Dashboard preview](Final%20Project/Dashboard.png)

## Key Metrics

| KPI | Value | How it is calculated |
|---|---|---|
| Matches | **200** | Count of `MatchID` |
| Total Goals | **520** | Sum of `GoalsScored` |
| Goals / Match | **2.6** | Average of `GoalsScored` |
| Stadium Capacity | **521,129** | Sum of `Capacity` |
| Total Stadiums | **10** | Count of `StadiumName` |

## Dashboard Visuals

| Visual | Chart type | Measure |
|---|---|---|
| Matches by Competition | Column | Count of `MatchID` per competition |
| Month-wise Competition Trend | 3D line | Count of `MatchID` by month and competition |
| Players by Position | Doughnut | Count of `PlayerID` per position |
| League-wise Teams | Treemap | Count of `TeamID` per league |
| Season vs Competition | 3D bar | Count of `MatchID` per season |
| Matches by City | 3D column | Count of `MatchID` per city |

**Slicers** (filter the dashboard interactively): Stadium Name, Season, Competition Name.

## Workbook Structure

`Final Project/Saswata_ Mondal_final project.xlsx` contains these sheets:

| Sheet | Purpose |
|---|---|
| `DASHBOARD` | Final dashboard with KPI cards, charts and slicers |
| `PIVOT Table & Chart` | All PivotTables and PivotCharts that feed the dashboard |
| `Matches vs stadium` | Bar chart of matches per stadium |
| `Matches vs Month` | Area chart of matches per month |
| `Matches by season` | Line chart of matches per season |
| `Competiton vs Stadium usage` | 3D column chart of competition usage by stadium |
| `Stadium capacity` | 3D column chart of capacity per stadium |
| `Sheet1` | Empty |

## Data Model

Data is loaded with **Power Query** from a separate source workbook, `FIFA__Dataset.xlsx` (not included in this repository), into the Excel **Data Model**. It has six tables:

| Table | Columns |
|---|---|
| `Matches` | MatchID, DateID, TeamID, OpponentTeamID, StadiumID, CompetitionID, GoalsScored, GoalsConceded, Attendance |
| `Competitions` | CompetitionID, CompetitionName, Season |
| `Dates` | DateID, MatchDate, Year, Month |
| `Stadiums` | StadiumID, StadiumName, City, Capacity |
| `Teams` | TeamID, TeamName, League, Country |
| `Players` | includes TeamID, PlayerID, Position (see note below) |

Transformations applied in Power Query:

- Header rows promoted and data types set (integers, text, date) on `Matches`, `Competitions`, `Dates`, `Stadiums` and `Teams`.
- `Players` is de-duplicated on `TeamID` (one player record kept per team) and sorted by `TeamID`. This is why *Players by Position* totals 10 players (DF 2, FW 3, GK 2, MF 3).

## Findings from the Data

- **Busiest stadium:** Stadium_2 with 27 matches. **Quietest:** Stadium_1 with 13.
- **Largest capacity:** Stadium_6 (75,050). **Smallest:** Stadium_2 (32,893).
- **Matches by competition:** Competition_2 and Competition_5 have 44 each, Competition_4 has 43, Competition_1 has 40 and Competition_3 has 29.
- **Seasons:** each season (2021-2022 to 2025-2026) maps to one competition. Matches per season are 40, 44, 29, 43 and 44.
- **Matches by month** (months 1–4): 64, 61, 53 and 22.
- **Leagues:** 5 leagues (League_0 to League_4) with 2 teams each.

## Tools Used

- Microsoft Excel (Power Query, Power Pivot / Data Model, PivotTables, PivotCharts, Slicers, Treemap chart)

## Repository Contents

```
├── README.md
├── FIFA AI Dashboard.png          # AI-generated dashboard mockup (illustrative only)
└── Final Project/
    ├── Dashboard.png              # Screenshot of the actual Excel dashboard
    └── Saswata_ Mondal_final project.xlsx
```

## How to Use

1. Download `Final Project/Saswata_ Mondal_final project.xlsx` and open it in desktop Excel (Windows recommended; Power Pivot and slicers on the Data Model are not fully supported in Excel for the web or Mac).
2. Go to the `DASHBOARD` sheet.
3. Use the Stadium, Season and Competition slicers to filter the charts and KPIs.
4. To refresh the data, the Power Query connections need access to the original `FIFA__Dataset.xlsx`. They currently point to a local path on the author's machine, so you must update the source path first.

## Notes

- Names such as `Competition_1`, `Stadium_1`, `City_1` and `League_0` are placeholders in the dataset, not real FIFA entities.

## Author

**Saswata Mondal**

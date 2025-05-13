# SQL-Progress-Journal-day-27

# Day 27 – SQL Learning Journey

## ✅ Focus Areas
- Continued CS50 Moneyball SQL Project (Tasks 8 & 9)
- Practiced calculating performance efficiency and filtering based on minimum thresholds
- Reinforced understanding of scalar vs. aggregate functions (`ROUND()` vs. `AVG()`, `SUM()`, etc.)
- Clarified when to use `WHERE` vs. `HAVING` in grouped queries

## 🧠 Key Learnings
- Wrote a fully working query on the **first try** for Task 8: finding top 10 players in 2001 with the best HR/salary efficiency.
- Reviewed the difference between scalar and aggregate functions.
- Started Task 9: identifying players with the worst batting averages (hits/at-bats), filtered for those with 100+ at-bats.
- Deepened understanding of when `HAVING` applies (only with aggregates after `GROUP BY`).

code used

SELECT p.first_name, p.last_name, pf.H, pf.AB, 
       ROUND(1.0 * pf.H / pf.AB, 4) AS batting_average
FROM performances pf
JOIN players p ON pf.player_id = p.id
WHERE pf.year = 2001 AND pf.AB >= 100
ORDER BY batting_average ASC
LIMIT 10;


and 

SELECT p.first_name, p.last_name, s.salary,
       ROUND((1.0 * HR / s.salary) * 1000000, 4) AS hr_efficiency
FROM performances pf
JOIN salaries s ON pf.player_id = s.player_id AND pf.year = s.year
JOIN players p ON pf.player_id = p.id
WHERE pf.year = 2001 AND HR > 0
ORDER BY hr_efficiency DESC
LIMIT 10;


## 🛠 Skills Applied
- Complex JOINs across `performances`, `salaries`, and `players` tables
- Derived metrics using math and rounding in SQL
- Query filtering using `HAVING`, `WHERE`, and `ORDER BY`
- Real-world data analysis mindset: value vs. performance

## 🔚 Next Steps
- Complete Task 9 with grouping and HAVING logic
- Tackle Tasks 10–12 and wrap up the CS50 Moneyball SQL project
- Shift focus to Lesson 2 of the CS50 SQL course

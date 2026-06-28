# Mountainland Capstone Project
1. About the data: 
The dataset used in this project, Early Wake-Up, Exercise & Health Outcomes, was sourced from Kaggle. It was designed to explore how daily lifestyle behaviors — particularly sleep habits, wake-up routines, and physical activity — relate to overall health outcomes across a diverse global population. The dataset contains information from 10,000 participants across 6 countries. 

Key variables:  

Limitations & Considerations:
• The dataset is synthetic/simulated, meaning findings reflect modeled relationships rather than real-world measurements. 
• Self-reported variables (mood, anxiety, life satisfaction) are inherently subjective and may carry response bias. 
• The dataset does not include longitudinal tracking — all observations represent a single point in time.
• Country-level differences are minimal across most metrics, suggesting the dataset may not fully capture cultural variation.
2. Problem Statement:
Modern public health research increasingly recognizes that lifestyle factors such as sleep quality, physical activity, and daily routines have a profound impact on overall health outcomes. Despite widespread awareness, many people lack actionable insights into which behaviors matter most and how they interact with one another. 
This project investigates the relationships between early wake-up habits, exercise behaviors, sleep patterns, and overall health scores across a global sample of 10,000 individuals. The goal is to identify which lifestyle factors are most strongly associated with better health outcomes, and to surface patterns that could inform personal wellness decisions or public health recommendations. 
Understanding which morning routines and exercise habits correlate with higher health scores can help individuals, wellness coaches, and policymakers prioritize the right habits to encourage in society. Even in a simulated dataset, the patterns identified here mirror relationships well documented in public health literature.

3. Research Questions:
•	How does age affect overall health score, and is the relationship linear?
•	Does wake-up time influence average health score? Are early risers healthier?
•	Which exercise type is most associated with higher life satisfaction and health scores?
•	How does exercise frequency and duration relate to health outcomes?
•	Does sleep quality correlate with health score, and how strongly?
•	How does pre-bed screen time relate to health score distributions?
•	Do napping habits interact with sleep quality scores across the population?

4. Data Preparation:
Data preparation and exploratory analysis were conducted in Python (pandas, matplotlib, seaborn) inside a Google Colab environment, with the dataset loaded directly from Google BigQuery. The following steps were taken to ensure the dataset was clean, consistent, and ready for visualization in Power BI.


Data Loading & Initial Inspection
The dataset was queried from a BigQuery project using the Google Cloud BigQuery Python client and converted to a pandas DataFrame. Initial inspection used df.head(), df.shape(), and df.info() to confirm the dataset contained 10,000 rows with the expected columns and data types.
df.describe() was used to review the distribution of all numeric variables, confirming that ranges for Health Score, BMI, Daily Steps, Exercise Duration, and Sleep metrics all fell within plausible bounds. No extreme outliers were identified that required removal.
Several df.groupby() aggregations were performed to explore relationships before visualizing — including average Health Score and Healthy Aging Score by Country, average Health Score and Sleep Quality Score by Exercise Type, and average Protein Intake by Exercise Type. These informed which breakdowns were worth including in the Power BI dashboard.
Variable Selection
Several variables present in the dataset — including Healthy Aging Score, Protein Intake, Resting Heart Rate, Smoking Status, Alcohol Consumption, and Social Interaction Score — were explored during the Python analysis phase. After reviewing their distributions and correlations, these variables were excluded from the final dashboard as they did not add meaningfully to the core narrative around sleep, exercise, and wake-up habits. The analysis focused on the variables most directly relevant to the project's research questions.
The data was then exported to a CSV file which was uploaded into Power BI report. 

5. Analysis & Findings:

Correlation Analysis
A formal correlation analysis was conducted in Python to quantify relationships between variables. The chart below ranks every variable by its correlation with Health Score, with positive correlates in blue and negative correlates in red.
 
Energy Level Score (r = 0.62) and Mood Score (r = 0.60) emerge as the top correlates when all variables are included — though these are partially outcome variables themselves rather than independent lifestyle drivers. Among true behavioral inputs, Exercise Frequency (r = 0.53), Life Satisfaction (r = 0.50), Daily Steps (r = 0.49), and Sleep Quality Score (r = 0.48) are the strongest positive predictors. On the negative side, Fatigue Level Score (r = -0.55), Anxiety Score (r = -0.54), and Depression Risk Score (r = -0.51) show the strongest inverse relationships, highlighting the mental health dimension of overall health outcomes. Variables including Healthy Aging Score, Protein Intake, Smoking Status, and Alcohol Consumption were also explored but did not show correlations strong enough to warrant inclusion in the dashboard. 
Finally, categorical variables were one-hot encoded and correlated with Health Score. The chart below shows that never-smoking status (r = 0.088) and active exercise types carry small but positive correlations, while current smoking (r = -0.14) and no exercise (r = -0.30) are the strongest negative categorical predictors. Country of residence shows near-zero correlation across all nations, confirming that health outcomes in this dataset are driven by individual behaviors rather than geography.
 

Dashboard
The Power BI dashboard was designed across three thematic pages, each targeting a distinct dimension of the analysis. 
Health Score Declines with Age (Q1)
The scatter plot of Average Health Score by Age shows a clear negative linear trend. Participants in their 20s average health scores near 76–78, while those in their 70s average closer to 68–70. The trendline indicates a consistent, gradual decline rather than a sharp drop at any particular age — suggesting lifestyle factors may moderate the rate of decline.
Early Risers Score Better (Q2)
The area chart of health score by wake-up time reveals that participants waking between 4–6 AM score the highest (75.3–75.6), while those waking at 11 AM score the lowest (70.1). There is a notable dip around 9 AM (72.8) followed by a brief recovery at 10 AM (74.1), suggesting the relationship is not perfectly linear but the general pattern favors early wake-up times.
 

High Intensity Interval Training (HIIT) Workouts Lead in Life Satisfaction
Among exercise types, HIIT participants report the highest average life satisfaction (7.54), followed closely by Sports (7.49), Running (7.48), and Cycling/Walking (7.47). Participants reporting no exercise have a notably lower score of 6.74 — a full 0.8 points below the top group — reinforcing that engaging in any exercise is the most important factor, regardless of type.
More Exercise = Better Health (Q4)
Both exercise duration and frequency show positive associations with health score. The scatter plots show that longer sessions and more frequent weekly workouts trend toward higher health scores. The morning workout distribution shows that Weight Training and Running have the highest proportion of AM workouts, suggesting motivated exercisers tend to train earlier in the day.
 

Sleep Quality is the Strongest Predictor (Q5)
The scatter plot of health score by sleep quality score shows one of the tightest positive relationships in the entire dataset. Participants with a sleep quality score near 2 have average health scores around 55–60, while those near 10 approach 85–90. This near-linear relationship was further confirmed by the Python correlation analysis, where Sleep Quality Score showed the highest positive correlation with Health Score among all numeric variables examined (r = 0.48).
Screen Time Shows Moderate Negative Trend (Q6)
The combined histogram and line chart shows that higher health score bins tend to coincide with slightly lower average pre-bed screen time. The effect is modest but consistent — participants with health scores above 80 average under 1.1 hours of screen time before bed.
Nap Frequency Interacts with Sleep Quality (Q7)
The nap frequency matrix reveals that participants who nap 0–2 times per week cluster at higher sleep quality scores (6.0–6.5), with a peak of 320 participants at score 6.5 for 0 naps/week. Heavy nappers (5–7 times/week) show flatter, lower distributions, suggesting excessive napping may reflect poor underlying sleep rather than supplement it.
 
7. Conclusions & Recommendations:
Findings:
•	Sleep quality is the most powerful lifestyle predictor of health score in this dataset, showing a near-linear positive relationship across the full range of scores.
•	Early wake-up times (4–6 AM) are consistently associated with higher average health scores, supporting the popular notion that morning routines benefit overall wellness.
•	Age has a steady negative effect on health score, but the gradient is gradual — lifestyle factors appear to moderate this decline.
•	Any exercise is better than none, with non-exercisers showing substantially lower life satisfaction (6.74 vs. 7.45–7.54 for active participants).
•	Pre-bed screen time has a modest but consistent negative association with health outcomes.
•	Excessive napping (5+ times/week) appears linked to lower overall sleep quality, suggesting it may be a symptom of poor sleep rather than a remedy.
Recommendations:
•	Prioritize sleep quality interventions — given its strong predictive power, programs targeting sleep hygiene (consistent schedules, reduced screen time, quiet environments) are likely to yield the greatest health improvements.
•	Encourage early wake-up habits as part of wellness programs, pairing them with consistent morning exercise routines for compounding benefit
•	Promote any form of structured exercise over sedentary behavior — the life satisfaction gap between exercisers and non-exercisers is substantial regardless of activity type.
•	Limit pre-bed screen time as a low-cost, accessible intervention that may modestly support better health outcomes.
For future analysis on this dataset, introducing a longitudinal tracking of participants over time could help identify other aspects of a healthy lifestyle, along with discovering other significant health variables. 

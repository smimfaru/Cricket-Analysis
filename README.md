# Cricket-Analysis
It's a project on ICC T20 World Cup Cricket Analysis with Python, Power BI, Machine Learning
# Problem Statement :
In This project I have performed some analysis on ICC Cricket World Cup 2022 using Python, Power BI and also performed some Machine Learning (such as Random Forest Algorithm) to verify the model predicted a specific team/class as the winner (based on batting performance), how often it was correct and also verify the model predicted a specific team/class as the winner (based on bowling performance), how often it was correct.

# Data Source : 
I got all the data regarding match and world cup detalis from the website : "www.espncricinfo.com" and  got the JSON file from Kaggle. 


# Data Transformation:
 After getting the data in JSON , I Performed initial data cleaning such as player name correction, handling missing values, match id linking etc. using Pandas.  Later I Transformed the final data for the dashboard using Power Query of Power BI.

Data Modelling:
Connected all the datasets with based on some defined primary keys such as team and match ids. Also, created many measures, and calculated columns and parameters for data analysis and dashboarding using DAX.

Data Analysis Expression (DAX)
Measures used in visualization are:

Total Runs = SUM(t20_batting_summary[runs])

Total Innings Batted =COUNT(t20_batting_summary[matchID])

Total Innings Dismissed = SUM(t20_batting_summary[Out])

Batting Avg = DIVIDE([Total Runs],[Total Innings Dismissed],0)

Total balls faced =SUM(t20_batting_summary[balls])

Strike rate = DIVIDE([Total Runs],[total balls faced],0)*100

Batting Possition = ROUNDUP(AVERAGE(t20_batting_summary[battingPos]),0)

Boundary % = DIVIDE(SUM(t20_batting_summary[Boundary runs]),[Total Runs],0)*100

Avg. balls faced =  AVERAGE(t20_batting_summary[balls])

wickets = SUM(t20_bowling_summary[wickets])

Balls Bowled = SUM(t20_bowling_summary[balls])

Runs Conced = SUM(t20_bowling_summary[runs])

Economy = DIVIDE([Runs Conced],([Balls Bowled]/6),0)

Bowling Strike Rate =DIVIDE([Balls Bowled],[wickets],0)

Bowling Avrage = DIVIDE([Runs Conced],[wickets],0)

Total Innings Bowled = DISTINCTCOUNT(t20_bowling_summary[matchID])

Dot Ball % = DIVIDE(SUM(t20_bowling_summary[zeros]),SUM(t20_bowling_summary[balls]),0)

Player selection = if(ISFILTERED(t20_players_info[name]),"1","0")

Display Text = if([Player selection] = "1"," ","Select Player(s) by clicking the player's name to see their invidual or combined strength")

Color Callout Value =if([Player selection]="0","#E8D166","#1D1D2E")

boundary runs batting =t20_batting_summary[fours]*4 + t20_batting_summary[sixes]*6

boundary runs bowling =t20_bowling_summary[fours]*4+t20_bowling_summary[sixes]*6

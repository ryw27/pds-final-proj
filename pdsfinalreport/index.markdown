---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page 
---
# **An Arcane-inspired investigation into League of Legends**

---


Authors: Ryan Wei and Eric Teng

---

## **Introduction**
Equipped with nearly a semester’s worth of practical data science tools, we set out to answer some pressing questions about the polarizing sisters of the hit show Arcane, Vi and Jinx, specifically in the context of the game itself, League of Legends. A fascinating game both in strategy and its psychological and global impact on the human race, League of Legends is a deeply complex game with many moving parts. Each game involves 2 teams, 5 characters a side, who compete on a map to capture certain objectives. At the end, a winner is declared. There are currently more than 140 different characters to choose from, each one carrying its own distinct strengths and weaknesses. Players are often forced to ask themselves: what characters are currently the best? What character will maximize my chance to win? 

We decided to focus on Vi and Jinx in particular, comparing their win rates and answer the question: How likely is a team to win if they have Vi or Jinx on their side? To accomplish this, the project utilizes Oracle Elixir’s extensive 2024 League of Legends datasets equipped with 150588 rows and 161 different data points. We reduced the relevant columns to the following:


## **Data Cleaning and Exploratory Data Analysis**
A lot of data cleaning was needed. There were multiple columns and rows that had NA values that needed to be cleaned in order to ensure best results. We first checked how many games had NA values in the character selections to see how many fully valid games were available. In the end, the massive amount of data was compressed to just 20378 games with all 5 character selections intact. [todo - how were columns cleaned?]

### **Univariate Analysis**

Next, the data was filtered for Vi and Jinx games in particular.  The original non filtered dataframe was used, meaning that games with NAN values were included. This may have affected the data, but the we thought the effect wasn’t too big. The more important aspect was seeing how prevalent the use of Jinx and Vi were. We first copied the original DataFrame, changing every entry in the character selection columns to NAN if they were not Jinx or Vi. Then, all rows with all NAN values in the character selection columns were dropped. The resulting DataFrame was one-hot encoded to yield a 3 column DataFrame, a boolean denoting the presence of Jinx in a game, a boolean for Vi, and the result. We were left with 3861 games, with 512 Vi only games, 3292 Jinx only games, 236 Vi wins, and 1644 Jinx wins. Finally, these datapoints were used to create the following graph. Clearly, Jinx was the more popular character.

![Vi and Jinx Popularity Comparison](../jinxvigames(1).png)

Next, we  checked the win rate across different esports teams when playing Jinx and Vi. Again, the games without Jinx and Vi were filtered out. Then, the resulting dataframe was grouped by teamname, with the number of rows that each team played Jinx and the number of rows where each team played Jinx and won extracted out. The following histograms display the number of teams that had a win rate in some range when playing Jinx. For Vi, the data looked a little different. In general, there were many more games with Jinx in it. Jinx was a more popular and preferred choice for esports teams.

![Vi and Jinx Popularity Comparison](../viwinrate(1).png)
*Figure 1: Distribution of win rates across different esports teams when playing Vi*

![Vi and Jinx Popularity Comparison](../jinxwinrate(1).png)
*Figure 2: Distribution of win rates across different esports teams when playing Jinx*

### **Bivariate Data**
To compare the two distributions of win rates, the plots were overlaid next to each other through the use of box plots. Jinx has a lower median win rate, as well as a lower minimum win rate. Vi has seen more success in competition, although this could be caused by the lower pick rate. Only teams with a particular specialist advantage with Vi would likely pick her. 

![Vi and Jinx Popularity Comparison](../viandjinx(1).png)

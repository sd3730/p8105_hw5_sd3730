# p8105_hw5_sd3730
Problem 0
This “problem” focuses on structure of your submission, especially the use git and GitHub for reproducibility, R Projects to organize your work, R Markdown to write reproducible reports, relative paths to load data from local files, and reasonable naming structures for your files. To that end:

create a public GitHub repo + local R Project; we suggest naming this repo / directory p8105_hw5_YOURUNI (e.g. p8105_hw5_ajg2202 for Jeff), but that’s not required
create a single .Rmd file named p8105_hw5_YOURUNI.Rmd that renders to github_document
create a subdirectory to store the local data files used in the assignment, and use relative paths to access these data files
submit a link to your repo via Courseworks
Your solutions to Problems 1, 2, and 3 should be implemented in your .Rmd file, and your git commit history should reflect the process you used to solve these Problems.

For this Problem, we will assess adherence to the instructions above regarding repo structure, git commit history, and whether we are able to knit your .Rmd to ensure that your work is reproducible. Adherence to appropriate styling and clarity of code will be assessed in Problems 1+ using the style rubric.

This homework includes figures; the readability of your embedded plots (e.g. font sizes, axis labels, titles) will be assessed in Problems 1+.

Problem 1
Suppose you put 𝑛
 people in a room, and want to know the probability that at least two people share a birthday. For simplicity, we’ll assume there are no leap years (i.e. there are only 365 days) and that birthdays are uniformly distributed over the year (which is actually not the case).

Write a function that, for a fixed group size, randomly draws “birthdays” for each person; checks whether there are duplicate birthdays in the group; and returns TRUE or FALSE based on the result.

Next, run this function 10000 times for each group size between 2 and 50. For each group size, compute the probability that at least two people in the group will share a birthday by averaging across the 10000 simulation runs. Make a plot showing the probability as a function of group size, and comment on your results.

Problem 2
When designing an experiment or analysis, a common question is whether it is likely that a true effect will be detected – put differently, whether a false null hypothesis will be rejected. The probability that a false null hypothesis is rejected is referred to as power, and it depends on several factors, including: the sample size; the effect size; and the error variance. In this problem, you will conduct a simulation to explore power in a one-sample t-test.

First set the following design elements:

Fix 𝑛=30
Fix 𝜎=5
Set 𝜇=0
. Generate 5000 datasets from the model

𝑥∼𝑁𝑜𝑟𝑚𝑎𝑙[𝜇,𝜎]

For each dataset, save 𝜇̂ 
 and the p-value arising from a test of 𝐻:𝜇=0
 using 𝛼=0.05
. Hint: to obtain the estimate and p-value, use broom::tidy to clean the output of t.test.

Repeat the above for 𝜇={1,2,3,4,5,6}
, and complete the following:

Make a plot showing the proportion of times the null was rejected (the power of the test) on the y axis and the true value of 𝜇
 on the x axis. Describe the association between effect size and power.
Make a plot showing the average estimate of 𝜇̂ 
 on the y axis and the true value of 𝜇
 on the x axis. Make a second plot (or overlay on the first) the average estimate of 𝜇̂ 
 only in samples for which the null was rejected on the y axis and the true value of 𝜇
 on the x axis. Is the sample average of 𝜇̂ 
 across tests for which the null is rejected approximately equal to the true value of 𝜇
? Why or why not?
Problem 3
The Washington Post has gathered data on homicides in 50 large U.S. cities and made the data available through a GitHub repository here. You can read their accompanying article here.

Describe the raw data. Create a city_state variable (e.g. “Baltimore, MD”) and then summarize within cities to obtain the total number of homicides and the number of unsolved homicides (those for which the disposition is “Closed without arrest” or “Open/No arrest”).

For the city of Baltimore, MD, use the prop.test function to estimate the proportion of homicides that are unsolved; save the output of prop.test as an R object, apply the broom::tidy to this object and pull the estimated proportion and confidence intervals from the resulting tidy dataframe.

Now run prop.test for each of the cities in your dataset, and extract both the proportion of unsolved homicides and the confidence interval for each. Do this within a “tidy” pipeline, making use of purrr::map, purrr::map2, list columns and unnest as necessary to create a tidy dataframe with estimated proportions and CIs for each city.

Create a plot that shows the estimates and CIs for each city – check out geom_errorbar for a way to add error bars based on the upper and lower limits. Organize cities according to the proportion of unsolved homicides.


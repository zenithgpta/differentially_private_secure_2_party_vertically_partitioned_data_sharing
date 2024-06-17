# Secure Two-Party Differentially Private Data Release for Vertically Partitioned Data
--	Zenith Gupta 22125041 DSAI

We use the openly available dataset 'adult' https://archive.ics.uci.edu/dataset/2/adult
Vertically partitioned data means that 2 or more parties have different features of data for the same sample of population. For example, P1 has peoples age and height and P2 has for the same people their weight and income. 
Our aim is to create a differentially private dataset so that no information is leaked while getting better predictive results.
How we do this is:
- Step 1: calculate a utility function 
- Step 2: based on this function select a winner column 
- Step 3: if the column is in our dataset, then update Dg, split and score, if not wait for party 2 to update.
Utility function: I use information gain in my implementation as the utility function. It essentially defines how useful each column is. 
Based on the taxonomy tree then for each predictor attribute we calculate the split value.
In Algorithm 1 we essentially give each column the amount of weight proportional to its utility function and then randomly pick out of them i.e. in the random pick we have a higher chance of picking out the column with a better utility or higher information gain.

Once we have the winner column, we check what is the best splitting attribute by making a classic decision tree and based on that updating Dg.
At the end using SSPP we combine the results and add noise to preserve privacy.

# Abalone Problem Statement
### Steven Slezak
### 29 Jan 2018

### Introduction

The Center for Machine Learning and Intelligent Systems at the University of California, Irvine, maintains a web site containing over 400 data sets as a service to the machine learning community.  This site, [the UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/index.php), consists of data bases, domain theories, and data generators that are open source to any users.  

This problem statement utilizes the *Abalone* [data set found there.](http://archive.ics.uci.edu/ml/datasets/abalone)

This problem statement includes the following:

1.  Domain:  Natural
2.  Problem Statement:  Age Prediction
3.  Description of Data Set:  9 x 4177 with Mixed Properties
4.  Proposed Solution:   Multiple Regression
5.  Benchmark Model:   Linear Regression
6.  Performance Metrics:   MSE and R-squared
7.  Citations
8.  Jupyter Notebook with Associated Code

### Domain:  Natural

The data consist of physical measurements of abalone, a large, delicious, univalve mullosk. 

### Problem Statement:  Age Prediction

The data set is to be used to predict the age of the abalone from the physical measurements collected.  In particular, the target is to predict age through the number of rings in the shell.  So the number of rings is a proxy for age in years.  A formula *Age = rings + 1.5* is used for this purpose.

The data set as presented on the UCI site has already been cleaned of missing data and were scaled for another study.

The original data were from a study by:

*Warwick J Nash, Tracy L Sellers, Simon R Talbot, Andrew J Cawthorn and Wes B Ford (1994) "The Population Biology of Abalone (_Haliotis_species) in Tasmania. I. Blacklip Abalone (_H. rubra_) from the North Coast and Islands of Bass Strait", Sea Fisheries Division, Technical Report No. 48 (ISSN 1034-3288)*

### Description of Data Set:  9 x 4177 with Mixed Properties

The data set consists of 9 attributes and 4177 rows.  The features include one category (Sex) consisting of three classes (Female, Male, and Infant), seven numeric, and one integer.

| **Name** | **Data Type** | **Meaurements** | **Description** |
| :---: | :---: | :---: | :---: |
| Sex | Character | NA | Female, Male, Infant | 
| Length | Numeric | millimeters | longest shell measurement |
| Diameter | Numeric | millimeters | perpendicular to length | 
| Height | Numeric | millimeters | meat in shell |
| Weight (Whole) | Numeric | grams | live weight |
| Weight (Shucked) | Numeric | grams | meat only |
| Weight (Viscera) | Numeric | grams | guts, less blood |
| Weight Shell | Numeric | grams | dried |
| No. Rings | Integer | NA | No. Rings + 1.5 = Age (years) |

Information on the data, the dimensions, and memory usage follow:

| **Set** | **Dimensions** | **Memory (in kB)** |
| :---: | :---: | :---: |
| Abalone Data | 4177 x 9 | 269 |

A table of summary statistics for the data set can be found in a separate data description file of this notebook.

### Proposed Solution: Multiple Regression

It is evident from the correlation table (see the data description file in this notebook), that no single feature is well-correlated with the number of rings.  For this reason, a linear regression model would not be appropriate. 

This suggests that a number of variables should be taken into account in a predictive model, which points to the usage of a multiple regression model.  We want to capture any effects of combined interaction between variables.  A multiple regression model allows for this.

### Benchmark Model:  Linear Regression

Since linear regression is a special case of a multiple regression model, in that it focuses on a single variable rather than many, we would use a linear regression model as the naive benchmark for this study.  A logistic regression is not appropriate because the target (age) is not a binary output.

### Performance Metrics:  MSE and R-squared

The model would be considered effective if we can minimiize the Mean Standard Error and maximize R-squared.  The lower the MSE, the better, since this is a measurement of typical prediction error.  The higher the R-squared the better, since this metric indicates the percentage of variation in the target that is explained by the features in the model.

Since the R-squared value automatically increases as we add more variables to the model, we would monitor the Adjusted R-squared to identify any overfitting.  This will help us remove variables that appear to have explanatory value (because they increase R-squared) but really are not adding anything (because they reduce adjusted R-squared). 

### Citations

Lichman, M. (2013). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml]. Irvine, CA: University of California, School of Information and Computer Science.


### Python Notebook with Associated *R* Code

The Python Notebook with ssociated *R* code can be found in the directory attached to this GitHub repository.



# Practical_Machine_learning
Course Project wite up

This document describe the analysis done for the prediction assignment of the practical machine learning course.
I used the following packages 
#install.packages("caret")
#install.packages("randomForest")
#install.packages("rpart")
library(caret)
Load the data to only in memory

training <- read.csv(url(trainUrl), na.strings=c("NA","#DIV/0!",""))
testing <- read.csv(url(testUrl), na.strings=c("NA","#DIV/0!",""))
In order to perform cross-validation, the training data set is partionned into 2 sets: subTraining (60%) and subTest (40%).

inTrain <- createDataPartition(y=training$classe, p=0.6, list=FALSE)
myTraining <- training[inTrain, ]; myTesting <- training[-inTrain, ]
dim(myTraining) 
Three different transformations were used to clean the data as follows: 
Cleaning NearZeroVariance Variables the  code is run to view possible NZV Variables:
In order to ensure proper functioning of Decision Trees and especially RandomForest Algorithm with the Test data set (data set provided), we need to coerce the data into the same type.
Using the Random Forest for the ML Algorithm for prediction, it was found that the Random Forest performed better than the Decision tree.


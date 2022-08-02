Objective :-To build a classification methodology to predict the quality of wafer sensors based on the given training data. 

The  data will be  in multiple sets of files in batches at a given location. Data will contain Wafer names and 590 columns of different sensor values for each wafer. The last column will have the "Good/Bad" value for each wafer.
"Good/Bad" column will have two unique values +1 and -1.  
"+1" represents Bad wafer.
"-1" represents Good Wafer. 
Apart from training files, we also require a "schema" file from the client, which contains all the relevant information about the training files such as:
Name of the files, Length of Date value in FileName, Length of Time value in FileName, Number of Columns, Name of the Columns, and their datatype.

Prediction: 

1) Data Export from Db - The data inthe stored database is exported as a CSV file to be used for prediction.
2) Data Preprocessing    
   a) Check for null values in the columns. If present, impute the null values using the KNN imputer.
   b) Check if any column has zero standard deviation, remove such columns as we did in training.
3) Clustering - KMeans model created during training is loaded, and clusters for the preprocessed prediction data is predicted.
4) Prediction - Based on the cluster number, the respective model is loaded and is used to predict the data for that cluster.
5) Once the prediction is made for all the clusters, the predictions along with the Wafer names are saved in a CSV file at a given location and the location is returned to the client.

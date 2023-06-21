# Deep Learning Challenge
## Overview 
The objective of this project is to create a binary classifier that predicts the probability of applicants achieving success if they receive funding from Alphabet Soup. To accomplish this, we will utilize the features available in the provided dataset and employ various machine learning techniques to train and evaluate the model's performance. Our goal is to optimize the model to achieve an accuracy score higher than 75%.

## Results
### Data Preprocessing
The objective of the model is to predict the likelihood of success for applicants who receive funding. This information is determined by the `IS_SUCCESSFUL` column in the dataset, which serves as the target variable. The feature variables encompass all columns except the target variable, as well as non-relevant variables like `EIN` and `names`. These features contain relevant information that can be utilized in predicting the target variable. To prevent potential confusion for the model, non-relevant variables that neither serve as targets nor features are dropped from the dataset to minimize noise.

During the preprocessing phase, I employed binning or bucketing to handle rare occurrences in the `APPLICATION_TYPE` and `CLASSIFICATION` columns. Subsequently, I transformed categorical data into numerical data using one-hot encoding. The dataset was then split into separate sets for features and targets, as well as for training and testing purposes. Finally, I applied data scaling to ensure consistency in the distribution of the data. 

### Compiling, Training, and Evaluating the Model
Revised Model: To construct my initial model, I opted for a layered architecture consisting of three layers: an input layer comprising 80 neurons, a second layer with 30 neurons, and an output layer containing 1 neuron. This configuration was chosen with the intention of maintaining a neuron count that ranged from 2-3 times the number of input features. In this particular scenario, after eliminating 2 irrelevant features, there were 43 input features remaining.

To facilitate binary classification, I employed the rectified linear unit (`relu`) activation function for both the first and second layers, while the output layer utilized the sigmoid activation function. Following the training of the model for 100 epochs, I achieved an accuracy score of approximately 74% on the training data and 72.9% on the testing data. No conspicuous signs of overfitting or underfitting were observed.

**Optimization attempts**
1. In an effort to improve the performance of the model, I made several modifications to its architecture. Firstly, I added two dropout layers with a rate of 0.5 to enhance generalization. Additionally, I changed the activation function to `tanh` in both the input and hidden layers. As a result of these changes, the training set achieved an accuracy score of 74.1%, while the testing set achieved a score of 72.9%.

2. In my second optimization attempt, I employed hyperparameter tuning using Keras. This process helped identify the optimal hyperparameters for the model. It was determined that using the `tanh` activation function, setting the first layer to have 41 neurons, and subsequent layers with 13, 5, and 4 units respectively yielded the best results. The model achieved an accuracy score of 73.3% through this approach.

3. For my final optimization attempt, I made additional adjustments. I removed the `STATUS` column and applied binning to the `ASK AMT` column during the preprocessing phase. Two bins were created: one for amounts equal to $5,000 and another for all other amounts in the `ASK_AMT` column. This decision was based on an observation of dataset imbalance, which was identified through a histogram analysis. The two dropout layers with a rate of 0.5 and the `tanh` activation function were retained. To determine the optimal number of epochs, I utilized the early stopping function with a patience of 5 and monitored the `val_accuracy` metric. It was found that training the model for 8 epochs produced the best results. Despite implementing these adjustments, the accuracy score achieved with this final optimization attempt was approximately 73%.

After three attempts to optimize the model, the desired goal of a 75% accuracy score was not attained.

## Summary
Since I was unable to achieve the desired accuracy target of 75%, I do not recommend any of the models mentioned previously. Nevertheless, if given more time, I would consider exploring alternative strategies. These may involve incorporating the Random Forest Classifier and experimenting with various preprocessing techniques. I am convinced that fine-tuning the dropout layers, exploring different activation functions, and adjusting the number of layers and neurons could also play a crucial role in optimizing the model and reaching the desired goal of 75% accuracy.  

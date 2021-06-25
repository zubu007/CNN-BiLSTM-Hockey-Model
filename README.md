# CNN-BiLSTM-Violence-Detection

## Introduction

This is a deep learning model to detect violence from videos. This repo contains the python notebook code for the impletementation of the 'CNN-BiLSTM for Violence Detection' research paper.
The pdf of the said paper is also available on the repository. Also this contains codes for testing this model's accuracy with foreign datasets. This repo has
some continuation with the previous CNN-BiLSTM repo. 

## Procedure

The entire paper impletemation is divided into 3 main steps. 

* Data preprocessing
* Model Creatation and training
* Testing

### Data preprocessing

The data for training the model was the "hockey fights" dataset. These contains 500 videos showing violence and another 500 showing normal gameplay. All the videos in the dataset
are from hockey matches. Each video was around 2-3 seconds long. 

To use the dataset into a deep learning model, we first extracted all the frames from all the videos. We got around 41,000 frames which can be used for training/testing.

### Model Creatation and training

The model mentioned in the paper was made from CNN layers followed by a LSTM layer. As the involvement of the LSTM layer made the model to be sequencial. Thus a 3D array of images
were fed into the model. The input of the first Conv layer was of  `(10, 100, 100, 3)`  where 100 is the width and height of a frames, 3 is the color channels (RGB) and 10 is the 
10 consicutive frames. 

The Conv layers were followed by max pooling layers and after the all the conv-max pooling layers, we flattened the output image to feed it into the LSTM layer. The LSTM layer 
was bi-directional, meaning it had a forward layer and a backward layer. The number of LSTM cells were 10 as the sequence of 1 sample is of 10 frames. Note that 10 LSTM cells 
should not be confused with 10 units in an LSTM layer. The hidden units of each LSTM cell were chosen to be 50 according to the paper. 

The output from the LSTM layer was fed into a fully connected layer and finally the output was of 2 neurons. 1 for indicatinge violence and other for non-violence.

### Testing

The validation split was of 10% so the 90% of the data was used to train the model. The testing of the model was done by other datasets to see how this model
performs of other videos of sort. This experiment was further done in our main research. 

The Testing was performed on 2 other benchmark dataset used for violence detection. 1 is the movie fights dataset and another is a dataset created in violence for south-east
asian context. The testing codes are available in this repo. 

## Results

The training accuracy of the model was of 97% and validation accuracy of the model is of 96.26%

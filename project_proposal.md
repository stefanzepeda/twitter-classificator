# Machine Learning Engineer Nanodegree
## Capstone Proposal - Twitter Disaster Classification Model
Stefan Zepeda 
March 18th, 2023

## Proposal

### Domain Background

This project will focus on the Natural Language Processing domain of Machine Learning. This domain has had incredible surge in the last few months specially with the rise of Large Language Models in the form of ChatGPT and GPT-4. I have always been passionate about human language and how language communicates what is going around us. This project gives me a great opportunity to learn more and get hands on in the subject. This project will use a very common way of electronic human communication, Twitter, to classify if a disaster is ocurring. This is actually a very common problem that emergency response and news organizations around the world use in their day to day monitoring operations as they prepare to relay information to the broader audience. 

The domain background and problem was sourced from a competition in Kaggle called "Natural Language Processing with Disaster Tweets" and a few of the problem statement and resources used in this proposal will be correctly attributed to the Kaggle site and author. Another related article in the subject is "Identification of Disaster-Related Tweets Using Natural Language Processing: International Conference on Recent Trends in Artificial Intelligence, IOT, Smart Cities & Applications (ICAISC-2020)" by Goswami et.al. that will also be referenced across this proposal.


### Problem Statement

As described in the Domain background, Twitter has emerged as a top social platform for users to communicate in real-time about real-life events like emergencies or events that affect the course of their everyday lives. This makes it a prime data generation source for monitoring of such events in order to identify and disseminate knowledge if deemed applicable. The challenge relies on the volume and nature of the data posted by individuals. Not every tweet is related to an emergency and furthermore detecting if a specific tweet relates to a critical event is challenging due to the complexity of our language. For example, some words that regular individuals could use to identify an ongoing fire like "ablaze" could also be used in other contexts like talking about a spectacular sundown. 

This project will aim to build a Machine Learning model that can identify a tweet as related to an emergency situation in the form of a binary output. The project will rely on a database of 10,000 tweets that were hand classified as its main dataset. This project was sourced from a Kaggle competition "Natural Language Processing with Disaster Tweets" as mentioned previously in this proposal.

### Datasets and Inputs

The dataset consists of a database of 10,000 hand classified tweets and it's split into two files:
*Train.csv - Contains a set of tweets with their human classified labels identifying the tweet as related to an emergency or not.
*Test.csv - Contains another set of tweets this time without a human classified label. This file will be used to calculate the accuracy of our model

The datasets have the following columns:
*id - a unique identifier for each tweet
*text - the text of the tweet
*location - the location the tweet was sent from (may be blank)
*keyword - a particular keyword from the tweet (may be blank)
*target - in train.csv only, this denotes whether a tweet is about a real disaster (1) or not (0)

As part of this project the model will generate output labels (1) for a disaster related tweet or (0) for a non-disaster tweet.

### Solution Statement

This project proposes using a Machine Learning model by which users can evaluate newly posted tweets. The model will use Natural Language Processing techniques to output a binary result of (1) to indicate that the tweet relates to an emergency disaster event. Those events can be aggregated and then be looked at humans to further disseminate if necessary. 

### Benchmark Model

Two benchmarks will be used as part of this project:
1. A published paper in this domain: Identification of Disaster-Related Tweets Using Natural Language Processing: International Conference on Recent Trends in Artificial Intelligence, IOT, Smart Cities & Applications (ICAISC-2020) by Goswami et.al.
2. The top contributor to the Kaggle competition "Natural Language Processing with Disaster Tweets"

In both those cases, the highest F1 score achieved is 0.84 in terms of the harmonic mean of precision and recall. Meaning a healthy balance between false positives and false negatives.

### Evaluation Metrics

This project will use the evaluaton metrics proposed by the Kaggle competition "Natural Language Processing with Disaster Tweets" in the form of an F1 score. This score gives us a good perspective of the balance between precision and recall. The reason why these two measures are ideal for this problem is that it is desired to have the lowest level of false positives due to the impact in the spread of tweets that are not an emergency.
F1 score is defined as:

``F1 = 2 * (precision * recall) / (precision + recall)``

where:

``precision = TP/(TP+FP)``

``recall = TP/(TP+FN)``

and:

``True Positive [TP] = your prediction is 1, and the ground truth is also 1 - you predicted a positive and that's true!``

``False Positive [FP] = your prediction is 1, and the ground truth is 0 - you predicted a positive, and that's false.``

``False Negative [FN] = your prediction is 0, and the ground truth is 1 - you predicted a negative, and that's false.``

### Project Design

As I approach this project two big considerations drive my design:

1. The size of the training dataset is relatively small (10,000 hand classified tweets)
2. My personal goals currently align with learning NLP transformer architecture


With the above considerations in mind, I have decided to use a BERT (Bidirectional Encoder Representations from Transformers) classification model. Although a deep learning approach like this would usually take a long time, I will leverage some of the pre-trained BERT models included with TensorFlow in order to speed up the set up for this project. I will still fine tune the model for this specific task, hopefully aiming to yield accurate results with the small training corpus. I want to give credit to this approach to a Kaggle competitor Kyrgyzstan Bishkek who submitted a design I used as inspiration. Other possible classifiers to explore could be a Decision Tree Classifier or an LSTM network.

A high level workflow of the steps to take are:

1. Retrieve dataset and load into Pandas dataframes
2. Identify unique keywords in training dataset
3. Remove stopwords and common words to reduce noise
4. Build frame that aligns with BERT inputs
5. Define the classifier model
6. Define evaluation metrics
7. Fit the model to train data
8. Calculate Predictions
9. Calculate loss and evaluation metrics
10. Report on results based on a binary classifier

This project will be run in a Jupyter Notebook and will be delivered according to the specifications required by the course.

### References
A. Kaggle Competition: Natural Language Processing with Disaster Tweets
  URL: https://www.kaggle.com/competitions/nlp-getting-started/code

B. Research paper: "Identification of Disaster-Related Tweets Using Natural Language Processing: International Conference on Recent Trends in Artificial Intelligence, IOT, Smart Cities & Applications (ICAISC-2020)" by Goswami et.at.

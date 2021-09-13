# fake_real_news
Kaggle Competition on detecting real vs fake news
About the problem:
Fake news is a problem. Especially since Whatsapp has become accessible to almost everybody. It is very easy to forward a piece of information or news without any verification or authenticity.  AI can help solve this problem, by training a model to detect the patterns of fake news/headlines.
Solution Approach:
Most of solutions available on Kaggle achieved 99% accuracy on training data using the combination of title and author. In ‘fake_real_1.ipny’ I trained to check,if I could achieve a 99% accuracy too. I trained Logistic regression, SGD Classifier, Decision tree and LSTM. Out of which Decision tree using a bow vectorizer technique gave an accuracy score of 0.9944. But I was curious to know if we added the text column to our data, will it improve our accuracy or decrease it. 
I assumed that since that the vocabulary increased, we might experience a drop in our accuracy score, but by how much would it reduce? 
I tried similar steps in [fake_real_1.ipynb](./fake_real_1.ipynb) into my new notebook [fake_real_2.ipynb](./fake_real_2.ipynb)
1.	Data Exploration – By looking and exploring the data and the conclusions received in file1, I decided to make use of the all the available text. The title is the most important because it is what leads to a reader clicking the link to read. After playing around with the data, I found that authors also contributed to the legitimacy of the news.  Hence the final data that will be used for training is a concatenation of the columns title, author and text.
2.	The next step was to pre-process the data. I removed punctuation and stop words from the text. The data is also lemmatized to its root form.
3.	The next step was to vectorize our data and I decided to try both BoW and TF-IDF to vectorize the data . BoW yielded better accuracy for the entire dataset than TF-IDF
4.	I initially created a base model using Logistic Regression that gave me an accuracy of 0.964 using bow and 0.9531 using tf-idf
I decided to use accuracy as a comparison parameter because both the classes had equal representation.
5.	I tried to use both techniques on Decision Tree and the accuracy score were as follow:
bow – 0.96 , tf-idf– 0.95. Again, bow performed better.
6.	For the next model training, I decided to go ahead with bow vectorizing on an SGD classifier because it gave slightly better results. The accuracy score using SGD classifier was 0.965. It was better than Decision Tree but not better than Logistic Regression
7.	To have a final comparison, I trained an LSTM model, but the validation accuracy was only 0.80. 
8.	Hence I decided to go ahead and find the best tuning parameters to improve our logistic regression model accuracy score. 
9.	Running the GridSearch on the parameters, and plugging in the best fit parameters, we get a slightly better accuracy of 0.972. We will use this model to get our results.
Precision for the final Logistic regression model on test data is as follows:
Class 0 = 0.9739
Class 1 = 0.9707

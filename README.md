# Apache-Spark-MovieLens-Recommendation-System
Apache Spark Movie Recommendation System on MovieLens

## Situation: 
The given data is from MovieLens Latest Datasets that contains four datasets: movies, ratings, links, tags, and movies dataset will be the target data for this project.


## Task: 
The goal is to build a recommendation system based on user rating data.


## Action:
### 1. Data Exploration and Cleaning
1. Use Spark DataFrame to load the data
2. Since I am only focusing on the movie and rating data, and both of them have no missing values, so I keep the rest there.
3. Count the number of movies(9742) and users(283228) for a brief understanding of the data

### 2. Exploring Data Analysis Spark SQL and OLAP -  Get insights of Data
1. Check the Ratings for Each Movie: After the examination, all movies have at least one rating. A movie has 2750 ratings on average while there are still 29 movies that only with one rating.
2. See which type of the genres is most commonly used by the movies
3. The average score for the entire genres is 3.59, and the standard deviation is 0.15. This indicates that most of the ratings are the even in different genres. Types like Film-Noir, war, Documentary, and Crime had higher ratings than the others, and those movies are usually involved with exaggerating the truth in the film. 

### 3. Modeling: Spark ALS Based Approach
1. Reload the data again in RDD format then split the model into training, validation, and test set. 
2. Make a training function that includes hyperparameter tunning including rank, lambda(regularization term), and draw a learning curve plot to find the best number of iterations. The learning curve is to find the optimal number of iterations to lessen 80% potential the computing cost(10 -> 2 iterations) in the future. In the plot, we can see that only 2 iteration can reach good results instead of 10 iterations. 
3. Evaluate the model using root mean square error, which is a regression based method.

## Result and future work
1. I achieve the model with 0.88 error in ALS which is very similiar to the results on the validation data.
2. To solve cold start problem, the spark ALS only support unrated items or new users to NULL values or just dropped them. This problem may be done by using the item-based collaborating method in the future.

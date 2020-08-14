---
title: "8 Lessons From My First Year as a Data Scientist"
date: 2020-08-02T15:34:30-04:00
tags:
  - Data Science
---

I'm writing this post so that I can remember what I learned during my first year as a Data Scientist. I hope you'll find these lessons helpful as well. 


## 1. Garbage In, Garbage Out  
**No matter how good a model is, if you feed it garbage data, it will give you garbage results.** This is important to remember but easy to forget, since when we first learn about machine learning, we tend to focus mostly on models.  

For example, when I first learned about deep learning, I focused on models and architectures and forgot how important the quality of your data is. My first data science job was at a medical video analysis startup. One of my first projects was an endoscopy image classification project to classify images as 'inside' or 'outside' the body. My team used Google's AI platform to quickly train models. After training several deep neural networks with different sets of train/validation images, I found the model's performance depended heavily on the quality of training data. Because our original data source was videos, the extracted images were imbalanced in terms of diversity. For example, when the camera is inside of a body, it moves quickly because it's filming an endoscopy procedure. On the contrary, when the camera is outside of a body it's mostly sitting on a table and is basically a stream of still images. This led to a lack of variety in the 'outside' category, which caused the model to perform poorly when predicting 'outside'. To resolve this issue we collected more dynamic 'outside' videos in an attempt to balance the diversity of our dataset. After re-training the model on our new dataset, we found its performance improved greatly.  

Ever since then, I always try hard to remind myself that data science is **data** science, not model science. 

## 2. Repetition Makes Things Easier
Everyone knows practice makes perfect, but what I didn't know was that __just by being exposed to something multiple times, things become easier to understand.__ Whenever I'm learning a new concept, I often feel I don't understand what's going on. But when I see or hear it a second time, surprisingly it makes more sense to me. And it gets better the next time. And the next. Afterwards, I'd ask myself "Why didn't I understand this before?" What I realized is that everytime I repeat the same concept, I pick up a new piece of it. At first it doesn't seem to make any sense, but at some point the puzzle pieces start to fit together and I'm able to see the big picture.

For example, I remember the first time I saw a training function for a neural network. I felt totally overwhelmed not knowing what each line of code does. But seeing it over and over again for different examples, I gradually felt less and less overwhelmed. And with practice, I finally got comfortable writing one myself! So it's okay if you don't understand something at first. It's even okay if you don't understand it the second time either. If you just keep repeating the same idea multiple times, you'll eventually understand it.

## 3. Always Have a Baseline Model
If a model's MSE is 0.9, is it always a good model? If a model's accuracy is 0.3, is it always a poor model? We can't make a blanket statement about their performance without a baseline model to compare to. If your baseline model and new model give you almost the same score, your new model probably doesn't add much. If your baseline model's accuracy is 0.2 and your new model gives you 0.3 then it's good progress. It's also nice to have multiple baseline models so that you have more context to evaluate your final model against.

## 4. Don't Underestimate Linear Models
As we learn fancier models and architectures in machine learning, we often tend to underestimate linear models. However, linear regression and logistic regression models are still widely used in industry because of their simplicity and interpretability. Especially when there is a strong linear relationship among predictors, linear models show strong performance. By the coefficients of the model you can also interpret the importance of each predictor.

I once participated in a kaggle competition for a tabular dataset in which the predictors were all unnamed. To figure out the relationships among the predictors, I plotted the correlation map and found a couple of predictors that were highly correlated with the target. Due to the high correlation, my linear regression model using only the highest correlated predictors achieved a 0.86 MSE, whereas the fancier models I tried only got around 0.9 MSE. Because I started with a simple linear model as my baseline, I was able to judge the performance gain of each new idea or model I tried, which helped guide me throughout the competition.


## 5. Readability Matters
When I first started to code, I thought the less code the better. However, as I programmed more and more, I realized that readability matters as much as efficiency when it comes to code. Because most data scientists work as part of a team, it's important that your code is easy to read by your teammates. If I write code that's too compact to easily understand, it's going to waste a lot of my teammates' time, even if it works perfectly. In the beginning, I usually felt a strong urge to shorten my code to make it more concise. I would use nested list comprehensions or merge several functions to avoid repeating some overlapping parts. However, after code reviewing with collaborators I learned that it can be harder to read. Ever since then, I try to balance the conciseness of my code with readability and try my best to ensure it's easily understood by others.


## 6. When it Comes to Algorithms, Efficiency Matters
When I first learned to write algorithms, I only focused on making them work because most of the test data I used was not big enough to make a noticeable difference at runtime. However, as I studied Data Structures & Algorithms, I learned that writing efficient algorithms makes a huge difference when you have a bigger dataset. If there's a one second delay when working with a small dataset, it can cause god knows how long of a delay when working with a large dataset. Since datasets are becoming bigger and bigger in the world, algorithmic efficiency is becoming more and more important. I've grown a habit of considering the complexity of the algorithms I write, which has helped tremendously. In particular, getting used to Big-O notation has been a big help.


## 7. Choosing the Right Metric Matters
A metric is a tool that you can use to evaluate whether your model is doing well or not. If you choose the wrong metric, you can easily encounter pitfalls like believing your model is better than it really is. For example, accuracy can't be a good metric when your data is imbalanced. If your test dataset is comprised of 9 correct items and 1 incorrect item, you can easily get 90% accuracy if you always predict 'correct'. Depending on whether you care more about false positives or false negatives, you can choose to use precision or recall or a weighted mix of both. For instance, if you're deploying a recommendation system to production, you probably care more about precision than recall. Why? Well, no one really knows if your model misses a good recommendation, but you certainly want to avoid recommending things that your customers don't like.


## 8. Organization Matters
I never realized how complicated things can get until I worked on a data science project with another person. Jupyter notebooks are extremely complicated to collaborate on because each person has their own workflow. My teammate and I didn't plan ahead what type of feature engineering we'd use or what type of parameters we'd try because we were under time pressure, so our work results were jumbled and unorganized in the end. That's when I realized that when I collaborate with other people on a project, it's important to organize our plans, trials, and results in a clear manner beforehand. Otherwise, we'll end up wasting a lot of time later on just trying to figure out what exactly we did. 


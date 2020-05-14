# SageMaker Deployment of a Sentiment Analysis Web App

This is a deployment project done using Amazon's SageMaker platform. A recurrent neural network is trained using SageMaker **ml.p2.xlarge** instance. 

Navigate to `Project/SageMaker_Project.ipynb` where the original Python script is executed.

This project goal is to have a simple web page which a user can use to enter a movie review. The web page then sends the review off to the deployed model which predicts the sentiment of the entered review. A sample output is shown in the image below.

|         The Godfather (1972) Rotten Tomatoes review          |
| :----------------------------------------------------------: |
| <img src="Project\website\sample1.png" alt="sample_image" style="zoom:60%;" /> |

AWS API Gateway and AWS Lambda functions are used in the project architecture. The Lambda function is a straightforward Python function that can be executed whenever a specified event occurs. It will do the data processing on a user submitted review. In addition, this function gets the permission to send and receive data from a SageMaker endpoint.

<img src="Project/Web App Diagram.svg">

Lastly, the method to execute the Lambda function is a new endpoint that is created using API Gateway. This endpoint is a url that listens for data to be sent to it. Once it gets some data it will pass that data on to the Lambda function and then return whatever the Lambda function returns. Essentially it acts as an interface that lets the web app communicate with the Lambda function.

Please note, that the endpoint was shut to avoid additional charges.

1. Project Summary
    - This project is a review to practice our skills working on automating tests for a RESTful webservice. 

2. Preconditions :
    a) In order to run the project, you will need to do the following : 
    - npm init
    - npm install --save-dev newman 
    - npm install --save-dev newman-reporter-htmlextra
    - User must have a valid account in SquareUp Payments in order to generate a token and idempotency keys. (https://developer.squareup.com/explorer/square/payments-api/)

3. Project Structure
    - The project contains three major folders: 
        * collection : This folder contains all main requests to test the API
        * envVariables : This folder contains the variables that can be establish for certain tests and it's ok to have them set.
        * reports : Whenever executing a project with the instruction of generating a report, this will be exported in the folder.
        * testData : This folder contains the data which need to be input in order to run our tests. For security reasons this json is empty so whenever someone wants to execute , they need to input 4 values : a token , and 3 keys.(The reason will be explained in the Before running the project section)

4. Before running the project : 
    - As you might noticed, to run the project I request  to input a personal token and 3 keys. Well the reasons are :
        * According to the documentation, the status of a payment can be approved or complete. Since it is requested to have a payment cancel , refund and complete that means we will be handling this in three different sections :
         1. When a payment is created 'Approved' -> this will be updated to 'Completed' (Any payment can't be updated if the payment status is already 'Completed')
         2. When a payment is created 'Approved' -> this will be updated to 'Completed' -> and then it will be 'Cancelled' (any payment can't be cancelled until the payment has been already completed)
         3. When a payment is created as 'Completed' -> this can be refund 'Refund' (this can't be done when the payment is 'Approved' or already cancel)

5. Instructions how to run the project
    * The main instructions to simplify the execution : 
        - npm run test-run-collection : This will run the tests and will show execution status in CLI
        - npm run test-run-collection-report : This will run the tests and create a report 
        - npm run test-run-collection-iterations : This will run the tests and will show execution status in CLI with multiple iterations.
        - npm run test-run-collection-iterations-report : This will run the tests and create a report with multiple iterations.


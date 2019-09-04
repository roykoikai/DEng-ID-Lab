Amazon Web Services
Data Engineering Immersion Day
====================================================

Welcome to the lab Instruction!

### Requirements:

* AWS account - if you don't have one, please ask your instructor for the login detail.
* Source RDS (Postgres) details - Your instructor should provide the database information. 
								  Otherwise, follow the instruction in [PreLab-instructor](/PreLab/0.0-PreLab-DMS_instructor_Setup.docx) and set it up yourself.


### What you'll do:

These labs are designed to be completed in sequence, and the full set of instructions are documented below.  Read and follow along to complete the labs. Our lab instructor will give you a high-level overview of the labs and help answer any questions.  Don't worry if you get stuck, we provide hints along the way.

__**Ensure your region is US East (N. Virginia)**__

* **Workshop Setup:** [Create working environment on AWS](#lets-begin)
* **Lab 1:** [Hydrateing the data lake via DMS](#Lab-1---Hydrating-the-data-lake-via-DMS)
* **Lab 2:** [Transforming in the data lake with Glue](#lab-2---Transforming-data-with-Glue)
* **Lab 3:** [Consuming the data lake with Athena & QuickSight](#lab-3---Consuming-data-with-Athena-and-Quicksight)
* **Lab 4:** [Machine learning in the data lake](#lab-4---Machine-learning-in-the-data-lake)
* **Cleanup** [Put everything away nicely](#workshop-cleanup)


## Let's Begin!

### Workshop Setup:

1. Open the CloudFormation launch template link in a new tab. It will load a CloudFormation Dashboard and start the creation process for your lab environment, which deploys:
 <pre>
    - A required Virtual Private Cloud for the DMS
    - An Amazon S3 bucket for the Data Lake
    - A required S3 bucket policy to restrict the data access by AWS DMS service
    - A Glue Service Role to use in later hands-on lab
 </pre>

   
Click the **Deploy to AWS** icons below to stand up the core workshop infrastructure. 

| Region | Launch Template |
| ------------ | ------------- | 
**N.Virginia** (us-east-1) | [![Launch CloudFormation](/assets/images/00-deploy-to-aws.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=dmslab-student&templateURL=https://immersionday-lab.s3.amazonaws.com/data-engineering/DMSlab_student_CFN.json)  


2. The template will automatically take you to the CloudFormation Console and start the stack creation process in **N.Virginia** region.

Proceed through the wizard to launch the stack. Leave all options at their default values, but make sure to check the box to allow CloudFormation to create IAM roles on your behalf:

![IAM resources acknowledgement](/assets/images/00-cf-create.png)

See the *Events* tab for progress on the stack launch that may take up to 5 minutes. You can also see details of any problems here if the launch fails. Proceed to the next step once the stack status advances to "CREATE_COMPLETE".

3. Click in the Output tab and take note of value for BucketName, GlueLabRole and DMSLabRoleS3, which you are going to use in future labs.

![output tab](/assets/images/00-cf-output.png)



### Checkpoint:
At this point, the data lake workshop environment has been setup, looks like this:

![all output](/assets/images/00-cf-final-output.png)

[*^ back to top*](#Requirements)


## Lab 1 - Hydrating the data lake via DMS

Download the [lab1 instruction file](https://immersionday-lab.s3.amazonaws.com/data-engineering/1-Lab-DMS.docx)

### Here's what you're going to work on in lab 1:

![Lab 1 Architecture](assets/images/01-arch.png)


### Checkpoint:
At this point, your DMS task should be finished with 'load Complete' status, and 16 tables are loaded in S3 from RDS by DMS

![Lab 1 done](/assets/images/01-lab1-done.png)

[*^ back to the top*](#Requirements)

## Lab 2 - Transforming data with Glue

Download the [lab2 instruction file](https://immersionday-lab.s3.amazonaws.com/data-engineering/2-Lab-ETL_With_Glue.docx) 

### Here's what you're going to work on in lab 2:

![Lab 2 Architecture](/assets/images/02-arch.png)


### Checkpoint:
Nice work!  You've successfully converted CSV raw data to Parquet, and added parquet tables to the Glue Data Catalog

![Lab 2 done](/assets/images/02-lab2-done.png)


[*^ back to top*](#Requirements)

## Lab 3 - Consuming data with Athena and Quicksight

Download the [lab3 instruction file](https://immersionday-lab.s3.amazonaws.com/data-engineering/3-Lab-Athena_Quicksight.docx) 

### Here's what you're going to work on in lab 3:

![Lab 3 Architecture](/assets/images/03-arch.png)


### Checkpoint:
Sweet! Now you have queried the Data Lake and visualized it in QuickSight. Next, We'll consume the Data Lake via machine learning.

[*^ back to top*](#Requirements)

## Lab 4 - Machine learning in the data lake

Download the [lab4 instruction file](https://immersionday-lab.s3.amazonaws.com/data-engineering/4-Lab-ML_using_Sagemaker.docx) 

### Here's what you will be implementing:
![Lab 4](/assets/images/04-arch.png)


### Checkpoint:
Congratulations, you've successfully built the Data Lake from end to end.  If you have time, try the optional steps in the 4 labs above. Otherwise, please remember to follow the steps below in the **Workshop Cleanup** to make sure all assets created during the workshop are removed so you do not see unexpected charges after today.

[*^ back to the top*](#Requirements)

## Workshop Cleanup

This is really important because if you leave stuff running in your account, it will continue to generate charges.  Certain things were created by CloudFormation and certain things were created manually throughout the workshop.  Follow the steps below to make sure you clean up properly.

[*^ back to the top*](#Requirements)

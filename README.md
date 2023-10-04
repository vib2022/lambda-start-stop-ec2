# lambda-start-stop-ec2
We use a scheduler to trigger a lambda function that starts or stops a specific ec2 instance

Lambda code reference to stop EC2

import boto3
region = 'Enter your region'
instances = ['Enter you instance ID']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.stop_instances(InstanceIds=instances)
    print('stopped your instances: ' + str(instances))

Lambda code reference to start EC2

import boto3
region = 'Enter your region'
instances = ['Enter you instance ID']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.start_instances(InstanceIds=instances)
    print('started your instances: ' + str(instances))

-create an event schedule (AWS cronjob name) to trigger you lambda function
-create a role to give the necessary permission to your lambda to access, start and stop ec2.

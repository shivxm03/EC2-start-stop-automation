# AWS Systems Manager Automation for Starting and Stopping EC2 Instances

This repository contains AWS Systems Manager Automation documents and instructions to automate the start and stop operations of AWS EC2 instances, along with roles, resource groups, and maintenance windows setup.

### StartInstanceAutomation

This automation document starts a specified EC2 instance.

#### Steps

1. **StartInstance**:
   - Action: `aws:changeInstanceState`
   - Parameters:
     - `InstanceId`: Specify the instance ID of the EC2 instance to start.
     - `DesiredState`: `StartInstance`

### StopInstanceAutomation

This automation document stops a specified EC2 instance.

#### Steps

1. **StopInstance**:
   - Action: `aws:changeInstanceState`
   - Parameters:
     - `InstanceId`: Specify the instance ID of the EC2 instance to stop.
     - `DesiredState`: `StopInstance`

## Roles and Permissions

### AutomationRole

Ensure you have an IAM role (`AutomationRole`) configured with permissions to execute AWS Systems Manager Automation documents and manage EC2 instances.

#### Example IAM Policy

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ssm:StartAutomationExecution",
                "ssm:StopAutomationExecution",
                "ssm:DescribeAutomationExecutions",
                "ec2:StartInstances",
                "ec2:StopInstances",
                "ec2:DescribeInstances"
            ],
            "Resource": "*"
        }
    ]
}


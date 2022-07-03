# build-an-ansible-inventory-excercise

Prerequisites
AWS CLI should be installed and configured. Verify it using:
aws --version
# Run any test command
aws iam list-users

# Run this in your exercise directory
touch inventory
echo [all] > inventory
Run the following CLI command to list the EC2 instance and save the IP address to the inventory file:
aws ec2 describe-instances \
\
        --query 'Reservations[*].Instances[*].PublicIpAddress' \
      --filters "Name=tag:Project,Values=udacity" \
      --output text >> inventory

This will append the udacity-tagged instance public IP addresses to our inventory file and should look something like this:

[all]
169.254.123.12  # The public IP will be different in your case

 # Automated Cloud Deployment using Terraform, Ansible, Docker, and GitHub Actions

This is my individual practical project where I created a small Python Flask web app and deployed it automatically on AWS EC2 using DevOps tools — Terraform, Ansible, Docker, and GitHub Actions.
The main goal of this project was to make everything happen automatically without any manual steps.

# Project Summary

In this project, I built a simple Flask app that says “Hello from Readle app on AWS!”
Using Terraform, I created a cloud server on AWS.
Then, I used Ansible to install Docker on that server and run the app inside a Docker container.
After that, I set up GitHub Actions so that whenever I update my code and push it to GitHub, the workflow runs automatically and redeploys the app with the new version.
This helped me understand how automation, CI/CD, and cloud computing work together.

# Tools I Used

For this assignment , I used several tools to make deployment automatic and easy. I used Terraform to create the AWS EC2 instance automatically, and Ansible to install Docker and deploy the app on the server without manual steps. Docker helped me containerize my Flask app so it can run anywhere easily, while AWS EC2 was used to host the app on the cloud. I also set up GitHub Actions to build and redeploy the app automatically whenever I updated my code. Finally, I used Flask (Python) to create a small web app for testing the deployment.

# Project Folder Structure

readle-automate/
│
├── terraform/         → Terraform files to create AWS instance
│   └── main.tf
│
├── ansible/           → Ansible inventory and playbook
│   ├── inventory.ini
│   └── site.yml
│
├── app/               → Flask app and Docker configuration
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── .github/workflows/ → CI/CD workflow file
│   └── ci-cd.yml
│
├── .gitignore         → Ignore unnecessary files
└── README.md          → This documentation file

# How I Set Up and Deployed the Project

1. Setting Up AWS and Terraform
   I created my AWS account and configured the CLI using:

      # aws configure

Then I ran these Terraform commands to create my EC2 instance:

      # terraform init
      # terraform plan -out plan.tfplan
      # terraform apply "plan.tfplan"

Terraform created the server and gave me the public IP address.

2. Configuring Ansible
After getting the IP, I updated the file inventory.ini and added my instance details.
Then I ran:

      # ansible-playbook -i ansible/inventory.ini ansible/site.yml --private-key ~/.ssh/readle_key

This automatically installed Docker and ran my Flask app container on the EC2 instance.

3. Creating and Testing My Flask App

Inside the app folder, I created a small Flask app in app.py that displays a simple message.
I built it locally using:

      # docker build -t readle-app:local .
      # docker run --rm -p 8080:80 readle-app:local
      
I opened the browser at http://localhost:8080 and saw “Hello from Readle app on AWS!”

4. Automating Everything with GitHub Actions
   
When I pushed my code to GitHub, the workflow in .github/workflows/ci-cd.yml ran automatically.
It built a new Docker image, uploaded it to Docker Hub, and redeployed the app on my AWS server.

Later, I tested updating the app:
I changed the message in app.py to “Welcome to Readle – Updated Version”, saved it, committed, and pushed the code.
GitHub Actions automatically started, redeployed the app, and when I refreshed my browser, the new message appeared — showing the pipeline worked perfectly!

# Results

   1.Terraform created the AWS instance successfully.
   2.Ansible installed Docker and deployed the app automatically.
   3.The app ran on my EC2 IP showing: “Hello from Readle app on AWS!”
   4.When I updated the code and pushed it to GitHub, the workflow ran automatically and updated the      app on the server.
   5.After refreshing the browser, the new message appeared — confirming that automation and CI/CD        worked correctly.
 <img width="1022" height="533" alt="image" src="https://github.com/user-attachments/assets/b765d873-949e-495d-8d8b-fa0db19b854f" />
    
  <img width="1023" height="382" alt="image" src="https://github.com/user-attachments/assets/84bd8a04-920c-4842-bd0b-6c7f68292cff" />
    
  <img width="1025" height="488" alt="image" src="https://github.com/user-attachments/assets/bee670e8-6b02-40e5-8d3b-a0219cec8609" />
   
 <img width="978" height="530" alt="image" src="https://github.com/user-attachments/assets/7e9a2fe1-90bc-4778-a82c-089b27be578c" />   


# What I Learned

   1.How DevOps tools work together for continuous integration and deployment.
   2.How to set up an automated pipeline that updates itself when I change my code.
   3.How to manage servers, containers, and deployments easily through the cloud.
   4.The importance of automation to save time and reduce manual errors.


# GitHub Repository: https://github.com/sakshi220122/readle-automate
# Video Presentation: https://youtu.be/iVV4pbHLV9k 

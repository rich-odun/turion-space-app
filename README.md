# Workflow Name: Deploy Flask App to EKS

### Overview: 

This workflow automates the deployment of a Flask app to an Amazon EKS cluster, incorporating several stages to ensure code quality, build, and deployment.

1. Source Code Testing:

> Linting and Static Analysis: Runs SonarQube for code quality and static analysis, checking for issues and enforcing quality gates.

> Unit and Integration Tests: Executes unit and integration tests using pytest within a Python virtual environment to ensure code functionality.

> Dependency Scanning: Uses Snyk to scan for vulnerabilities in dependencies.

2. Build Docker Image:

> Build and Push: Builds a Docker image for the Flask app and pushes it to Amazon ECR, tagging the image with the GitHub run number.

3. Docker Image Testing:

> Integration Tests: Pulls the Docker image from ECR, runs integration tests inside a container, and uploads test results as artifacts.

4. Install Kubectl:

> Setup: Installs kubectl on the GitHub Actions runner to interact with the EKS cluster.

5. Deploy to EKS:

> Configuration: Configures AWS credentials and updates the kubeconfig file to access the EKS cluster.

> Deployment: Updates the Kubernetes deployment manifest with the new Docker image tag and applies it to the EKS cluster.

> Status Check and Rollback: Monitors the deployment status and rolls back if the deployment fails.

This workflow ensures comprehensive testing, secure dependency management, and automated deployment to EKS, maintaining high code quality and application reliability.


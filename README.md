# Jenkins CI/CD Pipeline for CICD-App-Deploy

![Screenshot 2023-03-28 at 9 38 09 PM](https://user-images.githubusercontent.com/43399466/228301952-abc02ca2-9942-4a67-8293-f76647b6f9d8.png)


This repository contains a Jenkins pipeline configuration for automating the build, test, and deployment of a Spring Boot application. The pipeline pulls a Docker image, sets up a build environment, clones the application repository, builds and tests the application, and deploys it to Docker Hub, updating the deployment manifest in the process.

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Pipeline Stages](#pipeline-stages)
- [Setup Instructions](#setup-instructions)
- [Jenkins Plugins](#jenkins-plugins)
- [Credentials Configuration](#credentials-configuration)
- [Contributing](#contributing)
- [License](#license)

## Overview
This Jenkins pipeline automates the continuous integration and continuous deployment (CI/CD) process for the `CICD-App-Deploy` Spring Boot application. It performs the following tasks:
- Pulls and runs a custom Docker container for the build environment.
- Installs necessary dependencies (Git, Docker, etc.).
- Configures SSH for secure Git operations.
- Clones the application repository.
- Builds the application using Maven.
- Runs code quality checks with SonarQube.
- Builds and pushes a Docker image to Docker Hub.
- Updates the Kubernetes deployment manifest with the new image tag.
- Commits and pushes changes to the GitHub repository.

## Prerequisites
- **Jenkins Server**: A running Jenkins instance with administrative access.
- **Docker**: Docker installed on the Jenkins server or agent.
- **GitHub Account**: Access to the `shivendra9203/CICD-App-Deploy` repository.
- **Docker Hub Account**: Credentials for pushing images to Docker Hub.
- **SonarQube Server**: A running SonarQube instance (e.g., at `http://54.159.121.142:9000/`).
- **SSH Key**: An SSH key pair for GitHub authentication.
- **Jenkins Plugins**: Required plugins installed (see [Jenkins Plugins](#jenkins-plugins)).

## Pipeline Stages
1. **Pull and Run Docker Container**: Pulls the `shiv9203/docker-maven-agent:v1` image and runs a container.
2. **Install Dependencies**: Installs Git, Docker, and other tools in the container.
3. **Setup SSH for Git**: Configures SSH keys for secure Git operations.
4. **Git Pull App Repo**: Clones the `CICD-App-Deploy` repository.
5. **Build ARG through Maven**: Builds the Spring Boot application using Maven.
6. **Test the ARG through SonarQube**: Runs SonarQube analysis for code quality.
7. **Build Docker Image**: Builds a Docker image for the application.
8. **Push Docker Image to Docker Hub**: Pushes the image to Docker Hub.
9. **Update Deployment Image Tag**: Updates the Kubernetes deployment manifest.
10. **Git Push to GitHub**: Commits and pushes changes to the repository.

## Setup Instructions
1. **Install Jenkins Plugins**:
   - Navigate to `Manage Jenkins > Manage Plugins` in the Jenkins UI.
   - Install the plugins listed in the [Jenkins Plugins](#jenkins-plugins) section.

2. **Configure Credentials**:
   - Go to `Manage Jenkins > Manage Credentials`.
   - Add the following credentials:
     - **GitHub SSH Key**: Kind: `SSH Username with private key`, ID: `github-ssh-key`.
     - **SonarQube Token**: Kind: `Secret text`, ID: `sonarqube-token`.
     - **Docker Hub Credentials**: Kind: `Username with password`, ID: `docker-cred`.

3. **Create a Pipeline Job**:
   - In Jenkins, click `New Item`, select `Pipeline`, and provide a name.
   - In the pipeline configuration, select `Pipeline script` and paste the provided pipeline script.
   - Save and run the pipeline.

4. **Configure SonarQube**:
   - Ensure the SonarQube server is accessible at `http://54.159.121.142:9000/`.
   - Configure the SonarQube token in Jenkins credentials.

5. **Set Up GitHub Repository**:
   - Ensure the `shivendra9203/CICD-App-Deploy` repository is accessible via SSH.
   - Add the SSH public key to the GitHub repository's deploy keys.

6. **Run the Pipeline**:
   - Trigger the pipeline manually or configure a webhook for automatic builds on code changes.

## Jenkins Plugins
The following Jenkins plugins are required for this pipeline:
- **Git Plugin**: For Git repository operations.
- **Docker Pipeline Plugin**: For Docker build and push operations.
- **Credentials Plugin**: For managing credentials securely.
- **Pipeline Plugin**: For defining and running the pipeline.
- **Maven Integration Plugin**: For Maven build tasks.
- **SonarQube Scanner for Jenkins**: For SonarQube integration.
- **SSH Agent Plugin** (optional): For simplified SSH key management.
- **Pipeline Utility Steps Plugin** (optional): For advanced file operations.

## Credentials Configuration
| Credential ID         | Type                     | Description                              |
|-----------------------|--------------------------|------------------------------------------|
| `github-ssh-key`      | SSH Username with private key | SSH key for GitHub repository access.    |
| `sonarqube-token`     | Secret text              | Token for SonarQube server authentication. |
| `docker-cred`         | Username with password   | Docker Hub username and password.        |

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -m 'Add feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a pull request.

Please ensure your code follows the project's coding standards and includes appropriate documentation.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

**Note**: Update the SonarQube URL, repository details, and other specifics as needed before running the pipeline.
Updated by Jenkins pipeline on Thu May  8 04:20:46 UTC 2025
Updated by Jenkins pipeline on Thu May  8 05:22:12 UTC 2025
Updated by Jenkins pipeline on Thu May  8 05:27:57 UTC 2025
Updated by Jenkins pipeline on Thu May  8 05:31:54 UTC 2025
Updated by Jenkins pipeline on Thu May  8 14:12:04 UTC 2025
Updated by Jenkins pipeline on Fri May  9 06:51:29 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:38:03 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:44:07 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:45:29 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:46:44 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:47:58 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:49:12 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:50:29 UTC 2025
Updated by Jenkins pipeline on Sat May 10 06:51:47 UTC 2025

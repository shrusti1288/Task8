# Task8
Run a Simple Java Maven Build Job in Jenkins


1. Create Your Java App Locally

Directory structure:

hello-java-maven/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java

HelloWorld.java

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}

pom.xml

<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>hello</artifactId>
    <version>1.0</version>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>

2. Start Jenkins using Docker
docker run -p 8080:8080 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
Access Jenkins at: http://localhost:8080
Unlock Jenkins with the admin password (from the terminal output)
Install Suggested Plugins
Create an admin user when prompted

3. Configure Maven in Jenkins

1. Go to Manage Jenkins → Global Tool Configuration

2. Under Maven, click Add Maven
Name: Maven 3.8.6
Uncheck “Install automatically” if Maven is installed on host
Or enable it and select version 3.8.6

4. Create a Freestyle Project

1. Go to New Item → Name: hello-java-maven → Select Freestyle project

2. Under Source Code Management:
Option 1: Use Git if you have a repo
Option 2: Skip Git, use local folder

3. Under Build:
Click Add build step → Invoke top-level Maven targets
Goals: clean package
Maven Version: Maven 3.8.6 (what you configured)

5. Save & Build the Job
Click Build Now
After build completes, go to Console Output
You should see something like:
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] Total time: 1.234 s
[INFO] Finished at: ...
[INFO] ------------------------------------------------------------------------

6. Screenshot Deliverable
Once the build is successful, take a screenshot of the Console Output showing the BUILD SUCCESS line.
Here’s a basic structure and content for your hello-java-maven Git repository:

Repo Name: hello-java-maven
Directory Structure:

hello-java-maven/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java
            
1. HelloWorld.java
Path: src/main/java/HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}

2. pom.xml

Path: pom.xml

<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>hello</artifactId>
    <version>1.0</version>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>


How to Initialize This Repo
If you want to push this to GitHub:
# Clone or init local repo
git init hello-java-maven
cd hello-java-maven

# Add files
mkdir -p src/main/java
# Add HelloWorld.java to correct path
# Add pom.xml

# Commit
git add .
git commit -m "Initial commit: HelloWorld Java Maven project"

# Connect to GitHub
git remote add origin https://github.com/your-username/hello-java-maven.git
git branch -M main
git push -u origin main

Here’s your ready-to-use Java Maven project:

Download hello-java-maven.zip
Here’s a simple and clean README.md for your hello-java-maven project:
README.md

# Hello Java Maven
A simple Java project built using Maven — perfect for testing Jenkins CI/CD pipelines.

## Features

- Basic `HelloWorld` Java application
- Configured with Maven `pom.xml`
- Suitable for Jenkins Freestyle build jobs

## Project Structure

hello-java-maven/ ├── pom.xml └── src/ └── main/ └── java/ └── HelloWorld.java

## Getting Started

### Prerequisites

- Java JDK 8 or 11
- Maven
- (Optional) Jenkins for CI/CD

### Build & Run Locally

```bash
# Compile and package
mvn clean package

# Run the app
java -cp target/hello-1.0.jar HelloWorld

Expected Output
Hello, Jenkins + Maven!
Jenkins Integration

1. Start Jenkins (e.g., via Docker):
docker run -p 8080:8080 jenkins/jenkins:lts

2. Configure Maven under Global Tool Configuration in Jenkins.

3. Create a Freestyle project:
Source: Local folder or Git
Build Step: Invoke top-level Maven targets
Goals: clean package

4. Run the job and check the console output for BUILD SUCCESS.

License
This project is open-source and free to use for learning and educational purposes.

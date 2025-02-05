[3:28 PM, 2/5/2025] Sanjana Biradar: <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Beautiful Webpage</title>
    <style>
        body {
            margin: 0;
            font-family: 'Poppins', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            text-align: center;
            overflow: hidden;
        }
        .container {
            background: rgba(255, 255, 255, 0.95);
            padding: 50px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s, box-shadow 0.3s;
            max-width: 400px;
        }
        .container:hover {
            transform: scale(1.07);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
        }
        h1 {
            color: #333;
            margin-bottom: 20px;
            font-size: 2.5em;
            font-weight: 700;
            letter-spacing: 1px;
            text-shadow: 3px 3px 8px rgba(0, 0, 0, 0.15);
        }
        p {
            color: #444;
            margin-bottom: 30px;
            font-size: 1.2em;
            line-height: 1.8;
        }
        .btn {
            display: inline-block;
            padding: 15px 30px;
            color: #fff;
            background: linear-gradient(45deg, #ff758c, #ff7eb3);
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.2em;
            transition: all 0.3s;
            text-transform: uppercase;
            font-weight: bold;
            letter-spacing: 1px;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.3);
        }
        .btn:hover {
            background: linear-gradient(45deg, #ff4858, #ff5e78);
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
        }
        .btn:active {
            transform: translateY(1px);
            box-shadow: 0 3px 8px rgba(0, 0, 0, 0.2);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Welcome to DevOps Family</h1>
        <p>HELLOOO ASTROIDS</p>
        <button class="btn" onclick="alert('Hello! Have a great day!')">Click Me</button>
    </div>
</body>
</html>
[3:28 PM, 2/5/2025] Sanjana Biradar: pipeline {
    agent any

    tools{
        maven 'maven'
    }

    stages{
        stage('Check and remove container'){
            steps{
                script{
                    def containerExists = sh(script: "docker ps -q -f name=abc", returnStdout: true).trim()
                    if (containerExists) {
                    sh "docker stop abc"
                    sh "docker rm abc"
                    }
                }
            }
        }
        stage('Build package'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Create image'){
            steps{
                sh 'sudo docker build -t app /var/lib/jenkins/workspace/abc/'
            }
        }
        stage('Assign tag'){
            steps{
                sh 'docker tag app sanjana255/app'
            }
        }
        stage('Push to dockerhub'){
            steps{
                sh 'echo "Biradar@24" | docker login -u "sanjana255" --password-stdin'
                sh 'docker push sanjana255/app'
            }
        }
        stage('Remove images'){
            steps{
                sh 'docker rmi -f $(docker images -q)'
            }
        }
        stage('Pull image from DockerHub'){
            steps{
                sh 'docker pull sanjana255/app'
            }
        }
        stage('Run a container'){
            steps{
                sh 'docker run -it -d --name abc -p 8081:8080 sanjana255/app'
            }
        }
    }
    post {
        success {
            echo 'Deployment successful'
        }
        failure {
            sh 'docker rm -f abc'
        }
        always{
            echo 'Deployed'
        }
    }

}
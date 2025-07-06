@Library("Shared") _
pipeline{
    agent { label "vinod" }
    stages{
        stage("Code"){
            steps {
                script{
                  clone("https://github.com/parasssrajput/notes-app.git", "main")
                } 
            }
        }
        stage("Build"){
            steps {
                script{
                    docker_build("notes-app","latest")
                }
                
            }
        }
        stage("Push"){
            steps{
                script{
                    docker_push("parasssrajput", "notes-app", "latest")
                }
                
                }
            }
        stage("Deploy"){
            steps {
                echo "Docker Compose starts"
                sh "docker-compose down && docker-compose up -d"
                echo "Docker Compose completed"
            }
        }
   }

}
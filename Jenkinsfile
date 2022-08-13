pipeline{
    agent any
     parameters {
        string(name: 'VERSION', defaultvalue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanparam(name: 'executetests', defaultvalue: true, description: '')

     }
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials ('server_credentials')
    }
    stages{
        stage("build"){
            steps{
                echo 'building the chatting_application.'
                echo "building version ${NEW_VERSION}"
            }
        }

        stage("test"){
            when {
                expression{
                    BRANCH_NAME == 'master' && CODE_CHANGE == true
                }
            }
            steps{ 
                echo 'building the chatting project'
            }
        }
        stage ("deploy"){
            steps{
                echo 'building the chatting project'
                withcredntials ([
                    usernamepasssword(credentials: 'server_credentials', usernamevariable: USER, passwordvariable: PWD )
                ])
                sh "some script ${USER} ${PWD}"
            }
        }
    }


}

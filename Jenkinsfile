#! Groovy

node {

    properties([
        pipelineTriggers([
          [$class: "GitHubPushTrigger"]
        ])
    ])

    stage('Checkout') {
        checkout scm
    }

    stage('Build And Test') {
        //env.PATH = "${tool 'Maven3.3.9'}/bin:${env.PATHa}"

        try {

            echo "Build And Test ${env.BRANCH_NAME}" 
            sh 'mvn clean test' 
            currentBuild.result = 'SUCCESS'

        } catch (err) {
            currentBuild.result = 'FAILURE'
        }
    }

    //stage 'Notify' 
    //Step ([ $Class: 'GitHubCommitNotifier' , ResultOnFailure: 'FAILURE' ])
    
    // And notify Hipchat, LINE bot or Slack ... etc
}

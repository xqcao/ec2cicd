pipeline {
  agent any
  stages{
    stage("first stage,git clone"){
      steps{
              git url: "https://github.com/xqcao/hellospring.git", branch: "master"
            }
    }
    stage("2nd, generate k8s yml file"){
      steps{
        script{
            def gg_new_tag="1.15.8"
            sh """
                echo "before yaml update"
                sed "s/tagVersion/${gg_new_tag}/g" dev_example.yml > dev.yml
                echo "new yaml updated"
              """
        }
      }
    }
    stage("3rd,deploy to k8s"){
      steps{
        sh "cat dev.yml"
      }
    }
  }
}

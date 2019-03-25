pipeline {
  agent any
  stages {
    stage('Provisioning') {
      parallel {
           stage('Clean VM ') {
             steps {
		         sh '''#!/bin/bash
                     sleep 40
                     echo "VM Deleted"  '''
             }
            }
			
			stage('Create VM ') {
             steps {
		         sh '''#!/bin/bash
                     sleep 40
                     echo "VM Created"  '''
             }
            }
        
           stage('User Add') {
		    steps {
            sh '''#!/bin/bash
                     sleep 220
                     echo "User Added"  '''
          }      
         }
        }
       }		
      		 
    stage('Infra Security Scan') {
       steps {
                     sh '''#!/bin/bash
                     sleep 20
                     echo "Security Scan Completed"  '''
               }
              }


    stage('Install Container Tools') {
      parallel {
        stage('Install Docker') {
         steps {
           ansiblePlaybook(inventory: '/root/IAAC/playbooks/inventory.ini', playbook: '/root/IAAC/playbooks/docker.yml')
           
          }
         }   
        }
       }
          
    stage('Vulnerabilities scan') {
          steps {
                     sh '''#!/bin/bash
                     sleep 30
                     echo "Infra test"  '''
                  }
                }
      
    stage('Application Deployment') {
          parallel {
              stage('App Code Git Checkout') {
                steps {
                  sh '''#!/bin/bash
                     sleep 20
                     echo "SCM Check OUT"  '''
               }
              }
              stage('Build App') {
                steps {
                  sh '''#!/bin/bash
                     sleep 40
                     echo "Build APP"  '''
                  }
                 }
   
    stage('Static Code Analysis') {
                steps {
                  sh '''#!/bin/bash
                     sleep 60
                     echo "Unit Test and Sonar Code Coverage"  '''
                  }
                 }

            stage('Deploy App') {
                steps {
                   sh '''#!/bin/bash
                     sleep 60
                     echo "Unit Test and Sonar Code Coverage"  ''' 
                }
               }
              }
            }  
            stage('Application Testing') {
               parallel {
                 stage('Integration Test') {
                    steps {
                     sh '''#!/bin/bash
                     sleep 47
                     echo "Integration test"  '''
                  }
                }
            
            stage('Functional Test') {
                    steps {
                     sh '''#!/bin/bash
                     sleep 54
                     echo "Integration test"  '''
                  }
                }
           
             stage('Regression test') {
                    steps {
                     sh '''#!/bin/bash
                     sleep 39
                     echo "Integration test"  '''
                     }
                    } 
                   }
                  }
             
              stage('Infra Security Inspection') {
                 steps {
                sh '''#!/bin/bash
                     sleep 39
                     echo "Security Inspection for Complete Infrastructure"  '''
                }
               } 
           
           stage('Smoke Test') { 
                    steps {
                     sh '''#!/bin/bash
                     sleep 30
                     echo "Smoke Test Completed"  '''
                  }
                 } 
                }
               }

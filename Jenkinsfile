pipeline {
     agent { 
            node {
               label 'stage'
       
                 }
        
             }
   
    stages {
        stage('install wordpress')
        {
       
            steps 
            {
                sh 'sudo apt-get update'
                sh 'sudo apt install apache2 -y'
                sh 'sudo apt-get install mysql-server -y'
                sh 'sudo add-apt-repository ppa:ondrej/php -y'
                sh 'sudo apt-get install php7.3 -y'
                sh 'sudo apt install php7.3-cli php7.3-fpm php7.3-json php7.3-pdo php7.3-mysql php7.3-zip php7.3-gd php7.3-mbstring php7.3-curl php7.3-xml php7.3-bcmath php7.3-json -y'
                sh """ sudo mysql << QUERY_INPUT
create database bitnami_wordpress1; 
CREATE USER 'bn_wordpress1'@'localhost' IDENTIFIED BY '45bee7e8ac'; 
GRANT ALL ON bitnami_wordpress1.* TO 'bn_wordpress1'@'localhost' IDENTIFIED BY '45bee7e8ac'; 
SELECT DISTINCT User FROM mysql.user; 
FLUSH PRIVILEGES; 

"""

sh 'sudo  wget -c http://wordpress.org/latest.tar.gz'
sh 'sudo tar -xzvf latest.tar.gz'
sh 'sudo rm -rf latest.tar.gz'
sh 'sudo cp -r /home/ubuntu/workspace/pipe/* /var/www/html/'
sh 'sudo chown -R www-data:www-data /var/www/html/'
sh 'sudo service apache2 restart'
sh 'echo "Installation is complete."'
           
            }
           
        }
    }
       
 }

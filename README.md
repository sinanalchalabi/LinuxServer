# LinuxServer
This is a project to install a secure linux server that
host a web application programmed using python.
## Access Info
IP: 52.58.244.139
URL: http://library.almadarisp.com
App directory : /var/www/html/Library/ 
'grader' SSH private key attached with the repo
SSH port: 2200 
'grader' user password: udacity
## Application used
- Appache Server
- SQLite 
- python
- WSGI Model
## Changes Made
- change ssh defaul port to 2200
- allow only key based ssh
- disable remote access for root
- adding user grader with sudo permissions
- giving each file required permission and owner
- configuring the firewall to add more security
- configuring appache,PostgreSQL and wsgi to host my app
- Installing unattended-upgrade for auto update
## Installing the WSGI application
Update your instance

- Install python 
sudo apt-get install python2.7-dev

- Install apache server
sudo apt-get install apache2
- Install wsgi
sudo apt-get install libapache2-mod-wsgi
- Install pip for python 2
sudo apt-get install python-pip
- Install flask for python 2
sudo pip install flask
- Inside /var/www/html make a directory for your app
mkdir /Library
- Clone your app inside the above directory
git clone "url"
- Create a wsgi file
import sys
sys.path.insert(0, '/var/www/html/Library')
- Create a __init__.py empty file
sudo touch __init__.py
- Edit the 000-default.conf file 
sudo nano /etc/apache2/sites-enabled/000-default.conf
Add this line of code below /var/www/html 
WSGIScriptAlias / /var/www/html/Library/library.wsgi
<Directory library>
    WSGIProcessGroup library
    WSGIApplicationGroup %{GLOBAL}
    Order deny,allow
    Allow from all
</Directory>
- Restart Apache server
sudo service apache2 restart
## Additional Resoures:
- Installing Flask with wsgi:
http://flask.pocoo.org/docs/1.0/deploying/mod_wsgi/
- Github Amazon webserver tutorial:
https://github.com/JaeDukSeo/Amazon_webservice_Tutorial
- Udacity Linux servers course

# myaac
MyAAC is a free and open-source Automatic Account Creator (AAC) written in PHP.

## REQUIREMENTS

	- PHP 5.3.3 or later
	- MySQL database
	- PDO PHP Extension
	- XML PHP Extension
	- ZIP PHP Extension
	- (optional) mod_rewrite to use friendly_urls

## INSTALLATION AND CONFIGURATION

	Just decompress and untar the source (which you should have done by now,
	if you're reading this), into your webserver's document root.

	MyAAC needs proper permissions to handle files correctly.
	If you're using apache2, then your directory needs to have owner set to: www-data, you can do it by using following command:
		chown -R www-data.www-data /var/www/*
			(or any other path your MyAAC installation is located at..)

	  Note: Linux only
		If you're under linux use these commands to set proper permissions:
			chmod 770 config.local.php
			chmod 770 images/guilds
			chmod 770 images/houses
			chmod 770 images/gallery
			chmod -R 770 system/cache

	Visit http://your_domain/install (http://localhost/install) and follow instructions in the browser.


## Debian Guide

  ### Server Web:
  
  

    sudo apt update

    sudo apt install nginx
     
    sudo service nginx start
  
Add below lines to the http section of /usr/local/etc/nginx/nginx.conf or /etc/nginx/nginx.conf file.

	fastcgi_read_timeout 180;

In /etc/php/7.2/fpm/pool.d/www.conf :

	request_terminate_timeout = 180
	
 
In /etc/php/fpm php.ini :

	max_execution_time = 180

In default conf nginx:

 location ~ .php$ {
 ...
	fastcgi_read_timeout 180;
 }

  ### DataBase:

	sudo apt install mariadb-server
	
  	sudo mysql_secure_installation
	
  ### PHP MYAAC
  
    sudo apt install php php-fpm php-zip php-xml php-mysql php-curl
    
    sudo apt-get purge apache2*
    
    sudo apt-get autoremove
    
    cd /
    
    cd etc
    
    rm -r apache2

---
title: "JFFNMS Install on Ubuntu 6.06"
date: 2006-07-16
forum: Server Platforms
---

### Post by nkr1ptd on 2006-07-16
I had this working on 5.10 but am just now getting around to upgrading to 6.06.  So rather than do the upgrade I thought I would just update my install (from scratch) instructions.  Due to the strictness of MySQL 5.0 and some differences with PHP5.  You have to downgrade both to MySQL 4.1 and PHP4 respectively.  Here are the instructions I have for Installing JFFNMS on a server.  If you have any questions/problems/comments please contact me or respond here (bnewport at originalsyntheticoil dot com)

-------------------------------Start Ubuntu JFFNMS Install Instructions-----------------------------------
Written By: Brandon L. Newport
Date: July 16, 2006
Operatying System: Ubuntu 6.06
System Recommendations: While you can use a lower end box, I do not recommend it especially if you are sending logs to the system as well.  What I recommend is at least the following:

CPU: 2GHz
RAM: 1G
Hard Drive: 36GB (Unless you are doing syslog then I would recommend as much as you can afford)
Network Card: Something supported by Ubunut ;)


 

Build Ubuntu server


Download Ubuntu 6.06 Server
Install Ubuntu 6.06 Server


Once server is built, login the first time as the user you created.


I recommend you download my sources.list file

cd /etc/apt
sudo mv sources.list sources.list.ORIG
sudo wget [http://www.pinnaclebs.com/ubuntu606/sources.list](http://www.pinnaclebs.com/ubuntu606/sources.list)
 

Update system

sudo apt-get update

sudo apt-get upgrade

 

Install web server

sudo apt-get install apache2 mysql-server-4.1

Postfix will want you to answer some questions first:
	Postfix Configuration - Answer OK
	Postfix Configuration - Select Internet site and press ENTER
	Postfix Configuration (Mail name)? - enter your fully qualified domains (jffnms.pinnacle.lan) and press ENTER

 

sudo /usr/sbin/apache2-ssl-certificate --force -days 3650

(and answer the questions)

 

Now, enable ssl:

sudo a2enmod ssl

 

configure ssl:

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl

sudo a2ensite ssl

 

sudo vi /etc/apache2/sites-enabled/ssl

"/etc/apache2/sites-enabled/ssl" should look like this:

 

NameVirtualHost *:443

<VirtualHost *:443>

        ServerAdmin webmaster@localhost

 SSLEngine On

 SSLCertificateFile /etc/apache2/ssl/apache.pem

 ...

 

 

 

In /etc/apache2/ports.conf, add Listen 443

sudo vi /etc/apache2/ports.conf

 

----------------------------------------------------------------------

 

Install jffnms (Just for Fun Network Monitoring System)

 

sudo apt-get install jffnms libapache2-mod-php4 php4 php4-mysql php4-snmp php4-gd2 snmpd nmap smokeping syslog-ng tftpd smsclient graphviz ntp php4-pear snmp libpng12-0 libgd2 tmpreaper fping

 
You will be prompted for a few things during the Install

Now JFFNMS will ask you some questions:
	JFFNMS Configuration (Database Type) - select mysql and press ENTER
	JFFNMS Configuration (Admin Password) - press ENTER ( we will set the admin password later)
	JFFNMS Configuration (Application Password) - enter your PASSWORD and press ENTER
	
	




sudo cp /etc/jffnms/apache.conf /etc/apache2/conf.d/jffnms.conf

 

# Restart the web server

 

Modify the php.ini files

 

sudo vi /etc/php4/apache2/php.ini

 

#Search for memory_limit = 8M and change it to

memory_limit = 32M

 

#Search for register_globals = Off and change it to

register_globals = On

 

sudo /etc/init.d/apache2 restart

 

# Go to your web browser and finish the setup:

 

[https://your.server.name/jffnms/admin/setup.php](https://your.server.name/jffnms/admin/setup.php)

 

# Setup you site name
Set SMSClient for SMS via Modem to /usr/bin/sms_client 

# Check "Debugging/Logging Enabled"

# Check "Request Authentication to access Setup"

#When finished click "Save Changes" button at bottom of page

 

When the page comes back click "Main" in the upper right hand corner of the page.  It should take you to the following link:

 

[https://your.server.name/jffnms/](https://your.server.name/jffnms/)

 

Login using the default:

user: admin

pass: admin

 



# Secure mysql

mysqladmin -u root password "password"


-------------------------------End Ubuntu JFFNMS Install Instructions-----------------------------------

---


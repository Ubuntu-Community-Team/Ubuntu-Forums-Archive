---
title: "Cant view .php docs in browsers shows up as php code"
date: 2006-12-10
forum: Server Platforms
---

### Post by Bill007 on 2006-12-10
Kia Ora 

Cant view .php docs in browsers shows up as php code even phpmyadmin is showing as code  

Any clues do I have to adjust any config files

this is whats been loaded so far 


this is what I ve installed I run 6.10 edgy server this is for the php
[B]
apt-get install[/B] autoconf automake1.4 autotools-dev libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php-pear php5-ldap php5-mhash php5-mysql php5-mysqli php5-snmp php5-sqlite php5-xmlrpc php5-xsl php5-imap php5-mcrypt php5-pspell


**apt-get install** mysql-server mysql-client libmysqlclient15-dev


**a2enmod php5**

Regards Bill007

---

### Post by Bill007 on 2006-12-10
I will answere this my self

In order to allow Apache to recognise PHP-enabled HTML files as being grist for mod_php's mill, you need to have a line like the following in your

Opened up /etc/apache2/apache2.conf 

[B]nano  /etc/apache2/apache2.conf
[/B]
 
Find the lines 

**ctl V** untill you get to this part of the config file you may have to add a line I did for php5 make sure to uncomment the ones applicable to your system

[B]#AddType application/x-httpd-php .php
#AddType application/x-httpd-php3 .php3
#AddType application/x-httpd-php4 .php4
AddType application/x-httpd-php5 .php5[/B]


And I bet your php can be seen in your browser

Yeha i have been scared of that config file for some time Ive broken apache a few times mucking around in there  do your research and make a copy of the original thats what Ive learnt Oh and also make one change at a time 

Regards Bill007

---


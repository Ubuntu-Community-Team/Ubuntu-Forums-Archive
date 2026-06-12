---
title: "can't run php  from html page"
date: 2012-02-05
forum: Server Platforms
---

### Post by dvks on 2012-02-05
UBUNTU 11.10, apache2, PHP5
PHP is not activated inside html file on UBUNTU machine but works under widows machine.
 
On the windows machine I had to to modify httpd.conf to add directives such as- "addhandler"
Do I need to add them also on the UBUNTU machine? if yes where, I understand that httpd.conf should not be used while I can't find all the settings I have ther (on the windows system) on the apache2.conf filender ubuntu 11.10 where are all these settings for example :
AddHandler application/x-httpd-php .php
AddType application/x-httpd-php .html  .htm
PHPIniDir "C:/Windows"

---

### Post by richardjh on 2012-02-06
I think you are on the wrong path. 
First check you have package libapache2-mod-php5 installed. If you install that using the package manager you shouldn't have to manually edit any files to get this working.

---


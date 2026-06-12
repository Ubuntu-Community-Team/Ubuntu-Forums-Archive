---
title: "read me first lamp ,phpmyadmin"
date: 2012-01-03
forum: Server Platforms
---

### Post by shubham1 on 2012-01-03
hello all
when somebody setups a lamp server then he has many questions which are mostly common so here are the faqs
**how to setup lamp**
Here is the url it will explain every thing
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
**If you get this error**
***apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for [ServerName]("https://help.ubuntu.com/community/ServerName")*** 
open a terminal and enter the following command
```
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
```**where is web server folder**
it is loctated in /var/ folder
location:/var/www/

i** am not getting permission to acces /var/www/**
```
sudo chown username /var/www/
```and then
```
sudo chmod -R 777 /var/www/ 
```by this you will have access to create,modify and delete files and folders 
other options:
(they might be more difficult but secure)
[http://ubuntuforums.org/showpost.php?p=11499998&postcount=5](http://ubuntuforums.org/showpost.php?p=11499998&postcount=5)
**phpmyadmin does not allow no password**
open a terminal and type
```
sudo gedit /etc/phpmyadmin/config.inc.php 
```Add the following line if it does not exist in the configuration file. 
```
$cfg['Servers'][$i]['AllowNoPassword'] = TRUE;
```[B]
where is php ini file[/B] **located**
it is located in
/etc/php5/apache2/php.ini
to open it open a terminal and type the following command
```
sudo gedit /etc/php5/apache2/php.ini

```**How to get information about php server?**
in an php file write the following code
```
<?php phpinfo()?>
```**I forgot my mysql password. How do I reset it?**
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
[B]how to set php to display errors:
[/B]open a terminal and type the following code:
```
sudo gedit /etc/php5/apache2/php.ini
```then search for display_errors
then it will be off set to on
_import note:_
there are more than one display_error and the one which is actual for me was located at line no. 538 see the image for nearby lines
**how to restart/start/stop apache**
*restart apache*:
open a terminal
and type the following code:
```

sudo /etc/init.d/apache2 restart

```*stop apache*
```

sudo /etc/init.d/apache2 stop

```*start apache*
```

sudo /etc/init.d/apache2 start

```**how to start , stop  , restart mysql:**
these commands are to be typed in terminal
*start*
```
sudo /etc/init.d/mysql start
```*stop*
```

sudo /etc/init.d/mysql stop

```*restart*
```

sudo /etc/init.d/mysql restart

```**how to check the status of mysql:**
open a terminal and type the following code
```
sudo /etc/init.d/mysql status
```if anything need to be added please post your reply here these were the very common questions.

---

### Post by volkswagner on 2012-01-03
Firstly thanks for your post.  The poor search function on UbuntuForums, and posts that don't utilize key words makes finding solutions tough.  Using a search engine such as Google with keywords including "ubuntu server" can yield better results.

> **shubham1 said:**
> 

i** am not getting permission to acces /var/www/**
```
sudo chown username /var/www/
```
and then
```
sudo chmod -R 777 /var/www/ 
```
by this you will have access to create,modify and delete files and folders


I don't think people should be making their web root world writeable.  There are several solutions for allowing user to write to web root folder without making it world write.  Although they may not be as easy, it can be more secure.  

For example [this post]("http://ubuntuforums.org/showpost.php?p=11499998&postcount=5") shows a few options.

This is a heavily talked about issue, which I have yet to find a solution that will satisfy everyone's specific needs.

---

### Post by shubham1 on 2012-01-03
thanks a lot for your reply i have edited my post

---


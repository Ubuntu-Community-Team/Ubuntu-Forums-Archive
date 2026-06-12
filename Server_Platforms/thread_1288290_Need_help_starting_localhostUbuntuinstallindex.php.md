---
title: "Need help starting localhost/Ubuntu/install/index.php to install Discuz!7"
date: 2009-10-11
forum: Server Platforms
---

### Post by amylase on 2009-10-11
Hi,

My aim is to install Discuz!7.00 on Ubuntu 8.10 which has Apache2, PHP5, MySQL and phpMyAdmin and ModMono onboard to my best knowledge. My question in short is, how do I get [http://localhost/Ubuntu/install/index.php](http://localhost/Ubuntu/install/index.php) to run? Currently I get a pop up window saying it's a binary file and asks me where to save it.

The following is a run down of steps I've taken so far to reach this box mentioned above:

I followed the instructions on this website and I think I installed Apache 2, PHP5, MySQL and phpMyAdmin on Ubuntu 8.10:
[http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/]("http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/")

It asks me to issue a series of commands as follows:
> sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

sudo gedit /var/www/nass.php
<? phpInfo(); ?>
Point browser to [http://localhost/nass.php](http://localhost/nass.php)

sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
sudo apt-get install phpmyadmin
sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
Go to the phpMyAdmin login page by pointing your browser to: [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php)

Did all of above. To my surprise not a critical error was encountered. 

I ran [http://localhost/Ubuntu/](http://localhost/Ubuntu/)
and I do see "It works like charm!" successfully.

I created the file /var/www/nass.php whose content is 
<? phpInfo(); ?>
When I point my browser to [http://localhost/nass.php](http://localhost/nass.php) I see lots of information abotu my php5 installation so I guess it installed alright.

In addition I also installed ModMono which is an Apache module which provides ASP.NET support for Apache web server, following steps from this website:
[http://ubuntuexperiment.wordpress.com/2009/01/29/running-aspnet-applications-in-ubuntu-using-modmono/]("http://ubuntuexperiment.wordpress.com/2009/01/29/running-aspnet-applications-in-ubuntu-using-modmono/")

Next I downloaded Discuz! version 7.00 from here [http://download.comsenz.com/Discuz/7.0.0/]("http://download.comsenz.com/Discuz/7.0.0/")
and followed its readme instructions. I copied the content of "upload" to "/var/www/Ubuntu" on my computer.

I issued "chmod -R 777" to the following directories as described in readme:
> ./config.inc.php

./attachments

./forumdata

./forumdata/cache

./forumdata/templates

./forumdata/threadcaches

./forumdata/logs

./uc_client/data/cache


Next I hoped to start installing Discuz! via a web browser by typing in this line into the URL box: [http://localhost/Ubuntu/install/index.php](http://localhost/Ubuntu/install/index.php)

I see this window pop up: Title of window is "Opening index.php". The box  says: You have chosen to open index.php which is a BIN file from [http://localhost](http://localhost). Would you like to save this file? [Cancel] [Save file]

To double check, I opened the index.php file and I see legit php code, not machine code. So the computer is wrong in telling me this is a binary file.

Now I'm a bit lost. It seems to me my computer is refusing to run 
[http://localhost/Ubuntu/install/index.php](http://localhost/Ubuntu/install/index.php)
but previously pointing my browser to [http://localhost/nass.php](http://localhost/nass.php) did work okay. So my question is, how do I get [http://localhost/Ubuntu/install/index.php](http://localhost/Ubuntu/install/index.php) to start running??

Hope I made my question clear. Thanks a lot.

---

### Post by windependence on 2009-10-12
Put this at the end of your config file, or in your httpd.conf file;

```
AddHandler application/x-httpd-php .php
```

Then restart apache:

```
mysever# apachectl restart
```

Then run your PHP file.

-Tim

---

### Post by amylase on 2009-10-15
Hi Tim

Thanks for the reply. I found three httpd.conf on my hard disk:
/etc/apache2
/etc/gforge
/etc/phpmyadmin

The one under etc/phpmyadmin is quite big (328 bytes) with lots of things in it. Where in this file do I insert your line?

I added your line to /etc/apache2/httpd.conf which was empty to start with. So I just added your line in.

I restarted apache by issuing: 
> sudo /etc/init.d/apache2 restart

Then I pointed my browser to [http://localhost/Ubuntu/install/index.php](http://localhost/Ubuntu/install/index.php)
Still get the same pop up window asking where I want to save this BIN file.

Interestingly when I copied everything under Ubuntu to under localhost, and then pointed browser to [http://localhost/install/index.php](http://localhost/install/index.php), this time it worked. The php file started running and installed Discuz!7 no problem. I hope this piece of information is useful in eliciting what the cause might be for [http://localhost/Ubuntu/install/index.php](http://localhost/Ubuntu/install/index.php) not running....

Ideally I still would like it to go under the folder Ubuntu, so that I can run two separate forums, one Discuz is under Ubuntu folder and another Discuz is under Ubuntu2.

Please help~ Thanks very much.

---


---
title: "Installing Apache2 With PHP5 And MySQL Support On Ubuntu 12.04 LTS (LAMP)"
date: 2012-05-10
forum: Sudan Team
---

### Post by suspect x on 2012-05-10
First Login as root
```
sudo su
```
Installing MySQL 5
```
apt-get install mysql-server mysql-client
```
[SIZE="2"][SIZE="1"]You will be asked to provide a password for the MySQL root user - this password is valid for the user root@localhost as well as [email]root@server1.example.com[/email], so we don't have to specify a MySQL root password manually later on:

New password for the MySQL "root" user: <-- yourrootsqlpassword
Repeat password for the MySQL "root" user: <-- yourrootsqlpassword[/SIZE][/SIZE]
 Installing Apache2
```
apt-get install apache2
```
[SIZE="1"]Now direct your browser to [http://127.0.0.1](http://127.0.0.1), and you should see the Apache2 placeholder page (It works!):[/SIZE]
 Installing PHP5
```
apt-get install php5 libapache2-mod-php5
```
We must restart Apache afterwards:
```
/etc/init.d/apache2 restart
```
 Testing PHP5 / Getting Details About Your PHP5 Installation
```
vi /var/www/info.php
```
```
[PHP]<?php
phpinfo();
?>[/PHP]
```
Now we call that file in a browser (e.g. [http://127.0.0.1/info.php):](http://127.0.0.1/info.php):)
[IMG]http://static.howtoforge.com/images/lamp_ubuntu_12.04/big/2.png[/IMG]
[SIZE="1"]As you see, PHP5 is working, and it's working through the Apache 2.0 Handler, as shown in the Server API line. If you scroll further down, you will see all modules that are already enabled in PHP5. MySQL is not listed there which means we don't have MySQL support in PHP5 yet.[/SIZE]
 Getting MySQL Support In PHP5
To get MySQL support in PHP, we can install the php5-mysql package. It's a good idea to install some other PHP5 modules as well as you might need them for your applications. You can search for available PHP5 modules like this:
```
apt-cache search php5
```
Pick the ones you need and install them like this:
```
apt-get install php5-mysql php5-curl php5-gd php5-intl php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
```
Now restart Apache2:
```
/etc/init.d/apache2 restart
```
[SIZE="1"]Now reload [http://127.0.0.1/info.php](http://127.0.0.1/info.php) in your browser and scroll down to the modules section again. You should now find lots of new modules there, including the MySQL module:[/SIZE]
[IMG]http://static.howtoforge.com/images/lamp_ubuntu_12.04/big/3.png[/IMG]
phpMyAdmin
```
apt-get install phpmyadmin
```
you will see the following questions:

[COLOR="DeepSkyBlue"]Web server to reconfigure automatically: <-- apache2
Configure database for phpmyadmin with dbconfig-common? <-- No
[/COLOR]
Afterwards, you can access phpMyAdmin under [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/)
[IMG]http://static.howtoforge.com/images/lamp_ubuntu_12.04/big/4.png[/IMG]

---

### Post by subramanianpillai on 2012-07-12
I messed up with the last part of installation.

After installing 
phpmyadmin, in the following step
[COLOR=DeepSkyBlue]
Web server to reconfigure automatically: <-- apache2

[COLOR=Black]I didn't enter apache2 rather just pressed 'enter' key.
now, I'm not able to work with phpmyadmin.
localhost is working.
but i cant follow "localhost/phpmyadmin"
error 404
Please Help!
[/COLOR][/COLOR]

---

### Post by suspect x on 2012-07-16
try to reinstall phpMyAdmin
```
apt-get install phpmyadmin
```

---

### Post by nenadcvetkovic on 2013-02-02
Try this:
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf

Apparently, this serves to "symlink the phpMyAdmin conf file within the apache2/conf.d/" courtesy of pete fisher: [http://blog.peterfisher.me.uk/2012/06/27/solution-to-phpmyadmin-throwing-a-404-error/](http://blog.peterfisher.me.uk/2012/06/27/solution-to-phpmyadmin-throwing-a-404-error/)

---


---
title: "Can I install Apache, MySQL &amp; PHP all in one step?"
date: 2007-02-23
forum: Server Platforms
---

### Post by caffienda on 2007-02-23
I was wondering if it was possible to write a script that would allow me to install all the required components of Apache, MySQL & PHP all at one time.  I'm running 6.10 desktop and would like to have the same functions as server, but with the nice GUI of the desktop system.    I know that you can install a desktop manager on the server, but I would like to learn how to install the server this way, because I know a bunch of people who want to do it and I can then show them.  

So what I would really like to know is, what is installed when you check the LAMP server button on the Edgy Server CD install?  
Aslo, is PHP5 backwards compatible with PHP4?  If I install 5, do I need 4?

sudo apt-get install 
apache2 
php5 
libapache2-mod-php5 
mysql-server
mysql-admin
php5-xsl 
php5-gd 
php-pear 
libapache2-mod-auth-mysql 
php5-mysql 
phpmyadmin
python
libapache2-mod-python

********************************************************
sudo gedit /etc/mysql/my.cnf
comment out:
...
#bind-address           = 127.0.0.1
...
********************************************************
sudo gedit /etc/php<version>/apache2/php.ini
uncomment the ";extension=mysql.so" line 
...
extension=mysql.so
...
********************************************************
sudo gedit /etc/apache2/mods-available/mod_python.conf
add the following lines

AddType application/x-httpd-python .py
AddHandler mod_python .py
PythonHandler mod_python.publisher
PythonDebug On
********************************************************


sudo /etc/init.d/apache2 restart
********************************************************

This is about as much as I figured out, there is probably a good bit wrong.  Is there an easier way to setup a LAMP server?  Also, configuring MySQL is pretty tricky, I've been trying to find a good guide for it, suggestions.?

---

### Post by GoBieN on 2007-02-23
From the perfect setup how-to:

> 10 MySQL

In order to install MySQL, we run

apt-get install mysql-server mysql-client libmysqlclient12-dev

We want MySQL to listen on all interfaces, not just localhost, therefore we edit /etc/mysql/my.cnf and comment out the line bind-address = 127.0.0.1:

vi /etc/mysql/my.cnf

[...]
#bind-address           = 127.0.0.1
[...]

Then we restart MySQL:

/etc/init.d/mysql restart

netstat -tap

In the output you should see a line like this one:

tcp        0      0 *:mysql                 *:*                     LISTEN     4997/mysqld

Run

mysqladmin -u root password yourrootsqlpassword
mysqladmin -h server1.example.com -u root password yourrootsqlpassword

to set a password for the user root (otherwise anybody can access your MySQL database!).

13 Apache/PHP5

Now we install Apache:

apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 ssl-cert

Next we install PHP5:

apt-get install autoconf automake1.4 autotools-dev libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php-pear php5-ldap php5-mhash php5-mysql php5-mysqli php5-snmp php5-sqlite php5-xmlrpc php5-xsl php5-imap php5-mcrypt php5-pspell

You will be asked the following question:

Continue installing libc-client without Maildir support? <-- Yes

Next we edit /etc/apache2/apache2.conf

vi /etc/apache2/apache2.conf

and change DirectoryIndex to

[...]
DirectoryIndex index.html index.htm index.shtml index.cgi index.php index.php3 index.pl index.xhtml
[...]

Edit /etc/apache2/ports.conf and add Listen 443:

vi /etc/apache2/ports.conf

Listen 80
Listen 443

Now we have to enable some Apache modules (SSL, rewrite, suexec, and include):

a2enmod ssl
a2enmod rewrite
a2enmod suexec
a2enmod include

Reload the Apache configuration:

/etc/init.d/apache2 force-reload 
Some of it may have a little syntax change, since it was for dapper but mostly its just copy paste.

---

### Post by caffienda on 2007-02-25
That is a very good tutorial!  It seemed to install very easily.   Also, do you have a link to the "perfect setup"?  sounds like a pretty good guide!

I did get the following errors:
> Setting up apache2-common (2.0.55-4ubuntu4) ...
Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-prefork (2.0.55-4ubuntu4) ...
 * Starting apache 2.0 web server...           
      apache2: Could not determine the server's fully qualified domain name, using 192.168.1.142 for ServerName
                
caffiendo@UbServ:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server...                                   apache2: Could not determine the server's fully qualified domain name, using 192.168.1.142 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 192.168.1.142 for ServerName

---

### Post by GoBieN on 2007-02-26
Seems they did an update on the tutorial for edgy:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

But you don't need the ISPconfig part, and i would skip the mail part to. Unless you actually plan to use your server as a mail receiving server for a number of users.

I don't so it just set postfix to relay all trough: smtp.isp.com and made an alias e-mail for root and my user.

oh and those warnings, all nothing to worry about.

Perhaps you do want to set a hostname for your server, do it like this recplace server.1... with what you want:

> echo server1.example.com > /etc/hostname

Afterwards, run to check:

hostname
hostname -f

---

### Post by grandmk on 2007-02-26
There is nothing wrong. Try visiting [http://localhost](http://localhost) (or your IP) in a web browser and you should see that Apache is working fine. 

The warning you are getting is because Apache is checking for your computer's fully qualified domain name in *hostname* and when its not finding one set, it defaults to your IP (other users reading this post may note Apache defaults them to localhost/127.0.0.1 instead of an actual LAN IP; this is fine). The warning you see is from Apache letting you know that it is doing this. 

Try checking out your /etc/hostname file: 

```
cat /etc/hostname
```

If you just want to use your Apache install for web development, and you don't care that its not accessible to those outside your LAN, you should already be good to go. Visiting [http://your.ip.address](http://your.ip.address) should work. 
 
============================

HOWEVER...

If you want your Apache server to host [www.yourdomain.com](www.yourdomain.com) or [www.your.subdomain.com](www.your.subdomain.com), you might want to consider getting a DNS record that points to your IP address. You could set up your own DNS server (BIND -- warning: advanced) or subscribe to a free DNS service like afraid.org (which can also give you a free subdomain: yourname.afraid.org). Once everything is set up, and your URL points to your IP, you'd want to change your hostname to your computer's fully-qualified name by editing /etc/hostname and restarting apache. 

I notice that your IP looks like a LAN IP. There are a host of problems if you are using a home Internet connection and a cheapo D-Link/Linksys/whatever router. First, you'd have to tell your router to forward any web requests it receives to the internal IP of your server on the LAN (look up "port forwarding"). You may also want to tell your router to always assign the same IP to your Apache server computer every time so the target for your port forwarding never changes. How to do this is different for each and every brand/model of router, so Google up some help specific to your hardware. 

A final issue is a home ISP (even if its DSL or cable) will periodically change your IP address on you. This means your DNS records (domain name/ subdomain) won't point to your destination any more! The target has moved! Look up "Dynamic DNS" for help on resolving this issue. Note that some recent models of home routers even support popular dynamic dns services in their web-based admin tools. 

I'm not going to get into any more details as these are all networking issues and are unrelated to properly installing and configuring Apache. Use the keywords I've provided above to find relevant topics that can help you if your goal is to host yourdomain.com. 

PLEASE NOTE: if you are using your server for business applications, you should get a proper ISP for this purpose and not a home ISP. They will give you a nice static IP that will never change, and will be more reliable.

---

### Post by MianoSM on 2007-04-10
I'm receiving an error for libmysqlclient12-dev stating that it has no installation candidate, is this normal?

Everything else seems to work fine though....

---

### Post by revertex on 2007-04-12
What about the easy way?

Install aptitude, browse to > tasks > Unrecognized tasks > lamp-server, select all packages, install, you're done.

---

### Post by bigfatdummy on 2007-04-26
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server phpmyadmin

Try that

---


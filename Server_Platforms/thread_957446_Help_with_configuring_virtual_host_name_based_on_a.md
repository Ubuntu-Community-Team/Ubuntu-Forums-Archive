---
title: "Help with configuring virtual host name based on apache"
date: 2008-10-24
forum: Server Platforms
---

### Post by wendowed on 2008-10-24
I AM TRYING TO SETUP A SERVER WITH 4 WEBSITES THAT WILL BE ACCESSIBLE ON THE INTERNET. I HAVE TRIED BUT I AM FACED WITH TWO MAJOR PROBLEMS. I AM VERY NEW TO UBUNTU AND IT WOULD HELP IF WHEN YOU GIVE YOUR ANSWER, ASSUME THAT I KNOW NOTHING ABOUT IT. GIVE THE FULL CODE e.g. _**sudo apt-get install apache2**_ INSTEAD OF SAYING INSTALL APACHE2. BE A BIT SPECIFIC PLEASE. 

1. IN THE DEFAULT /VAR/WWW/ SITE, I DO NOT HAVE PERMISSION TO EDIT THE DEFAULT PAGE THOUGH AM LOGGED IN AS THE ROOT. 

2. I HAVE A PROBLEM WITH HOW TO EDIT THE HTTPD FILE AFTER MAKING A NEW COPY OF THE DEFAULT /VAR/WWW/DEFAULT FOLDER AND CHANGING THE COPY TO /VAR/WWW/MYNEWSITE. WHAT DO I WRITE IN THE httpd.conf FILE TO CONNECT THE SITE TO THE NameVirtualHost *? I think there are a number of folders i need to edit but reading through all this material i find that its written for specialists not starters. 

Below is the error message i get. 

[B] /etc/init.d/apache2 restart
 * Restarting web server apache2                                               [Fri Oct 24 15:43:04 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Oct 24 15:43:04 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Oct 24 15:43:14 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Oct 24 15:43:14 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                        [ OK ][/B]

PLEASE HELP. MANY KIND REGARDS.

WENDOWED

---

### Post by canh_nguyen on 2008-10-24
Here is my apache2.conf
```
........Other config..............
........................................
# Include the virtual host configurations:
#NameVirtualHost 127.0.1.1:80
Include /etc/apache2/sites-enabled/  

```
In /etc/apache2/sites-available/
make file with same name of domain(recommend).
etc : domain1.com
sudo gedit /etc/apache2/sites-available/domain1.com
```
<Directory "/var/www/domain1.com">

	Order allow,deny

	Allow from all

</Directory>
<VirtualHost *>

	DocumentRoot "/var/www/domain1.com/htdocs"

	ServerName "www.var/www/domain1.com"

	ServerAlias "var/www/domain1.com"

	ErrorLog /var/www/domain1.com/logs/error_log

	CustomLog /var/www/domain1.com/logs/access_log combined

</VirtualHost>
```

make a domain2 as domain1

and in terminal type:
a2ensite domain1.com
a2ensite domain2.com
:)

---

### Post by Vegan on 2008-10-24
in the sites-available I name every *.conf so that apache2 can recognize them.

my apache2.conf is unchanged

my sites are names url.ext.conf where I have 5 running fine

---

### Post by Iowan on 2008-10-24
I found [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To helpful in setting up my LAMP server.

---

### Post by wendowed on 2008-10-25
> **canh_nguyen said:**
> Here is my apache2.conf
```
........Other config..............
........................................
# Include the virtual host configurations:
#NameVirtualHost 127.0.1.1:80
Include /etc/apache2/sites-enabled/  

```
In /etc/apache2/sites-available/
make file with same name of domain(recommend).
etc : domain1.com
sudo gedit /etc/apache2/sites-available/domain1.com
```
<Directory "/var/www/domain1.com">

	Order allow,deny

	Allow from all

</Directory>
<VirtualHost *>

	DocumentRoot "/var/www/domain1.com/htdocs"

	ServerName "www.var/www/domain1.com"

	ServerAlias "var/www/domain1.com"

	ErrorLog /var/www/domain1.com/logs/error_log

	CustomLog /var/www/domain1.com/logs/access_log combined

</VirtualHost>
```

make a domain2 as domain1

and in terminal type:
a2ensite domain1.com
a2ensite domain2.com
:)
still having problems. do i need to edit **httpd.conf** for this? 

the error this time is **host-based authentication failed. ** 

should i add or change the value of ***VirtualHost **** to **_VirtualHost domain1.com_** or something like that?

should i uncommnt this line in **#NameVirtualHost 127.0.1.1:80**
apache2.conf? will this action activate the nem server.

I AM BASICALLY TRYING TO SET UP A NAME BASED VIRTUAL SERVER BECAUSE I HAVE A DYNAMIC IP WITH DYNDNS.COM

---


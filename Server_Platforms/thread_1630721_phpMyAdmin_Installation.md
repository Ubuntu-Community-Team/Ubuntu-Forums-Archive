---
title: "phpMyAdmin Installation"
date: 2010-11-25
forum: Server Platforms
---

### Post by BMorganVA on 2010-11-25
I'm trying to install phpMyAdmin on my Ubuntu 10.10 server. I type the following command (I don't use "sudo" because I'm logged in as root, I know its not safe):
> apt-get install phpmyadmin
and go through the installation. I allow the installation to configure the database, and I chose the correct server (Apache2), when it asks for passwords, I use the same password that I use for the rest of the server (i.e. it is the account password for root, sudo, and my account).

Once the installation is complete, I try and access it from a computer on the same network. I type "http://***.***.*.*/phpmyadmin" and I get the message saying the directory isn't there. I go into Webmin to confirm that the directory isn't there, and it isn't.

My questions are (1) Why isn't the phpmyadmin directory in my Apache Server root? (2) Is it installed with apt-get, if so, where? (3) How do I know what server I selected for it to install to? (4) What do I need to do to get it to install correctly?

I know this is a lot of questions, so I want to give a big THANK YOU in advance.

THANK YOU FOR YOUR HELP!

---

### Post by mbaas on 2010-11-25
phpmyadmin installs in /usr/share/phpmyadmin, and creates a directory alias in the apache configuration (/etc/apache2/conf.d/phpmyadmin.conf which is a symlink to /etc/phpmyadmin/apache.conf). IIRC, i had to reboot my machine before everything worked as it should.

---

### Post by BMorganVA on 2010-11-25
I restarted my server. When I tried to access it again, there was still no phpmyadmin directory in my site root (/var/www). When I look in /etc/apache2/conf.d, there was no phpmyadmin.conf, but there was apache.conf in /etc/phpmyadmin.

---

### Post by James78 on 2010-11-25
There's not supposed to be any phpmyadmin directory in /var/www, however there IS supposed to be a conf file; /etc/apache2/conf.d/phpmyadmin.conf (as said earlier, it's a symlink to /etc/phpmyadmin/apache.conf)

You could try a dpkg-reconfigure phpmyadmin, or you could try uninstalling and reinstalling, or even just a reinstall. However there should be files in /etc/phpmyadmin ..

---

### Post by BMorganVA on 2010-11-25
Then where is the site root supposed to be for the Apache Server?

---

### Post by James78 on 2010-11-25
Your site root hasn't moved or changed, it's the same. It states here in the configuration, an alias /phpmyadmin pointing to directory /usr/share/phpmyadmin

/etc/apache2/conf.d/phpmyadmin.conf
```
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options FollowSymLinks
	DirectoryIndex index.php

	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>
```

---

### Post by BMorganVA on 2010-11-25
But there is no "/etc/apache2/conf.d/phpmyadmin.conf". What am I doing wrong? How I know if I choose the server?

---

### Post by James78 on 2010-11-25
> **James78 said:**
> There's not supposed to be any phpmyadmin directory in /var/www, [B]however there IS supposed to be a conf file; /etc/apache2/conf.d/phpmyadmin.conf (as said earlier, it's a symlink to /etc/phpmyadmin/apache.conf)

_You could try a dpkg-reconfigure phpmyadmin, or you could try uninstalling and reinstalling, or even just a reinstall. However there should be files in /etc/phpmyadmin .._[/B]
Try these steps first, as I posted earlier.

---

### Post by BMorganVA on 2010-11-25
There have always been files in /etc/phpmyadmin, but there is no /etc/apache2/conf.d/phpmyadmin.conf.

I tried uninstalling/reinstalling phpmyadmin, and nothing changed. dpkg-reconfigure says phpmyadmin isn't insalled, and apt-get says its the newest version possible.

Thanks for the help again.

---

### Post by windependence on 2010-11-25
You probably missed this:
 
 
To set up under Apache all you need to do is include the following line in /etc/apache2/apache2.conf. 
 
```
 
Include /etc/phpmyadmin/apache.conf

```
 
Look at this article:
 
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)
 
 
-Tim

---

### Post by BMorganVA on 2010-11-25
I didn't work. I thought I didn't need to do that because I'm using 10.10, also when I look in Webmin, it says my Apache Webserver is down, does that have anything to do with it?

---

### Post by windependence on 2010-11-25
It sure does. Apache must be running for phpMyadmin to work. From the command line do a:
 
apachectl start
 
 
-Tim

---

### Post by BMorganVA on 2010-11-25
I run the command, but it says its already running, I'm also able to access my server from a different computer on the same network. I reinstalled apache2, php5, and phpmyadmin, but there is still no /etc/apache2/conf.d/phpmyadmin.php

---

### Post by windependence on 2010-11-25
Try this:
 
```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
 
sudo /etc/init.d/apache2 reload
``` -Tim

---

### Post by BMorganVA on 2010-11-25
I'm so stupid. I forgot to select the server!!!!! I'm sorry for all this trouble, but thanks for your time!!!!

---

### Post by windependence on 2010-11-26
No trouble at all. If the link I posted helped you realize that, then it wasn't all for nothing. :-)
 
-Tim

---

### Post by willow315 on 2011-05-04
I am running Ubuntu 10.04 thru VirtualBox on a MAC. I've managed to get Apache, MySQL and PHP installed using aptget...but I cannot get PHPMyAdmin working right.
 
I have the same problem with no /etc/apache2/conf.d/phpmyadmin.conf. I read somewhere that you had to create a symlink which you say should happen automatically. It was now so long ago....since I gave up trying to make this work, that I can't exactly remember where that is...but now when I type in

[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) I get a directly list but the phpmyadmin login does not appear. I have obviously mess everything up. How can I uninstall everything to do with PHPMyAdmin and start over. 

I have attempted to just reinstall over what I had, but that is not helping me. 

Would you be willing to assist me? I know that this thread is on the right track, since this person was able to solve their problem. I thought for sure I'd selected the server, though. But it was a while ago that I attempted this. Thx. WCW

---

### Post by willow315 on 2011-05-04
Well, I thank whoever wrote this. I just tried resetting that symlink  and voila! all is well. I can bring up the login interface for  PHPMyAdmin AND log in successfully. Interestingly enough, though the  password I thought I'd be using to get into PHPMyAdmin did not work, but  the root password for MySQL did. So, all is well, and thianks! WCW

---


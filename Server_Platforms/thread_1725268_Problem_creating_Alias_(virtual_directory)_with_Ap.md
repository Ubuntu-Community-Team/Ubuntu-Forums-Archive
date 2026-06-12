---
title: "Problem creating Alias (virtual directory) with Apache 2.2"
date: 2011-04-09
forum: Server Platforms
---

### Post by TMachado on 2011-04-09
**EDIT** I realized that with info.php at /var/www happens the same, so it's php problem? I reinstalled using: (i'm at ubuntu 10.10)

sudo apt-get install apache2 php5 libapache2-mod-php5

but happens the same. localhost/index.html is fine but localhost/index.php download file :( What can I do?

> 
I have my web applications here

/media/........../www/

and my index.php (apkitchen web app) is under /www/apkitchen/index.php

So I did was is stated here
[https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-apache-http-server.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-apache-http-server.html)

and created a new file 'alias', with

[QUOTE]Alias /www /media/....../www/

<Directory /media/...../www/>
    Options Indexes FollowSymLinks
    AllowOverride All
    Order allow,deny
    Allow from all
</Directory>

Restarted apache2, but the problem is, when I go to [http://localhost/www](http://localhost/www), ok I got all my web applications, but if I choose one (apkitchen for example) my browser prompts the download of the index.php file.[/QUOTE]

What am I doing wrong?

---

### Post by SeijiSensei on 2011-04-09
Do you have /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load installed?  Did you restart apache with "sudo service apache2 restart"?

If the files aren't in mods-enabled, just copy them (as root with sudo) from /etc/apache2/mods-available/ to mods-enabled.

---

### Post by TMachado on 2011-04-09
> **SeijiSensei said:**
> Do you have /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load installed?  Did you restart apache with "sudo service apache2 restart"?

If the files aren't in mods-enabled, just copy them (as root with sudo) from /etc/apache2/mods-available/ to mods-enabled.

Looks like the problem is at my apache/php installation. A few days ago I removed all those packages.

So i did this

sudo apt-get remove --purge apache2 php5
sudo apt-get remove --purge libapache2-mod-php5
sudo apt-get install php5 apache2 libapache2-mod-php5

but I get this:

> Setting up apache2-mpm-prefork (2.2.16-1ubuntu3.1) ...
ERROR: Module cgid does not exist!
ERROR: Module cgi does not exist!
It looks like you've deleted /etc/apache2/mods-available/cgid.load, so mod_cgid cannot be enabled.  To fix this, please purge and reinstall apache2.2-common.
.: 49: Can't open /etc/apache2/envvars
invoke-rc.d: initscript apache2, action "start" failed.


So I "purged and reinstalled" apache2.2-common, but always that that error.

Any ideas, or do I have to reinstall ubuntu? :(

EDIT: I eventually installed all those packages without error, and apache is running again, but I'm still downloading php files instead run them :(

***_EDIT2:_*** What the f***....

I tried with Firefox, no problem. I was running chrome. Well. -1 point for chrome :S

---


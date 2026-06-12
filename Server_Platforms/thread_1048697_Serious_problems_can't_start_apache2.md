---
title: "Serious problems: can't start apache2"
date: 2009-01-23
forum: Server Platforms
---

### Post by Mamsaac on 2009-01-23
I get the following error:

```
mamsaac@mamsaac-laptop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                       apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                                              [fail]
```

I have checked if any app is using the port, but nothing seems to be doing so. I checked configuration... I haven't changed anything recently except for something at the php configuration, but that shouldn't affect the behavior. Then I proceeded to uninstall and reinstall, but with and without --purge. Nothing.

Apps I reinstalled:

apache2 apache2-utils apache2-mpm-prefork apache2.2-common jetty libapache2-mod-fcgid libapache2-mod-python php5 php5-dev php5-common php5-gd php5-cli php5-mysql php5-pgsql php5-sqlite php5-odbc libapache2-mod-php5 php-pear php5-mcrypt phpmyadmin zend-framework libzend-framework-php python-django

I've googled for almost 2 hours... I don't know when this started, but can't be longer than a day. I don't know what could have triggered this.

Any suggestions?

---

### Post by albinootje on 2009-01-23
> **Mamsaac said:**
> I get the following error:

```
mamsaac@mamsaac-laptop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                       apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                                              [fail]
```

I have checked if any app is using the port, but nothing seems to be doing so.

You checked : 
```

netstat -tan|grep 80

```
right ?
And you have jetty installed, at what port is that running, 8087 or something ?
What about the "unable to open logs" error ?
```

ls -la /var/log/apache2/*.log

```

---

### Post by albinootje on 2009-01-23
What happens after :
```

sudo /etc/init.d/apache2 restart

```
which is "restart" instead of "start".

---

### Post by Mamsaac on 2009-01-23
Ok, one by one:

```
mamsaac@mamsaac-laptop:~$ netstat -tan|grep 80
tcp        1      1 192.168.0.5:55945       91.189.94.12:80         LAST_ACK   
tcp        1      1 192.168.0.5:55946       91.189.94.12:80         LAST_ACK   
tcp        0      0 192.168.0.5:59127       168.83.82.141:80        ESTABLECIDO
tcp        0      0 192.168.0.5:42341       204.2.215.32:80         ESTABLECIDO

```

```
mamsaac@mamsaac-laptop:~$ ls -la /var/log/apache2/*.log
-rw-r----- 1 root adm  0 2009-01-23 17:35 /var/log/apache2/access.log
-rw-r----- 1 root adm  0 2009-01-23 17:35 /var/log/apache2/error.log
-rw-r--r-- 1 root root 0 2008-10-31 00:18 /var/log/apache2/other_vhosts_access.log

```

And then... I just tried doing the restart.

Weird as hell, I had restarted (I just checked the bash log) many times, but this time it said ok. It runs... but prompts everything as a phtml. At least I get about 10 instances of apache2 running, which is good.

I have no idea what happened. I had been trying to solve this with the exact same commands for a while. I guess I will try to reinstall libapache2 mods for php and python.

---

### Post by albinootje on 2009-01-23
> **Mamsaac said:**
> It runs... but prompts everything as a phtml.

Okay, good that you're 1 step further now.
I have this with apache2 + php + squirrelmail on my desktop :

```

grep -r -i php /etc/apache2/
/etc/apache2/mods-enabled/php5.conf:<IfModule mod_php5.c>
/etc/apache2/mods-enabled/php5.conf:  AddType application/x-httpd-php .php .phtml .php3
/etc/apache2/mods-enabled/php5.conf:  AddType application/x-httpd-php-source .phps
/etc/apache2/mods-enabled/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
/etc/apache2/mods-enabled/php5.load:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
/etc/apache2/mods-available/php5.conf:<IfModule mod_php5.c>
/etc/apache2/mods-available/php5.conf:  AddType application/x-httpd-php .php .phtml .php3
/etc/apache2/mods-available/php5.conf:  AddType application/x-httpd-php-source .phps
/etc/apache2/mods-available/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
/etc/apache2/mods-available/php5.load:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
/etc/apache2/conf.d/squirrelmail:  <IfModule mod_php4.c>
/etc/apache2/conf.d/squirrelmail:    php_flag register_globals off
/etc/apache2/conf.d/squirrelmail:  <IfModule mod_php5.c>
/etc/apache2/conf.d/squirrelmail:    php_flag register_globals off
/etc/apache2/conf.d/squirrelmail:    DirectoryIndex index.php
/etc/apache2/conf.d/squirrelmail:  <Files configtest.php>

```

---

### Post by Mamsaac on 2009-01-23
Yeah, thanks =) I even modified some aspects that didn't allow me to use .psp AND .py as both PSP (I don't use Publisher with python for website development). Everything seems to be working fine now.

I only wish I knew what made all this happen.

---

### Post by albinootje on 2009-01-23
> **Mamsaac said:**
> Yeah, thanks =) I even modified some aspects that didn't allow me to use .psp AND .py as both PSP (I don't use Publisher with python for website development). Everything seems to be working fine now.

I only wish I knew what made all this happen.

I think you gave the answer to this already in your OP :
> 
I've googled for almost 2 hours... 


Drink lots of water or tea during all the hacking, makes you go to the toilet often enough to have a break from the monitor and get some fresh air. :)

---


---
title: "Dynamic IP and cron job"
date: 2006-12-13
forum: Server Platforms
---

### Post by satimis on 2006-12-13
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64

I have a script.php which is used to update the IP address of my domain on registrar's website.  I keep it on /etc/.  The IP address of the server only changes on connection.  Please advise how to create a "cron job" which will run the script after booting to update the IP address.

Is /etc/ the right directory for holding the script?

TIA

B.R.
satimis

---

### Post by chrisfay on 2006-12-13
Hey satimis, I recognize you from my forum at cjfay.com/forums. Strange, we meet again...:mrgreen: 

Assuming your PHP was installed as an Apache module, to run PHP scripts via cron you need to install the Lynx browser. Once this is installed, configure your crontab as follows:

```
* * * * * lynx -dump http://localhost/script.php
```

You can create a relative link instead of the absolute. If you're not sure how to replace the '*' with times, you might want to google it; its rather involved.

If your PHP was installed CGI, all you need to do is add the path to your php executable at the beginning of your script (must be the first line):
```
#!/usr/bin/php5 -q
```

Thats assuming you have PHP5 of course. I haven't used this method so can't say anything about its quarks.

---

### Post by satimis on 2006-12-13
Hi chrisfay,

This is a small World.

> Assuming your PHP was installed as an Apache module, to run PHP scripts via cron 

How to check it.

> 
you need to install the Lynx browser. Once this is installed, 

I have Lynx browser running on this server;

$ dpkg -l | grep lynx```

ii  lynx                                             2.8.5-2ubuntu1              Text-mode WWW Browser

```

> 
configure your crontab as follows:

```
* * * * * lynx -dump http://localhost/script.php
```

Whether you meant on Webmin?

> 
You can create a relative link instead of the absolute. 

Whether you meant sym-link?

> 
If you're not sure how to replace the '*' with times, you might want to google it; its rather involved.

Sorry I don't follow.  Pls explain in more detail.  Tks.

> 
Thats assuming you have PHP5 of course.
$ dpkg -l | grep php```

ii  libapache2-mod-php5                              5.1.2-1ubuntu3.4              server-side, HTML-embedded scripting languag
ii  php-pear                                         5.1.2-1ubuntu3.4              PEAR - PHP Extension and Application Reposit
ii  php5                                             5.1.2-1ubuntu3.4              server-side, HTML-embedded scripting languag
ii  php5-cli                                         5.1.2-1ubuntu3.4              command-line interpreter for the php5 script
ii  php5-common                                      5.1.2-1ubuntu3.4              Common files for packages built from the php
ii  php5-curl                                        5.1.2-1ubuntu3.4              CURL module for php5
ii  php5-dev                                         5.1.2-1ubuntu3.4              Files for PHP5 module development
ii  php5-gd                                          5.1.2-1ubuntu3.4              GD module for php5
ii  php5-imap                                        5.1.2-1              IMAP module for php5
ii  php5-ldap                                        5.1.2-1ubuntu3.4              LDAP module for php5
ii  php5-mcrypt                                      5.1.2-1              MCrypt module for php5
ii  php5-mhash                                       5.1.2-1ubuntu3.4              MHASH module for php5
ii  php5-mysql                                       5.1.2-1ubuntu3.4              MySQL module for php5
ii  php5-mysqli                                      5.1.2-1ubuntu3.4              MySQL Improved module for php5
ii  php5-pspell                                      5.1.2-1              pspell module for php5
ii  php5-snmp                                        5.1.2-1ubuntu3.4              SNMP module for php5
ii  php5-sqlite                                      5.1.2-1ubuntu3.4              SQLite module for php5
ii  php5-xmlrpc                                      5.1.2-1ubuntu3.4              XML-RPC module for php5
ii  php5-xsl                                         5.1.2-1ubuntu3.4              XSL module for php5

```
php5 is running on this server.

Others noted with tks.

B.R.
satimis

---

### Post by chrisfay on 2006-12-14
> How to check it.

To check if you're PHP5 was installed as CGI or an Apache module you would create the file info.php somewhere on your web server and input this within that file:

```
<? phpinfo(); ?>
```

Save it and open up info.php in your web browser. It will output a bunch of info regarding your PHP settings. Look for Server API (fourth from the top), if it says CGI, its installed as CGI, if it says Apache, its installed as an Apache Module.


> Whether you meant on Webmin?

I meant in your 'crontab' you create for your cron job.  I'm not sure if Webmin allows you to create crontabs, or if it just does the scheduling for you. If the latter, you should be able to use the 'Create New Cron Job' within webmin and in the text box for what command to run, enter the link (relative or absolute) to the php script you want to schedule in the format:

```
lynx -dump http://localhost/script.php
```

So if you would rather make a 'relative' link to the php script in webmin and the file was located for example at /var/www/script.php, then you would enter the scheduled command in webmin as follows:

```
lynx -dump /var/www/script.php
```

If you prefer an absolute link instead, assuming you're web root directory is /var/www, the format would be:

```
lynx -dump http://localhost/script.php
```

```
Whether you meant sym-link?
```

I meant the link you specify in either your crontab or your Webmin scheduled cron job to your script.

```
Sorry I don't follow. Pls explain in more detail. Tks.
```

Again, if you're using webmin, it should have the option to schedule your cron job using the webmin interface. If not, then you need to learn how to do it manually. Scheduling a cron job is done by creating a crontab and specifying the time it runs at, along with the location of the file or command to be run in the format:

```
* * * * * command or file to be run
```

The asterisks should be changed according to your scheduling needs. Here are some examples from a brief tutorial found [here]("http://www.mkssoftware.com/docs/man1/crontab.1.asp").

0 0 * * *          -- midnight every day
0 0 * * 1-5        -- midnight every weekday
0 0 1,15 * *       -- midnight on 1st and 15th of month
0 0 1 * 5          -- midnight on 1st of month and every Friday

Like I said before, its somewhat confusing and takes a bit of testing to get it right. Although, if you're using webmin it may be a moot task.

Hope that helps a bit....

---

### Post by satimis on 2006-12-18
Hi chrisfay,

I don't need to run the script.php anymore because I'm now running "satimis.homelinux.com" as domain.  The said script is used to update dynamic IP address.

> 
To check if you're PHP5 was installed as CGI or an Apache module you would create the file info.php somewhere on your web server and input this within that file:

```
<? phpinfo(); ?>
```

Save it and open up info.php in your web browser. It will output a bunch of info regarding your PHP settings. Look for Server API (fourth from the top), if it says CGI, its installed as CGI, if it says Apache, its installed as an Apache Module.


$ nano /home/satimis/info.php
copied "<? phpinfo(); ?>" on it.

Started Firefox and ran /home/satimis/info.php

It asked whether I need to open the file with Text Editor?

Did I make something wrong?  Tks

Others noted with tks.


B.R.
satimis

---


---
title: "Php"
date: 2016-04-18
forum: Server Platforms
---

### Post by m_ghv_geo on 2016-04-18
1st Hello all.
2nd What am I asking
I installed php with this commands

```

[COLOR=#333333]sudo apt-get install php5-common libapache2-mod-php5 php5-cli
 It installed

[/COLOR]miky@media:/var/www/html$ /etc/init.d/apache2 stop
[ ok ] Stopping apache2 (via systemctl): apache2.service.


miky@media:/var/www/html$ sudo /etc/init.d/apache2 start
[sudo] password for miky: 
[ ok ] Starting apache2 (via systemctl): apache2.service.

miky@media:/var/www/html$ php -v
PHP 5.6.4-4ubuntu6.4 (cli) (built: Oct 28 2015 01:21:29) 
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2014 Zend Technologies
    with Zend OPcache v7.0.4-dev, Copyright (c) 1999-2014, by Zend Technologies







```

I created /var/www/html/phpinfo.php
```
miky@media:/var/www/html$ ls -ltotal 28
-rwxr-xr-x 1 root root 1692 Apr 17 16:12 about.html
-rwxr-xr-x 1 root root 3082 Apr 17 16:12 cont.html
drwxr-xr-x 2 root root 4096 Apr 16 13:35 css
drwxr-xr-x 3 root root 4096 Apr 16 03:46 images
-rwxr-xr-x 1 root root 1732 Apr 17 16:12 index.html
-rwxr-xr-x 1 root root   17 Apr 17 21:38 phpinfo.php
-rwxr-xr-x 1 root root 2971 Apr 17 16:12 serv.html
miky@media:/var/www/html$ cat phpinfo.php
<?
phpinfo();
?>
miky@media:/var/www/html$ 

```

As I was told that phpinfo.php should show me info about php in system if it is working correctly.
but on server's web browser i am typing 127.0.0.1/phpinfo.php page is completely blank.
I guessed something is not right I started digging and found this [http://ubuntuforums.org/showthread.php?t=2220317](http://ubuntuforums.org/showthread.php?t=2220317)

his solution was this.
[COLOR=#000000]aahmad@ubuntu-desktop:~$ cat /etc/apache2/sites-enabled/* | grep 'var/www'[/COLOR]
[COLOR=#000000]DocumentRoot /[/COLOR][B]var/www/html
[/B]
 I copied it and blindly pasted in terminal it executed as two separate commands

Know i do not know what I have messed up.







3rd extra info. i am completely noob when it comes to web services and programming.[INDENT]I just created my 1st webpage ict.br.com(It is not done yet, actually far form it. but at least it is better than nothing right?)
I used HTML and CSS for this web page. I wanted to use little bit  of database i Found out I need PHP for that.[/INDENT]

---

### Post by Graham_Willis on 2016-04-18
The commands that you issued should not mess anything. The first one is totally unharmful (it just searches for lines matching [COLOR=#000000]var/www in all the files in [COLOR=#000000]/etc/apache2/sites-enabled/* and displays them on the screen) and the second doesn't even exist in the system (so it simply did nothing). But the question is, why you can't load the webpage. Could you for start check what will be the result of opening 127.0.0.1/index.html in the server's browser?[/COLOR][/COLOR] It will reveal if the problem concerns only PHP files or if there is a deeper problem with returning the contents of HTML files, too. Also, could you please paste the output of the command:

```
cat /etc/apache2/sites-enabled/* | grep 'var/www'
```

It will tell you where the files of your page (such as index.html, index.php) should be placed.

---

### Post by m_ghv_geo on 2016-04-19
> **Graham_Willis said:**
> The commands that you issued should not mess anything. The first one is totally unharmful (it just searches for lines matching [COLOR=#000000]var/www in all the files in [COLOR=#000000]/etc/apache2/sites-enabled/* and displays them on the screen) and the second doesn't even exist in the system (so it simply did nothing). But the question is, why you can't load the webpage. Could you for start check what will be the result of opening 127.0.0.1/index.html in the server's browser?[/COLOR][/COLOR] It will reveal if the problem concerns only PHP files or if there is a deeper problem with returning the contents of HTML files, too. Also, could you please paste the output of the command:

```
cat /etc/apache2/sites-enabled/* | grep 'var/www'
```

It will tell you where the files of your page (such as index.html, index.php) should be placed.




Considering I was the one who made  index.hml and it's css files they work perfectly.
You may check them out ict.br.com .

I run that code
and this output
```

miky@media:~$ cat /etc/apache2/sites-enabled/* | grep 'var/www'    
               DocumentRoot /var/www/html
miky@media:~$ 

```

And yes .php file is located in /var/www/html/
```

miky@media:/var/www/html$ ls -l
total 28
-rwxr-xr-x 1 root root 1692 Apr 17 16:12 about.html
-rwxr-xr-x 1 root root 3082 Apr 17 16:12 cont.html
drwxr-xr-x 2 root root 4096 Apr 16 13:35 css
drwxr-xr-x 3 root root 4096 Apr 16 03:46 images
-rwxr-xr-x 1 root root 1732 Apr 17 16:12 index.html
**-rwxr-xr-x 1 root root   17 Apr 17 21:38 phpinfo.php**
-rwxr-xr-x 1 root root 2971 Apr 17 16:12 serv.html
miky@media:/var/www/html$ 

```

---

### Post by SeijiSensei on 2016-04-19
To use only "<?" in PHP scripts you must have "short_open_tag" enabled in /etc/php5/apache2/php.ini.  It is disabled by default.  Try rewriting your script as
```
<?php phpinfo() ?>
```
Any better?

If you want to use short tags, set that directive to "On" in php.ini and restart Apache.

---

### Post by m_ghv_geo on 2016-04-19
> **SeijiSensei said:**
> To use only "<?" in PHP scripts you must have "short_open_tag" enabled in /etc/php5/apache2/php.ini.  It is disabled by default.  Try rewriting your script as
```
<?php phpinfo() ?>
```
Any better?

If you want to use short tags, set that directive to "On" in php.ini and restart Apache.


Thank you 
After I changed it to 
```

miky@media:/var/www/html$ cat phpinfo.php
<?php phpinfo(); ?>
miky@media:/var/www/html$

```

It works

---


---
title: "PHP not executing"
date: 2016-07-05
forum: Server Platforms
---

### Post by wadie on 2016-07-05
Hi,

I'm running Ubuntu 14.04 with Apache2 and PHP7.

For some reason,probably after I updated the PHP version,it is no longer executing.
This is the output of ```
php -v
```

> PHP 7.0.8-3+deb.sury.org~trusty+1 (cli) ( NTS )
Copyright (c) 1997-2016 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies
    with Zend OPcache v7.0.8-3+deb.sury.org~trusty+1, Copyright (c) 1999-2016, by Zend Technologies

The root folder is > /var/www/html

Any ideas ?
I appreciate it! :)

---

### Post by T.J. on 2016-07-05
> **wadie said:**
> Hi,

I'm running Ubuntu 14.04 with Apache2 and PHP7.

For some reason,probably after I updated the PHP version,it is no longer executing.
This is the output of ```
php -v
```



I'm afraid that is not enough information to help you.  Could you please post an example of code that is not working?  It doesn't have to be extensive, just something to demonstrate what is wrong so I can help you.

---

### Post by wadie on 2016-07-05
Even if I try to execute something as simple as echo function or phpinfo(); it gets returned as plain text when loading index.php for example

---

### Post by T.J. on 2016-07-05
> **wadie said:**
> Even if I try to execute something as simple as echo function or phpinfo(); it gets returned as plain text when loading index.php for example

Sounds like your server is not configured to recognize PHP files as scripts.  Make sure your web server configuration has the handlers enabled:

AddType  application/x-httpd-php         .php
AddType  application/x-httpd-php-source  .phps

---

### Post by SeijiSensei on 2016-07-05
With a standard Apache/PHP installation, the dependent package libapache2-mod-php5 installs the handlers T.J. mentions above.  If you didn't install PHP from the repositories, you'll have to add these handlers yourself.  The key file in that package is /etc/apache2/mods-available/php5.conf:
```

$ more /etc/apache2/mods-available/php5.conf
<FilesMatch ".+\.ph(p[345]?|t|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>
<FilesMatch ".+\.phps$">
    SetHandler application/x-httpd-php-source
    # Deny access to raw php sources by default
    # To re-enable it's recommended to enable access to the files
    # only in specific virtual host or directory
    Order Deny,Allow
    Deny from all
</FilesMatch>
# Deny access to files without filename (e.g. '.php')
<FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
    Order Deny,Allow
    Deny from all
</FilesMatch>

# Running PHP scripts in user directories is disabled by default
# 
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>

```

---

### Post by wadie on 2016-07-05
> **T.J. said:**
> Sounds like your server is not configured to  recognize PHP files as scripts.  Make sure your web server configuration  has the handlers enabled:

AddType  application/x-httpd-php         .php
AddType  application/x-httpd-php-source  .phps



For some reason when I load PHP files Firefox pop-ups a window for me to download it :/

---

### Post by T.J. on 2016-07-05
> **wadie said:**
> For some reason when I load PHP files Firefox pop-ups a window for me to download it :/

I'd definitely verify the handlers are working and enabled for whatever directory you are storing the scripts in.  The location matters.

---

### Post by wadie on 2016-07-05
Fixed by running the following commands:

> sudo apt-get install libapache2-mod-php7.0
sudo a2dismod php*
sudo a2enmod php7.0
sudo apache2ctl restart

---

### Post by pdk-knight on 2017-05-11
Having the same problem....
If you look at ph7.conf (I have 7.1) 
<FilesMatch "^\.ph(p[3457]?|t|tml|ps)$">
you have to append .php7 to the file name. I did this and the browser no longer goes out to google.
However still get a blank page.
I have ubuntu 14.04 , latest version of apache2 an php7.1
All indications are that everything is installed correctly.
I cannot see any need except for the files match to change anything else
apache2ctl -M shows php module loaded (shared)
php -a allows me to execute phpinfo() in the shell. however if I type php7 -f test_php.php I just get a list of the lines in the file. Maybe this provides another clue.
Blank pages in apache2 ......... 
any one able to add something.
Peter

---

### Post by wildmanne39 on 2017-05-11
@pdk-knight, please start your own thread so you can get the help you need, it is not likely you will get help in this old solved thread.
Thanks

---


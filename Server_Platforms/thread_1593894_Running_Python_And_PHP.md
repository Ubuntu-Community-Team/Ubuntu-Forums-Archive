---
title: "Running Python And PHP"
date: 2010-10-11
forum: Server Platforms
---

### Post by abou maryam on 2010-10-11
Hello,

i'm a Web Developper, i'm using apache2 and php5 and mysql on my laptop, i want to try the Django (Framework based on Python Language), so for this i have installed python-mysql...

after this i can't access my localhost and can't open sites that i'm working on

so any one can help me?

note: for installing the python-mysql i have followed those steps: h[ttp://bryanhelmig.com/setting-up-ubuntu-10-04-with-apache-memcached-ufw-mysql-and-django-1-2-on-linode/]("http://bryanhelmig.com/setting-up-ubuntu-10-04-with-apache-memcached-ufw-mysql-and-django-1-2-on-linode/")

---

### Post by Barriehie on 2010-10-11
So what do the apache log files show???

---

### Post by abou maryam on 2010-10-11
thankx Barriehie for ur reply,

i've attache a copy of the file: /var/log/apache2/error.log

---

### Post by Barriehie on 2010-10-11
Did you even look at the logfile???

You've got missing files, .htaccess issues, and invalid commands.  I'ld start with the missing files, then the .htaccess issue/command.  Also, are you stopping/restarting apache??? it seems to get terminated frequently.

---

### Post by abou maryam on 2010-10-11
> **Barriehie said:**
> Did you even look at the logfile???

You've got missing files, .htaccess issues, and invalid commands.  I'ld start with the missing files, then the .htaccess issue/command.  Also, are you stopping/restarting apache??? it seems to get terminated frequently.
Yes i have checked the apache log, but i don't know how to fix the problem, All Sites was wroking great before installing python-mysql

all files are in their places and also the .htacces has no problem, it's the same, site was working with the same .htaccess before installing python-mysql
this is a copy of the .htaccess files
```
<FilesMatch "\.(engine|inc|info|install|make|module|profile|test|po|sh|.*sql|theme|tpl(\.php)?|xtmpl|svn-base)$|^(code-style\.pl|Entries.*|Repository|Root|Tag|Template|all-wcprops|entries|format)$">
  Order allow,deny
</FilesMatch>

# Don't show directory listings for URLs which map to a directory.
Options -Indexes

# Follow symbolic links in this directory.
Options +FollowSymLinks

# Handle any 404 errors.
ErrorDocument 404 /index.php

# Force simple error message for requests for non-existent favicon.ico.
<Files favicon.ico>
  # There is no end quote below, for compatibility with Apache 1.3.
  ErrorDocument 404 "The requested file favicon.ico was not found.
</Files>

# Set the default handler.
DirectoryIndex index.php

# Override PHP settings. More in sites/default/settings.php
# but the following cannot be changed at runtime.

# PHP 4, Apache 1.
<IfModule mod_php4.c>
  php_value magic_quotes_gpc                0
  php_value register_globals                0
  php_value session.auto_start              0
  php_value mbstring.http_input             pass
  php_value mbstring.http_output            pass
  php_value mbstring.encoding_translation   0
</IfModule>

# PHP 4, Apache 2.
<IfModule sapi_apache2.c>
  php_value magic_quotes_gpc                0
  php_value register_globals                0
  php_value session.auto_start              0
  php_value mbstring.http_input             pass
  php_value mbstring.http_output            pass
  php_value mbstring.encoding_translation   0
</IfModule>

# PHP 5, Apache 1 and 2.
<IfModule mod_php5.c>
  php_value magic_quotes_gpc                0
  php_value register_globals                0
  php_value session.auto_start              0
  php_value mbstring.http_input             pass
  php_value mbstring.http_output            pass
  php_value mbstring.encoding_translation   0
</IfModule>

# Requires mod_expires to be enabled.
<IfModule mod_expires.c>
  # Enable expirations.
  ExpiresActive On

  # Cache all files for 2 weeks after access (A).
  ExpiresDefault A1209600

  <FilesMatch \.php$>
    # Do not allow PHP scripts to be cached unless they explicitly send cache
    # headers themselves. Otherwise all scripts would have to overwrite the
    # headers set by mod_expires if they want another caching behavior. This may
    # fail if an error occurs early in the bootstrap process, and it may cause
    ExpiresActive Off
  </FilesMatch>
</IfModule>

# Various rewrite rules.
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_URI} !=/favicon.ico
  RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]
</IfModule>
php_value upload_max_filesize 10000M
php_value post_max_size 10000M
```

---

### Post by Barriehie on 2010-10-11
Okay, let's isolate it.  If you purge python-mysqldb do you get your sites back?

Barrie

Edit:  Looks like something is trying to access a LOT of windows type files.

---

### Post by abou maryam on 2010-10-11
i've reisntalled php 5 and mysql and apache2

sites works great now, but Python sites are not working :)

---

### Post by Barriehie on 2010-10-11
> **abou maryam said:**
> i've reisntalled php 5 and mysql and apache2

sites works great now, but Python sites are not working :)

Cool, maybe make a backup...  My stuff is pretty much php so can't help with the .py stuff.  Glad you got it working.

This might help: [https://help.ubuntu.com/community/Django](https://help.ubuntu.com/community/Django)

---


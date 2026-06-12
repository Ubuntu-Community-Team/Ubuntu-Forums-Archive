---
title: "Apache2 .htaccess won't work =("
date: 2010-02-08
forum: Server Platforms
---

### Post by toshiba23 on 2010-02-08
Hey Guys,

I'm a newb when it comes to linux operating systems so I'm attempting to get better through experience.

I work for a web development company and we use Ubuntu for our operating systems (the programmers at least).

Anyways, I'm trying to install LAMP services and get them working.

I have all L.A.M.P. services installed... but Apache2 is giving me a problem.

I have an .htaccess file installed in a directory under my document root. But Apache2 is not interpretting it.

I have AllowOverride All on but I can't figure it out....

Btw: I did make a bogus .htaccess file attempting to make apache give me a error... nothing.

---

### Post by Sef on 2010-02-09
Moved to server platforms.

---

### Post by HorseBox on 2010-12-17
I'm using Ubuntu 11.04 and I was having this problem earlier but heres how I got .htaccess files working. 

**sudo gedit /etc/apache2/sites-available/default**

Heres what was in the file
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        **AllowOverride None**
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

I changed **AllowOverride None **to **AllowOverride All **then restarted apache2 and now it reads the .htacess files.

---


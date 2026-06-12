---
title: "VirtualHost only seeing one site"
date: 2009-12-02
forum: Server Platforms
---

### Post by kwickcut on 2009-12-02
Hello all i am having a small problem with my v host.. it seems no matter what url i use it takes you to the first directory...


siteone.com and sitetwo.com both take you to siteone directory...


this is the default v host
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
        AllowOverride None
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

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
DirectoryIndex index.html index.htm index.php

</VirtualHost>

```first v host i added

```
<VirtualHost 192.168.1.150>
DocumentRoot "/var/www/siteone"
ServerName siteone.com
<Directory "/var/www/siteone">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```second vhost i added


```
<VirtualHost 192.168.1.150>
DocumentRoot "/var/www/sitetwo"
ServerName sitetwo.com
<Directory "/var/www/sitetwo">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```now i ran this code

```
 grep -i -e virtualhost -e ServerName -e documentroot /etc/apache2/sites-enabled/*

```
this is the output


```
/etc/apache2/sites-enabled/*
/etc/apache2/sites-enabled/000-default:<VirtualHost *:80>
/etc/apache2/sites-enabled/000-default: DocumentRoot /var/www
/etc/apache2/sites-enabled/000-default:</VirtualHost>
/etc/apache2/sites-enabled/example1.com.conf:<VirtualHost 192.168.1.150>
/etc/apache2/sites-enabled/example1.com.conf:DocumentRoot "/var/www/siteone"
/etc/apache2/sites-enabled/example1.com.conf:ServerName siteone.com
/etc/apache2/sites-enabled/example1.com.conf:</VirtualHost>
/etc/apache2/sites-enabled/sitetwo.com.conf:<VirtualHost 192.168.1.150>
/etc/apache2/sites-enabled/sitetwo.com.conf:DocumentRoot "/var/www/sitetwo"
/etc/apache2/sites-enabled/sitetwo.com.conf:ServerName sitetwo.com
/etc/apache2/sites-enabled/sitetwo.com.conf:</VirtualHost>
```
now i have 2 other questions in the vhost files i made should i have 
<VirtualHost 192.168.1.150> 
or should it be  
<VirtualHost 192.168.1.150:80>

=================================


second question

under Create a New Virtual Server

in the field

Server Name


should this be the name of the server example1.com

should it be the name of the site i am going to host siteone.com

or should it just be set to default 


thanks for any help



kwick

---

### Post by Vegan on 2009-12-02
Go to my site, forum, in the LAMP area on Apache which as a quick start.

---

### Post by kwickcut on 2009-12-02
thanks for the help i think i got it maybe lol




kwick

---


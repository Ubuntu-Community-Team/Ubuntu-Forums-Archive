---
title: "Apache2 subdomain configuration"
date: 2012-11-25
forum: Server Platforms
---

### Post by PinkFloyd102489 on 2012-11-25
Apologies if this is in the wrong section.

I'm attempting to set up a subdomain but the sub keeps redirecting back to my main site.

Here are the two files I've edited (in addition to enabling the default site) and I've also added a CNAME for the subdomain pointing to the server IP.

/etc/apache2/httpd.conf:
```
<Directory /var/www/admin>
AllowOverride AuthConfig
</Directory>

<Directory /var/www/ogame/output/>
AllowOverride AuthConfig
</Directory>

<Directory /var/www/phpvbox/>
AllowOverride AuthConfig
</Directory>

AccessFileName .htaccess


DirectoryIndex index.html index.php

NameVirtualHost *

<VirtualHost *>
  ServerName www.nomegahurts.com
  DocumentRoot /var/www/
</VirtualHost>

<VirtualHost *>
  ServerName derick.nomegahurts.com
  ServerAlias derick.*
  DocumentRoot /var/www/derick/
</VirtualHost>
```


/etc/apache2/sites-available/default:

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


<VirtualHost *>
        DocumentRoot "/var/www/derick/"
        ServerName derick.nomegahurts.com
        ServerAdmin contact@nomegahurts.com
        ErrorLog /var/log/apache2/nomegahurts.log

        <Directory /var/www/derick/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>
```

---

### Post by pkadeel on 2012-11-25
First of all never define your virtual hosts in your httpd.conf or inside the "default" site
remove all those definitions from those files.

In current version each virtual host is defined in its own separate file and placed inside sites-available folder then you can enable that virtual host by using the a2ensite command in terminal
```
sudo a2ensite filename
```now your actual problem, following is what I will do in this case

file name "nomegahurts" placed in sites-available folder.
```

<VirtualHost *:80>
    ServerName nomegahurts.com
    ServerAlias www.nomegahurts.com
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
       DirectoryIndex index.php index.html
</VirtualHost>

<VirtualHost *:80>
    ServerName derick.nomegahurts.com
    DocumentRoot /var/www/derick
    <Directory /var/www/derick/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Order Deny,Allow
        Allow from all
    </Directory>
</VirtualHost>

```

Appropriate "A" name for "nomegahurts.com" and "CNAME" for "www.nomegahurts.com" and "derick.nomegahurts.com" need to be set

If you want to be able to keep the derick.nomegahurts.com running even if you disable the main site then you will have to put the definition for derick.nomegahurts.com in a separate file in sites-available folder and again enable it by a2ensite command.

---

### Post by PinkFloyd102489 on 2012-11-25
I changed the name of the alternate sites-available file to "a" and everything is loading properly. I had read somewhere about Apache loading the default and then ignoring everything else.

My site isn't anywhere near high traffic, so this works for me. Thanks. :)

---

### Post by SeijiSensei on 2012-11-25
I recommend reading the [Ubuntu Server Guide](https://help.ubuntu.com/12.04/serverguide/httpd.html) where the method that Ubuntu uses to handle virtual hosts is described in detail.  I also wrote a brief overview [here](http://ubuntuforums.org/showpost.php?p=11922324&postcount=2).

---


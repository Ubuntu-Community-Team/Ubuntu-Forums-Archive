---
title: "Bind Apache2 to localhost on port 420"
date: 2011-11-09
forum: Server Platforms
---

### Post by ki4jgt on 2011-11-09
Here's what I've done. It doesn't seem to be working. I've restarted Apache and everything and nothing seems to work.

```
<VirtualHost [I put the URL here]:420>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/jesse/Desktop/site/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/jesse/Desktop/site/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order deny,allow
        allow from 127.0.0.1
        deny from all
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

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost [URL here]:420
Listen 127.0.0.1:420

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```

Have any suggestions?

---


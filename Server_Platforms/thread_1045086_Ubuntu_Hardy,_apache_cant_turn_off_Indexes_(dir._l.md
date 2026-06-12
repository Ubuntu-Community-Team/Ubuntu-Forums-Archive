---
title: "Ubuntu Hardy, apache cant turn off Indexes (dir. listings)"
date: 2009-01-20
forum: Server Platforms
---

### Post by cyberek_b on 2009-01-20
Hi.

I have configuration with some virtual hosts.

Virtual hosts basedir is "/var/www/sitename/htdocs"
OOTB directory listings was turn on for all, so i have edited:
/var/etc/apache2/sites-available/default:
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options -Indexes FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
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
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options -Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>


</VirtualHost>


```
and reloaded apache (also tried to full stop and start)
I wanted to force /var/www to disable indexes... but it failed.

Only thing that worked, was adding:
```
<Directory /var/www/>
Options -Indexes
</Directory>
```
in every virtualhost config (/etc/apache2/sites-available/sitename) and reloading apache.

Is there any possible way to disable catalog listings for whole apache?

---


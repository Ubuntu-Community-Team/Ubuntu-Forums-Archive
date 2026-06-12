---
title: "mod rewrite &amp; permalinks"
date: 2013-04-12
forum: Server Platforms
---

### Post by AvengerX9 on 2013-04-12
I seem to have some problems with the permalinks on my website. I enabled mod_rewrite and restarted apache, but still they are failing when I access them.

I think apache is ignoring my htaccess files so I tried doing like here [http://ubuntuforums.org/showthread.php?t=1506129&highlight=mod_rewrite](http://ubuntuforums.org/showthread.php?t=1506129&highlight=mod_rewrite)

Changing to *Allow Override All* but there is no help in that here.

This is my Virtualhost file

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
                AllowOverride All
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
Thanks for reading!

Roger

---

### Post by AvengerX9 on 2013-04-12
Sorry my fault here. I forgot to change both lines in the /var/www blocks with Allow Override All and I didnt restart Apache after the 2nd attempt. Works now!! :) but please comment the virtualhost if you feel like. I'm here to learn :)

---


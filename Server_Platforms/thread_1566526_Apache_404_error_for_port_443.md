---
title: "Apache 404 error for port 443?"
date: 2010-09-02
forum: Server Platforms
---

### Post by thegaffney on 2010-09-02
Hey, so i noticed in my logs today, that someone was trying to get the phpMyAdmin on my website (phpMyAdmin is not on my server BTW) so i tried going to that myself and got the plain 404 error even though i have a custom 404 error setup, but it seems to only work for pages not directories, if i put .php or .htm after the phpmyadmin i get my custom error

Is there something different i need to do to display that for missing directories also?



EDIT

Actually i see the problem it only works if i get rid of the https and just use http

what do i need to do them to catch it on port 443?
Do i need to change or add another virtual host for it?

right now midfifty.com is the default site in apace, and my default site looks like this

```

<VirtualHost *:80>
        ServerAdmin mike@midfifty.com

        DocumentRoot /www/midfifty
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /www/midfifty/>
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
        ErrorDocument 403 /noallow.php
        ErrorDocument 404 /notfound.php
        ErrorLog /var/log/apache2/web.log

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

</VirtualHost>

```

---

### Post by deoren on 2010-09-02
There may be a better way to do this, but I would have inside of that same *.conf file a portion for *:443 like so:

```
<VirtualHost *:80>
        ServerAdmin mike@midfifty.com
...
        DocumentRoot /www/midfifty
...
        ErrorDocument 403 /noallow.php
        ErrorDocument 404 /notfound.php
        ErrorLog /var/log/apache2/web.log
</VirtualHost>

<VirtualHost *:443>
        ServerAdmin mike@midfifty.com
...
        DocumentRoot /www/midfifty
...
        ErrorDocument 403 /noallow.php
        ErrorDocument 404 /notfound.php
        ErrorLog /var/log/apache2/web-https.log
</VirtualHost>
```

If you have many vhosts you may want to not specify the log files in the separate vhosts and use a combined log file (to split out later as a cron job).

---

### Post by thegaffney on 2010-09-03
Ah ok ill give it a try, thanks :)

And we just have 2 sites that we log, the internal site which is a complicated web app, and then our public website, I split them up so that all the 404 errors from people trying to search engine cached pages on our old site, dont get mixed in to the errors for the web app, which is still in production so i check that log every few hours or so to weed out any small bugs.

Seems to work for now, ill probably put it all back to the error.log when all the debugging is done

---


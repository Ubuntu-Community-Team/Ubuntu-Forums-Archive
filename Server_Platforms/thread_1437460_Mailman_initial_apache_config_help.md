---
title: "Mailman initial apache config help"
date: 2010-03-23
forum: Server Platforms
---

### Post by neuronotic on 2010-03-23
Hi, I've installed mailman on 9.10, using apt-get, have apache2 setup already. However I'm getting 403 forbidden issues when trying to access [http://XXX/cgi-bin/mailman](http://XXX/cgi-bin/mailman)

I may have mucked something up as initially i jumped straight in and created a virtualhost and played around with the URL redirects. but as far as I can see, it's back to its default and it's still not working...

Help appreciated!!

When I try to access the page, in my apache error.log, i get this:
> [Wed Mar 24 02:36:37 2010] [error] [client 192.168.1.1] attempt to invoke directory as script: /usr/lib/cgi-bin/mailman/I've tried check_perms, it does give this error:
> root@babel:/etc/apache2# check_perms 
/var/lib/mailman/templates bad group (has: root, expected list)
/var/lib/mailman/bin bad group (has: root, expected list)
/var/lib/mailman/cgi-bin bad group (has: root, expected list)
/var/lib/mailman/Mailman bad group (has: root, expected list)
/var/lib/mailman/scripts bad group (has: root, expected list)
/var/lib/mailman/mail bad group (has: root, expected list)
/var/lib/mailman/cron bad group (has: root, expected list)
/var/lib/mailman/logs bad group (has: root, expected list)
/var/lib/mailman/locks bad group (has: root, expected list)
/var/lib/mailman/icons bad group (has: root, expected list)
Problems found: 10
Here's my default apache config file:
> <VirtualHost *:80>
        ServerAdmin webmaster@XXX
        ServerName XXX:80
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
</VirtualHost>
and my mailman apache config file (sym-linked to the apache sites-enabled directory)

> 
ScriptAlias /cgi-bin/mailman/ /usr/lib/cgi-bin/mailman/
Alias /pipermail/ /var/lib/mailman/archives/public/
Alias /images/mailman/ /usr/share/images/mailman/


<Directory /usr/lib/cgi-bin/mailman/>
    AllowOverride None
    Options ExecCGI
    AddHandler cgi-script .cgi
    Order allow,deny
    Allow from all
</Directory>
<Directory /var/lib/mailman/archives/public/>
    Options Indexes FollowSymlinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
<Directory /usr/share/images/mailman/>
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
thanks again!

---

### Post by Vishal Agarwal on 2010-12-02
Any Updates ?

---


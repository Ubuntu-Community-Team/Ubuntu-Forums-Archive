---
title: "Apache 2 rewrite rule"
date: 2010-07-16
forum: Server Platforms
---

### Post by CryptiniteDemon on 2010-07-16
So I've been playing around with rewrite rules and I cannot get it to work for what I'm trying to do.

I want it so that when someone goes to [http://www.mydomain.com/HWM/](http://www.mydomain.com/HWM/) it redirects it to /cgi-bin/HWM/somefile.cgi

Here's the config for my virtual host:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
                RewriteRule ^/HWM/$ /usr/lib/cgi-bin/HWM/somefile.cgi
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
        ServerSignature On

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

### Post by cdenley on 2010-07-16
Did you enable the rewrite module and restart apache?
```

sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart

```

Also, by default, "RewriteEngine" is set to "off". I think it should work, but why use RewriteRule in the directory context?
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        RewriteEngine On
        RewriteRule ^/HWM/$ /usr/lib/cgi-bin/HWM/somefile.cgi
        DocumentRoot /var/www/
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
        ServerSignature On

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

### Post by CryptiniteDemon on 2010-07-16
Dunno how I forgot the rewriteEngine on command.  I had it in there before, I thought.

Thanks for your help.

---


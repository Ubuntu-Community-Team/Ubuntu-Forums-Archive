---
title: "Basic apache config with virthosts"
date: 2010-06-25
forum: Server Platforms
---

### Post by linorics on 2010-06-25
I've trying to look this up for two days now and got nothing. This is what i have.

[http://site.com](http://site.com)
[https://sub.site.com](https://sub.site.com)

They work okay but i have an issue. If i type in [http://sub.site.com](http://sub.site.com) it goes to [http://site.com](http://site.com) and if i type in [https://site.com](https://site.com) it goes to [https://sub.site.com](https://sub.site.com) page.

# /etc/apache2/sites-available/default
```

<VirtualHost *:80>
        #ServerAdmin webmaster@localhost

        DocumentRoot /var/www/site
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /var/www/site>
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


```

# /etc/apache2/sites-available/ssl
```

<VirtualHost *:443>
        ServerName sub.site.com
        DocumentRoot /var/www/sub

        SSLEngine on
        SSLOptions +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>

```

I'm guessing it has to do with the *:80 and *.443 but I don't know how to change it so it only listens to one web address. Does anyone know what I need to change?

---


---
title: "Apache2 403 Forbidden"
date: 2011-12-02
forum: Server Platforms
---

### Post by Thomas_Matthew on 2011-12-02
Hello, today I decided to start rebuild my Web Server and I installed a fresh copy of Ubuntu 10.04 and Apache2 onto it. I wanted the DocumentRoot to be on my second (slave) drive so I went into the file called "default" in the sites-available folder and set my document root to my second drive. I put a test index.html into the new document root and tried to load localhost up and it says > You don't have permission to access / on this server. I also have my default file here if that may be the problem. > <VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /media/Mercy-Data-Disk/www

        
    <Directory />
            Options FollowSymLinks
            AllowOverride None
        </Directory>
        <Directory /media/Mercy-Data-Disk/www>
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

Thanks! :)
[B]
[/B]

---

### Post by stmiller on 2011-12-03
```
sudo chown -R www-data /media/Mercy-Data-Disk/www
```

That should do it. But note that this is probably not a good idea. Apache's root and associated files should be in /var/www for security and other reasons.

---

### Post by CharlesA on 2011-12-04
> **stmiller said:**
> ```
sudo chown -R www-data /media/Mercy-Data-Disk/www
```

That should do it. But note that this is probably not a good idea. Apache's root and associated files should be in /var/www for security and other reasons.

Aye, that's a bad idea.

It would be a better idea to just make those files world readable. Are they on an NTFS drive?

---


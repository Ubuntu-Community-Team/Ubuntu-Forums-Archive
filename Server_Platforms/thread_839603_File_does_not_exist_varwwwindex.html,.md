---
title: "File does not exist: /var/wwwindex.html,"
date: 2008-06-24
forum: Server Platforms
---

### Post by zenoran on 2008-06-24
This is stumping the heck out of me and I can't seem to figure out what's going on...

the error log is showing this:

File does not exist: /var/wwwindex.html

That's when I try to directly reference "http://<site>/index.html"

I even tried restoring the default default.dpkg-dist virtual host configuration and still no luck.  With Indexing turned on I can view the directory structure in the /var/www directory but it basically just does the same thing any time I try to click on a folder or directory:

File does not exist: /var/wwwfiles
File does not exist: /var/wwwplugin

etc etc...

it isn't putting an extra / in there!  What is up with that?!
```
root@orion:/etc/apache2/sites-available# cat default
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

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

### Post by cariboo on 2008-06-24
It looks like you've got a / missing in your document root setting.

The file it is looking for is /var/www/index.html

Jim

---

### Post by zenoran on 2008-06-24
> **cariboo907 said:**
> It looks like you've got a / missing in your document root setting.

The file it is looking for is /var/www/index.html

Jim

Ya, I know what it SHOULD be look for .. but it isn't... document root is set appropriately as in the above config file...

---

### Post by cdenley on 2008-06-24
That is odd. Have you been changing the configuration? If so, have you restarted apache?
```

sudo /etc/init.d/apache2 restart

```

Just to make sure your modular configuration isn't messed up, you can post this output
```

ls -l /etc/apache2/sites-enabled
grep Include /etc/apache2/apache2.conf|grep -v \#

```

---


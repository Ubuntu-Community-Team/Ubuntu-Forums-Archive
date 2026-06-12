---
title: "Changing the web root in Apache2"
date: 2010-07-07
forum: Server Platforms
---

### Post by JohnElway on 2010-07-07
I've installed apache and php on my desktop and am trying to change the default web root of /var/www to /home/momen/www_momen. To do this I made a copy of the default virtual host in /etc/apache2/sites-available, renamed it to www_momen and modified the document root line so it looks like this:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/momen/www_momen
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
```Then I enabled the site: sudo a2ensite www_momen

and reloaded apache. However, if I try to access that web folder in a web browser I get a 404 error. Is there something wrong with my virtual host?

---

### Post by cdenley on 2010-07-07
> **JohnElway said:**
> Is there something wrong with my virtual host?

Nothing, except you never defined a ServerName. In what scenario do you expect your new vhost to be used rather than your default vhost? When your server is accessed using a hostname such as [www.mysite.com](www.mysite.com), apache looks for a virtual host matching that ServerName or ServerAlias starting with default, then alphabetically. If none match, which will be the case since you haven't defined any ServerName or ServerAlias, the default vhost will be served.

Either modify the default vhost with the correct DocumentRoot, or define a ServerName in your new vhost and access your site with that hostname.

---

### Post by JohnElway on 2010-07-07
Ok so I deleted the extra vhost and just modified the default to look exaclty like what I posted above. But when I try to navigate to the site my browser is giving me a 403 error.

---

### Post by cdenley on 2010-07-07
What are the permissions on the file you are attempting to access?

---

### Post by JohnElway on 2010-07-07
All the web files are in my home folder so I have read and write access to them.

---

### Post by cdenley on 2010-07-07
> **JohnElway said:**
> All the web files are in my home folder so I have read and write access to them.

That wasn't my question. Whether YOU have access to them is irrelevant. What matters is does apache have access to them?

---

### Post by JohnElway on 2010-07-07
I guess there were some kind of permission issues with the folders in the document root because when I remade the folders and dumped my files in them everything worked fine. It's weird because the original folders worked on another apache install and the only I did was transfer them to another computer on a flash drive. I guess that was enough to mess with the permissions. Thanks for the help.

---

### Post by cdenley on 2010-07-08
> **JohnElway said:**
> I guess there were some kind of permission issues with the folders in the document root because when I remade the folders and dumped my files in them everything worked fine. It's weird because the original folders worked on another apache install and the only I did was transfer them to another computer on a flash drive. I guess that was enough to mess with the permissions. Thanks for the help.

Flash drives typically use a filesystem which doesn't support Linux permissions, so transferring them via flash drive certainly could have lost any permissions you originally had on the files and directories.

---


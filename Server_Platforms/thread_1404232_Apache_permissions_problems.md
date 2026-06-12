---
title: "Apache permissions problems"
date: 2010-02-11
forum: Server Platforms
---

### Post by J V on 2010-02-11
I've had these problems before, but I can't find out how I fixed them...

I'm getting a 403 error when trying to browse the folder with my site in it...

I think the problem is in the sites-available file but I can't find it if it is...

Some terminal output:
```
drwxrwxr-x  2 j www-data 4096 2010-02-11 13:30 www
cd www
-rwxrwxr-x 1 j www-data 0 2010-02-11 12:46 index.html

cat /etc/apache2/sites-available/default 
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/j/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/j/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

</VirtualHost>

```Edit: added allowoverride and removed all but follow symlinks from options

---


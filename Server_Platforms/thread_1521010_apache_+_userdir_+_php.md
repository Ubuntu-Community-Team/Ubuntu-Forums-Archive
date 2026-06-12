---
title: "apache + userdir + php"
date: 2010-06-30
forum: Server Platforms
---

### Post by its_me_gb on 2010-06-30
i am having an issue with getting php to run under my public_html in my user account.

i have been running apache with php which has been running fine from the web root (/var/www), as i am currently using ampache which is all php.

however i decided recently to enable userdir only for myself. however when i try to open the index.php, my browser attempts to download the file rather than display it.

This is my userdir.conf
```

<IfModule mod_userdir.c>
UserDir disabled
UserDir enabled george
UserDir "public_html"
</IfModule>

```

and in my default site:
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
    Alias /tf/ "/opt/torrentflux/html/"
    <Location "/opt/torrentflux/html/">
        Options Indexes FollowSymLinks MultiViews
        Order allow,deny
        Allow from all
    </Location>
UserDir disabled
UserDir enabled george
UserDir "public_html"
AccessFileName .htaccess
</VirtualHost>

```

as i said earlier, php is working on the default site, when served from /var/www but not from my user dir.

have i done something glaringly wrong? or am i missing something essential? if you need to see any more config files, please let me know!

cheers,

gb

---

### Post by patjenk on 2010-06-30
I am using 10.4 server and recently ran into this problem.

In /etc/apache2/mods-enabled/php5.conf check to see if PHP is explicitly turned off in user directories. The configuration will look like this:

    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>

Commenting this out and restarting the apache server fixed the problem for me.

---

### Post by its_me_gb on 2010-06-30
Excellent! this worked!

thanks for your help!

gb

---

### Post by erop on 2010-08-14
> **patjenk said:**
> I am using 10.4 server and recently ran into this problem.

In /etc/apache2/mods-enabled/php5.conf check to see if PHP is explicitly turned off in user directories. The configuration will look like this:



Unfortunately this didn't work for me. I have a clean install of Lucid server as VirtualBox guest on Lucid host.
mod_userdir enabled. php5.conf snippet commented as written above (my php5.conf even has similar recommendation in itself as comment above <IfModule mod_userdir.c> section). 
Plain HTML files accessed perfectly from my /home/username/public_html directory. But when accessing PHP files my Firefox tries to download it and not to execute script. Any other suggestion how to fix issue?

---

### Post by erop on 2010-08-14
One should clean browser cache after modifying php5.conf I noticed this in another post [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1478721](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1478721) and everything works fine at the moment.

---


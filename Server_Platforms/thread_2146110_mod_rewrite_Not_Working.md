---
title: "mod_rewrite Not Working"
date: 2013-05-17
forum: Server Platforms
---

### Post by jonedney on 2013-05-17
I've been troubleshooting over the last couple of days on my Ubuntu Server 12.04 installation, why mod_rewrite is not working properly.  I'm at a dead end, and wanted to post to see if I could get over this rock wall.

mod_rewrite is enabled
```
Module rewrite already enabled
```

I've added AllowOverride options in the sites-available
```
<Directory /home/.../sites/.../public_html/blog/>                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```

.htaccess has mod_rewrite rules
```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>


# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /blog/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /blog/index.php [L]
</IfModule>

Anyone see anything out of the normal?



```

---

### Post by linuxtechguy on 2013-05-17
You cant have allowoverride none and expect .htaccess to work.

---

### Post by chrisguk on 2013-05-18
> **linuxtechguy said:**
> You cant have allowoverride none and expect .htaccess to work.

What he said.  Your declaration for the directory is wrong.  I am assuming you pulled that from something default.  Something else I noticed.  you have two declarations of Rewritebase in the same file but for different levels.  .htaccess is a directory level function for example the .htaccess stuff for wordpress sits in /blog/ only and if the other rewrite rule above it is for your website pages then that should be in the root directory (/var/www or /public_html/).

---

### Post by jonedney on 2013-05-21
Thanks guys.

What I pasted was a local copy, what is live on the server does have AllowOverride On, yet the mod_rewrite still does not work.

I had 2 declarations for it in .htaccess, because I was unsure if it was required.  The WordPress install is in /blog. I've been assuming that the problem is within the virtual hosts, but I cannot seem to get it working.

---

### Post by chrisguk on 2013-05-21
Can you paste the virtual hosts block in here.  It should be located in /etc/apache2/sites-available/

Also I assume your website is in the normal document root for web applications:

/var/www/

So your directory tree should be something like:

/var/www/.htaccess
/var/www/index.php
/var/www/otherphpfiles.php
/var/www/blog/.htaccess
/var/www/blog/index.php

Thats just the basics of course.

Is it a dedicated server or a PC with LAMP install (Linux, Apache2, MySQL, PHP)?

Is it is a server do you have it setup as a DNS server?

Finally is this a remotely hosted web?

The more information you can give will help.

Another thing to do is paste the output of the apache error log here.  Should be located in /var/log/apache2/error.log

you can debug that normally with this:  sudo tail -f /var/log/apache2/error.log in order to see what happens when you start and stop apache.

---

### Post by jonedney on 2013-05-21
Well, as aggravating as this has been, it's working.  I'm unsure if messing with it after my initial post got things working (I haven't looked at it in a few days).

Thank you for all of your posting, I must have had something out of order.

---


---
title: "Apache Virtual Host not working as expected?"
date: 2008-12-03
forum: Server Platforms
---

### Post by Kremlin on 2008-12-03
I had an older ubuntu server with a previous apache configuration that I'm trying to set up again on a newer hardy system.

I have two items under sites-enabled, one for my gallery page and one for the main page.

the web root is /var/www/introspection.net.au/web/

The gallery files are kept under ./gallery2 of the webroot, and the main webpage is under ./web/ of the webroot

my two sites configs are as follows:

Main site:
```
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName introspection.net.au
        ServerAlias www.introspection.net.au
        DocumentRoot /var/www/introspection.net.au/web
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www_ins/web>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On
</VirtualHost>
```

Gallery site:
```
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName gallery.introspection.net.au
        DocumentRoot /var/www/introspection.net.au/web/gallery2
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www_ins/web/gallery2>
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
        ServerSignature On
</VirtualHost>

```

However, when I go to gallery.introspection.net.au, it simply redirects me to the main webroot instead of going to the correct place. Any ideas as to why?

---

### Post by MJN on 2008-12-03
It works fine from here i.e. [www.introspection.net.au]("http://www.introspection.net.au") goes to your website (blue banner) and gallery.introspection.net.au goes to the Gallery 2.1 installer pages.
 
Perhaps your broswer cache needs clearing?
 
Mathew

---

### Post by Kremlin on 2008-12-03
You just checked it in the few moments since I fixed it ;)

The default install of apache symlinks the default virtualhost configuration file in to be loaded first. Foolishly I deleted it thinking it didn't matter, but there is one key line right at the top of the configuration file:

```
NameVirtualHost *
```

Once that was put back it is all fixed. Now I just have to configure drupal with mod-rewrite to get it back and working again!

---


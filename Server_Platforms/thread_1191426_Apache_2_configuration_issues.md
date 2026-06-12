---
title: "Apache 2 configuration issues"
date: 2009-06-18
forum: Server Platforms
---

### Post by afbase on 2009-06-18
Hello, 

I am having issues configuring apache2.  I cannot get my gallery.coldowl.com to work properly.  Here is a snippet of my problem.

```

NameVirtualHost *
<VirtualHost *>
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
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /home/clinton/online/coldowl/
        </Directory>
[     ....  other stuff .....    ]
</VirtualHost>


<VirtualHost *>
ServerName gallery.coldowl.com
DocumentRoot /var/www/gallery
<Directory /var/www/gallery>
AllowOverride All
Options ExecCGI Includes
Order allow,deny
Allow from all
</Directory>
</VirtualHost>


<VirtualHost *>
ServerName bart.coldowl.com
DocumentRoot /var/www/torrentbart/html
<Directory /var/www/torrentbart/html>
AllowOverride All
Options ExecCGI Includes
Order allow,deny
Allow from all
</Directory>
</VirtualHost>



```

[bart.coldowl.com](bart.coldowl.com) works just fine.    however I cannot figure out why [gallery.goldowl.com](gallery.goldowl.com) does not work.  Apaches says 
> **Not Found**

 The requested URL /main.php was not found on this server.
which isn't true.  main.php is found in /var/www/gallery
  Note that gallery.coldowl.com is supposed to be my [gallery2](http://gallery.menalto.com/) site.

---

### Post by jnat64 on 2009-06-19
It might be stupid or unimportant, but the first DocumentRoot is 
```
/var/www
```and the Directory has 
```
/var/www/
```while the gallery has the same structure on the DocumentRoot statement, but

the Directory is
```
/var/www/gallery
```without the suffixed forward slash.

I am really green with apache, but know how precise the .conf files can be.

HTH

---

### Post by afbase on 2009-06-19
> **jnat64 said:**
> It might be stupid or unimportant, but the first DocumentRoot is 
```
/var/www
```and the Directory has 
```
/var/www/
```while the gallery has the same structure on the DocumentRoot statement, but

the Directory is
```
/var/www/gallery
```without the suffixed forward slash.

I am really green with apache, but know how precise the .conf files can be.

HTH

I tried these two modifications of the issue you pointed out
A)
```

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
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /home/clinton/online/coldowl/
        </Directory>
[     ....  other stuff .....    ]
</VirtualHost>

```
B)```

<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /home/clinton/online/coldowl/
        </Directory>
[     ....  other stuff .....    ]
</VirtualHost>

```
Niether worked to resolve the issue.  thus far my /etc/apache2/sites-available/default looks like A).  Any other ideas?  Is this a chmod or chown issue????

---

### Post by wojox on 2009-06-19
Rename main.php to index.php

---


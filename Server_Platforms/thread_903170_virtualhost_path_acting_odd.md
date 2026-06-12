---
title: "virtualhost path acting odd"
date: 2008-08-28
forum: Server Platforms
---

### Post by gjj391 on 2008-08-28
I have set up a virtual host, did it all correct i thought but i am getting this behavior...

[www.example.com]("http://www.example.com") >  will go to /var/www/index.html

[www.example.com/index.html]("http://www.example.com/index.html") >  goes to its correct path (/var/www/example.com/index.html)

anyone come across this before ? 

this is my vh file

<VirtualHost *>
        ServerAdmin [email]yo@example.com[/email]
        ServerName [www.example.com](www.example.com)
        ServerAlias example.com
        DocumentRoot /var/www/www.example.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/www.example.com>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

---

### Post by windependence on 2008-08-28
Is this VH file in your /etc/apache2/sites-available or did you put it in your main conf file (not recommended).

-Tim

---

### Post by gjj391 on 2008-08-28
That is in my sites-available, i then ran a2ensite, then  stop, reloaded, and started apache.

---

### Post by mbeach on 2008-08-28
out of curiosity where does
[www.example.com/](www.example.com/)
(note the trailing slash) go?

---

### Post by gjj391 on 2008-08-28
will end up pointing to /var/www/index.html

---

### Post by gjj391 on 2008-08-28
Okay so I simplifed some things this morning and reloaded.

I thought I had it but... now all my virtualhosts point to the first virtualhost added.

Code for /sites-enabled/www.example1.com/

<VirtualHost *>
        ServerAdmin [email]user@user.com[/email]
        ServerName [www.example1.com](www.example1.com)
        ServerAlias * example1.com
        DocumentRoot /var/www/www.example1.com/
</VirtualHost>

I then have a file in the /conf.d/ call virtual.conf which has the following:

NameVirtualHost *

This should be loaded at runtime by apache.conf (http.conf).

Any suggestions now ?

---

### Post by windependence on 2008-08-28
Did you disable the default virtual host?

-Tim

---


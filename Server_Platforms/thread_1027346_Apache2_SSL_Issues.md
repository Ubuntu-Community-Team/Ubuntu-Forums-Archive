---
title: "Apache2 SSL Issues"
date: 2009-01-01
forum: Server Platforms
---

### Post by lucasite on 2009-01-01
Hi all,
Ive been following this document to get apache2 and ssl up and running, but Ive run into some issues.
([https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL))

Ive completed all the instructions, yet when I type **/etc/init.d/apache2 reload**I get the following error:

NameVirtualHost *:80 has no VirtualHosts
httpd not running, trying to start
Permissions denied: make_sock: could not bind to address 0.0.0.0:80 no listening sockets available, shutting down

Here's the config: /etc/apache2/sites-available/default 
[I]
NameVirtualHost *:80

<VirtualHost *:80>
     ServerAdmin webmaster@localhost
     DocumentRoot /var/www/
...
</VirtualHost>
[/I]
and this is the ssl config: /etc/apache2/sites-available/ssl

[I]NameVirtualHost *:443

<VirtualHost *:443>
     ServerAdmin webmaster@localhost
     SSLEngine On
     SSLCertificateFile /etc/apache2/ssl/apache.pem
     DocumentRoot /var/www/
...
</VirtualHost>[/I]

Incidentally, the following config file shows this: /etc/apache2/ports.conf

[I]# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
[/I]

Also, if I visit my url in a browser, I get an invalid certificate. Im using homedns.org so my question is, when I generate my ssl certificate, should I be using the machine name, or the full url from homedns.org? The first part doesnt actually match the machine name of my linux box.


Any advise

Luca

---


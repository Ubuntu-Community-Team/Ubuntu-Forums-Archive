---
title: "Cannot get VirtualHost files to work"
date: 2012-01-15
forum: Server Platforms
---

### Post by temple3188 on 2012-01-15
Hello all,

I am new to the forum, though I am on it frequently using your advice to solve my Ubuntu problems :)

Anyway, I have tried every solution on here to do with Virtual Host files and nothing is working for me, in fact the last time I tried setting these up I got frustrated and quit.  Perhaps I am missing the concept of a Virtual Host file, all I would like to do is map a url (helloblah.com) to a local web dev directory (/var/www/helloblah), so that I can use the URL during development, this is possible with a VHost file isn't it?

I have just started a fresh dev machine and just finished installing a lamp stack with tasksel.

Under /etc/apache2/
I currently have user configurations in httpd.conf with:
```
ServerName localhost
```This is my ports.conf file: 
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```Under  /etc/apache2/sites-enabled/ I have a file named 'helloblah' with:
```
<VirtualHost *:80>
   DocumentRoot /var/www/helloblah
   ServerName helloblah.com
</VirtualHost>
```From what I gather, after I restart apache I should be able to browse to 'helloblah.com' and I should be taken to the contents of the folder at /var/www/helloblah, yes?

Sorry if this seems like a stupid question but this has stomped me for so long it's embarrassing. 

In pure desperation I have also tried adding '127.0.0.1/helloblah      helloblah.com' to the /etc/hosts file with no success.

Anyone no the problem?

Many Thanks and Kind Regards,

Chris

---


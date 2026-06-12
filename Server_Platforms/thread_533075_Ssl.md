---
title: "Ssl"
date: 2007-08-23
forum: Server Platforms
---

### Post by frankos44 on 2007-08-23
SSL Help please

I have a live (Feisty) Ubuntu server currently in use. 
I have a file called default in /etc/apache2/sites-available.

After following the instructions in the Ubuntu server manual I installed SSL and purchased a certificate.

Now the site works OK with https:..... but if if visit the site using http:.. the bowser complains and suggests I should try https:...... instead.

Obvously I need the http:... to work as before but in my links make only certain pages secure.

I understand that I need two copies of VirtualHost, one for VirtualHost *:80 and another for VirtualHost *:443

How do I do this?

---

### Post by wirelessmonkey on 2007-08-23
Edit the "virtual hosts" entries in your httpd.conf, they may be specified by an INCLUDE file and you may have a vhosts directory that stores those included files.

---

### Post by frankos44 on 2007-08-24
My httpd.conf is empty

---

### Post by NewbieNik on 2007-08-24
then it should be your apache2.conf (I assume you have apache2 installed)

---

### Post by frankos44 on 2007-08-24
Thanks for responding again. Yes I do have Apache2

apache2.conf contains the lines towards the end:
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

The following file exist on the server:
/etc/apache2/sites-available/default
/etc/apache2/sites-enabled/000-default

This is what i did to my already working http port 80 site:

sudo a2enmod ssl
sudo openssl genrsa -des3 -out server.key 1024
sudo openssl req -new -key server.key -out server.csr
sudo openssl x509 -req -days 365 -in server.csr -sighkey server.key -out server.crt
sudo cp server.crt /etc/ssl/certs
sudo cp server.key /etc/ssl/private

"Added  the following to /etc/apache2/sites-available/default under DoucumentRoot"

SSLEngine
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key

"Changed /etc/apache2/ports.conf to read:

Listen 80
Listen 443

Finally restarted apache

---

### Post by frankos44 on 2007-08-24
OK, after messing around for a day I got it working perfectly! The server now responds to HTTP and HTTPS requests. I thought it may be of use to other people trying to build a server. So here goes:

FIRSTLY CONFIGURE SERVER TO USE SSL (You need to purchase a cert of course)

sudo a2enmod ssl
sudo openssl genrsa -des3 -out server.key 1024
sudo openssl req -new -key server.key -out server.csr
sudo cp server.crt /etc/ssl/certs
sudo cp server.key /etc/ssl/private


THEN CHANGE /etc/apache2/ports.conf to read:

Listen 80
Listen 443

RESTART SERVER

sudo /etc/init.d/apache2 restart


CREATE /etc/apache2/sites-available/default as follows:

NameVirtualHost *:443
NameVirtualHost *:80

<VirtualHost *:80>
        ServerName [www.mysite.co.uk](www.mysite.co.uk)
        DirectoryIndex index.php
        DocumentRoot /var/www/mysite/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

<VirtualHost *:443>
        ServerName [www.mysite.co.uk](www.mysite.co.uk)
        DirectoryIndex index.php
        DocumentRoot /var/www/mysite/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined

        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>


RESTART SERVER

sudo /etc/init.d/apache2 restart

That's it folks

FRANKOS

---


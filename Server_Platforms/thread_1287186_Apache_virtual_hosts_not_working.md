---
title: "Apache virtual hosts not working"
date: 2009-10-09
forum: Server Platforms
---

### Post by Gforce20 on 2009-10-09
**Update: extra/httpd-vhosts.conf wasn't being included. Durr. Problem resolved.**

I'm trying to set up multiple domains under one machine (one IP address) using virtual hosts. This worked perfectly with XAMPP for Windows, but on XAMPP/LAMPP on Ubuntu 9.04, every virtual host ([...]/htdocs/domain1/, [...]/htdocs/domain2/, et cetera) just goes to DocumentRoot ([...]/htdocs/). The only things I've changed are http-vhosts.conf and added "Listen 8000" after "Listen 80" in httpd.conf.

My http-vhosts.conf:
[SIZE=1]```
NameVirtualHost *:80

<VirtualHost *:80> 
    ServerAdmin admin@localhost
    DocumentRoot /media/hd/xampp/htdocs/home 
    ServerName home.example.com
    ServerAlias home.local 
    ErrorLog logs/dev-error.log 
    CustomLog logs/dev-access.log common 
</VirtualHost> 
 
<VirtualHost *:80> 
    ServerAdmin admin@localhost
    DocumentRoot /opt/lampp/htdocs/xampp 
    ServerName admin.example.com
    ServerAlias admin.local 
    ErrorLog logs/admin-error.log 
    CustomLog logs/admin-access.log common 
</VirtualHost> 
 
<VirtualHost *:8000> 
    ServerAdmin admin@localhost
    DocumentRoot /media/hd/xampp/htdocs/home 
    ServerName home.example.com
    ServerAlias home.local 
    ErrorLog logs/home-error.log 
    CustomLog logs/home-access.log common 
</VirtualHost> 
 
<VirtualHost *:8000> 
    ServerAdmin admin@localhost
    DocumentRoot /media/hd/xampp/htdocs/xampp 
    ServerName admin.example.com
    ServerAlias admin.local 
    ErrorLog logs/admin-error.log 
    CustomLog logs/admin-access.log common 
</VirtualHost>
```[/SIZE]

---

### Post by upbeat.linux on 2009-10-14
For the standard release of Apache 2.2.x that ships with 9.04 you'll have to create separate config files for each host.

```
/etc/apache2/sites-available
```

You'll then have to enable the site before restarting apache:

```
sudo a2ensite mydomain.com
```

The sites will then show up in 

```
/etc/apache2/sites-enabled
```

Please consult the documentation:

[https://help.ubuntu.com/9.04/serverguide/C/httpd.html]("https://help.ubuntu.com/9.04/serverguide/C/httpd.html")

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

[http://httpd.apache.org/docs/2.2/vhosts/]("http://httpd.apache.org/docs/2.2/vhosts/")

---

### Post by Gforce20 on 2009-10-14
I've looked at that, but I don't think it applies to me because I'm using XAMPP (which doesn't use Ubuntu's Apache).

---


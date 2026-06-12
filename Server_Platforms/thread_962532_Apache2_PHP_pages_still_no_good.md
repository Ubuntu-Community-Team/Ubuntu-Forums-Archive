---
title: "Apache2 PHP pages still no good"
date: 2008-10-29
forum: Server Platforms
---

### Post by Vegan on 2008-10-29
After installing 8.10 last night, and applying fixes as suggested my web server keep serving PHP pages as text without parsing them.

sudo do-release-upgrade -d
sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart


[Wed Oct 29 08:10:07 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Wed Oct 29 08:10:08 2008] [warn] NameVirtualHost *:80 has no VirtualHosts

---

### Post by cdenley on 2008-10-29
Reboot, just for good measure. Clear your browser's cache, restart your browser. Try again. Post this output.
```

grep mods-enabled /etc/apache2/apache2.conf
cat /etc/apache2/mods-enabled/php5.*
cat /etc/apache2/sites-enabled/*
tail /var/log/apache2/error.log
dpkg -l|grep apache

```
create the file /var/www/test.php
[PHP]
<?php
phpinfo();
?>
[/PHP]
make sure the permissions are correct
```

sudo chmod 644 /var/www/test.php

```
See if it works:
[http://localhost/test.php](http://localhost/test.php)

---

### Post by Vegan on 2008-10-29
> **cdenley said:**
> Reboot, just for good measure. Clear your browser's cache, restart your browser. Try again. Post this output.
```

grep mods-enabled /etc/apache2/apache2.conf
cat /etc/apache2/mods-enabled/php5.*
cat /etc/apache2/sites-enabled/*
tail /var/log/apache2/error.log
dpkg -l|grep apache

```
create the file /var/www/test.php
[PHP]
<?php
phpinfo();
?>
[/PHP]
make sure the permissions are correct
```

sudo chmod 644 /var/www/test.php

```
See if it works:
[http://localhost/test.php](http://localhost/test.php)

$ grep mods-enabled /etc/apache2/apache2.conf
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf


$ cat /etc/apache2/mods-enabled/php5.*
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

$ cat /etc/apache2/mods-enabled/php5.*
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
$ cat /etc/apache2/sites-enabled/*
<VirtualHost *:80>
  ServerAdmin [email]veganfanatic@hotmail.com[/email]
  DocumentRoot /web/computer-chess
  ServerName computer-chess.dyndns.biz:80
  ServerAlias computer-chess.dyndns.biz *.computer-chess.dyndns.biz
  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
</VirtualHost>

<Directory /web/computerchess>
  Options FollowSymLinks
  AllowOverride None
  Order allow,deny
  Allow From All
</Directory>
<VirtualHost *:80>
  ServerAdmin [email]veganfanatic@hotmail.com[/email]
  DocumentRoot /web/contract-developer
  ServerName contract-developer.dyndns.biz:80
  ServerAlias contract-developer.dyndns.biz *.contract-developer.dyndns.biz
  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
</VirtualHost>

rest are copies of above



$ tail /var/log/apache2/error.log
[Wed Oct 29 07:53:29 2008] [notice] Graceful restart requested, doing restart
[Wed Oct 29 07:53:29 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
[Wed Oct 29 07:53:29 2008] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch configured -- resuming normal operat
ions
[Wed Oct 29 07:53:30 2008] [notice] caught SIGTERM, shutting down
[Wed Oct 29 07:53:31 2008] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch configured -- resuming normal operat
ions
[Wed Oct 29 08:05:17 2008] [notice] caught SIGTERM, shutting down
[Wed Oct 29 08:06:52 2008] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch configured -- resuming normal operat
ions
[Wed Oct 29 08:10:07 2008] [notice] caught SIGTERM, shutting down
[Wed Oct 29 08:10:08 2008] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch configured -- resuming normal operat
ions
[Wed Oct 29 09:25:26 2008] [error] [client 193.200.51.235] script '/web/computer-chess/abc.php' not found or unable to stat



$ dpkg -l|grep apache
ii  apache2                               2.2.9-7ubuntu3                Apache HTTP Server metapackage
ii  apache2-mpm-prefork                   2.2.9-7ubuntu3                Apache HTTP Server - traditional non-threade
ii  apache2-utils                         2.2.9-7ubuntu3                utility programs for webservers
ii  apache2.2-common                      2.2.9-7ubuntu3                Apache HTTP Server common files
rc  libapache2-mod-mono                   1.2.5-2                       Apache module for running ASP.NET applicatio
ii  libapache2-mod-php5                   5.2.6-2ubuntu4                server-side, HTML-embedded scripting languag
rc  mono-apache-server                    1.2.5-1ubuntu1                backend for mod_mono Apache module
ii  mono-apache-server2                   1.9.1-2                       ASP.NET backend for mod_mono2 Apache module


OK all the sites except 1 now have PHP back up, only one site seems sick now.

---


---
title: "apache subdomains 403 forbidden"
date: 2007-08-16
forum: Server Platforms
---

### Post by twistedtwig on 2007-08-16
Hi all,

I am trying to reset up my server.  I have apache serving pages from the document root. (/var/www/root) houseofhawkins.com 

but the subdomains are not working.  I get 403 Forbidden error:

```

You don't have permission to access / on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 proxy_html/2.5 Server at dale.houseofhawkins.com Port 80

```

the vhosts.conf file is in /etc/apache2/   

which has included from httpd.conf

```

include /etc/apache2/vhosts.conf

```

```

######## default root directory #########

<VirtualHost *>
ServerName houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride all
</Directory>

ErrorLog /var/log/apache2/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>

######################### test page ############

<VirtualHost *>
Servername test.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/test
<Directory />
Options FollowsymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>

```

I don't know how to get this to work, can someone help me please?

---

### Post by twistedtwig on 2007-08-17
Ok so I have done some testing and subdomains work if the directory is a subdirectory of /var/www/root/ (this is where the main page / site is.

/var/www/root/index.html = main home page

/var/www/root/old/index.html = a working subdomain I can link to

/var/www/test/index.html = a subdomain I can not get to work (403 forbidden error)

---

### Post by colo on 2007-08-17
Are the given DocumentRoot-Directories accessible to the apache webserver's effective user id? Please do also paste the vhosts' error logs.

---

### Post by twistedtwig on 2007-08-19
Thanks for the reply.  here is the ls -l for /var/www

```

total 1108
drwxr-xr-x  2 nobody nogroup    4096 2007-08-17 17:52 apache2-default
-rwxr-xr-x  1 nobody nogroup 1040801 2007-08-16 18:57 bettyDB.sql
drwxr-xr-x  6 nobody nogroup    4096 2007-08-16 18:57 charlotte
drwxr-xr-x  2 nobody nogroup    4096 2007-08-16 18:57 dale
drwxr-xr-x  2 nobody nogroup    4096 2007-08-16 18:57 ethan
drwxr-xr-x  8 nobody nogroup    4096 2007-08-16 18:57 footfaerie
drwxr-xr-x  3 nobody nogroup    4096 2007-08-16 18:57 garethwest
-rwxr-xr-x  1 nobody nogroup   27136 2007-08-16 18:57 Hosting.doc
drwxr-xr-x  2 nobody nogroup    4096 2007-08-16 18:57 mobile
-rwxr-xr-x  1 nobody nogroup      23 2007-08-16 18:57 robots-old.txt
drwxr-xr-x  7 nobody nogroup    4096 2007-08-17 01:31 root
drwxr-xr-x 10 nobody nogroup    4096 2007-08-16 18:58 root-old
drwxr-xr-x  3 nobody nogroup    4096 2007-08-16 18:58 shak
drwxr-xr-x  4 nobody nogroup    4096 2007-08-16 18:58 squid-reports
drwxr-xr-x  2 nobody nogroup    4096 2007-08-16 21:53 test
drwxr-xr-x  5 nobody nogroup    4096 2007-08-16 18:58 wap

```

here is the full vhosts just in case:

```

################### Charlotte home page #################

<VirtualHost *>
ServerName charlotte.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/charlotte
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### Foot faerie home page #################

<VirtualHost *>
ServerName footfaerie.me.uk
Serveralias www.footfaerie.me.uk footfaerie.me.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/footfaerie
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


################### gareth west home page #################

<VirtualHost *>
ServerName gareth-west.co.uk
Serveralias www.gareth-west.co.uk gareth-west.co.uk
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/garethwest
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### dale home page #################

<VirtualHost *>
ServerName dale.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/dale
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Ethan home page #################

<VirtualHost *>
ServerName ethan.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/ethan
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### Shak home page #################

<VirtualHost *>
ServerName shak.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/shak
<Directory />
Options FollowSymLinks
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### test home page #################

<VirtualHost *>
ServerName test.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root/old
<Directory />
Options FollowSymLinks
AllowOverride All
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>



################### default root directory #################

<VirtualHost *>
ServerName houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride all
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>

```

here is the /var/log/apache2/error.log file

```

[Sun Aug 19 06:30:13 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 proxy_html/2.5 configured -- resuming normal operations
[Sun Aug 19 07:22:46 2007] [error] [client 65.55.208.147] File does not exist: /var/www/charlotte/robots.txt
[Sun Aug 19 08:39:24 2007] [error] [client 65.55.208.149] File does not exist: /var/www/charlotte/externallinks.html
[Sun Aug 19 13:05:10 2007] [notice] caught SIGTERM, shutting down
[Sun Aug 19 13:05:20 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 proxy_html/2.5 configured -- resuming normal operations
[Sun Aug 19 13:05:26 2007] [error] [client 192.168.10.200] File does not exist: /var/www/charlotte/old, referer: http://test.houseofhawkins.com/
[Sun Aug 19 13:05:26 2007] [error] [client 192.168.10.200] File does not exist: /var/www/charlotte/old, referer: http://test.houseofhawkins.com/
[Sun Aug 19 13:05:26 2007] [error] [client 192.168.10.200] File does not exist: /var/www/charlotte/old, referer: http://test.houseofhawkins.com/
[Sun Aug 19 13:05:26 2007] [error] [client 192.168.10.200] File does not exist: /var/www/charlotte/old, referer: http://test.houseofhawkins.com/
[Sun Aug 19 13:05:26 2007] [error] [client 192.168.10.200] File does not exist: /var/www/charlotte/old, referer: http://test.houseofhawkins.com/
[Sun Aug 19 13:05:27 2007] [error] [client 192.168.10.200] File does not exist: /var/www/root/old/favicon.ico
[Sun Aug 19 13:06:19 2007] [notice] caught SIGTERM, shutting down
[Sun Aug 19 13:06:30 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 proxy_html/2.5 configured -- resuming normal operations
[Sun Aug 19 13:06:33 2007] [error] [client 192.168.10.200] Directory index forbidden by Options directive: /var/www/shak/
[Sun Aug 19 13:06:33 2007] [error] [client 192.168.10.200] File does not exist: /var/www/shak/favicon.ico

```

thank you again for your help this has me stumped

---

### Post by southernman on 2007-08-19
AFAIK - Directories you want to be publicly viewable must be chmod 755 and files within must be 644. That may solve part of the problem, but looks like you still have problems with who actually owns the files. It's my understanding that apache now runs as www-data and that seems to be the other part of the problem, but I can't say how to fix it.

Take all of what I said with a grain of salt until someone more capable chimes in to confirm, deny, or teach us both something. :/

---

### Post by rybaxs on 2008-05-07
Help, Anyone know how to fix /var/www/ all of the files are 403 forbidden. After I load two iptables modules and iptables rules for incoming request on port 21 (open port 21) script my localhost is forbidden.

I've chmod 777 but nothing happens.

---


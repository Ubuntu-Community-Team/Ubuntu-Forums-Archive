---
title: "Apache : Illegal override option FileInfo"
date: 2012-06-06
forum: Server Platforms
---

### Post by Houmie on 2012-06-06
Hi,

I have installed a new Ubuntu 12.04 Server and setup Apache and MySQL.

I am just trying to replicate what I have in my current server and came across one single problem. -> FileInfo

Within these two files below:

/etc/apache2/sites-available/default-ssl
/etc/apache2/sites-available/default

I need to add some overrides for the apache server.

Original:
```
 
        <Directory /var/www/MySite>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride **None**
                Order allow,deny
                allow from all
        </Directory>


        <Directory /var/www/MySite>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride **FileInfo, Indexes**
                Order allow,deny
                allow from all
        </Directory>
```

I have installed the following mods for Apache:

```
sudo apt-get install lamp-server^ -y
sudo apt-get install apache2.2-common apache2-utils openssl openssl-blacklist openssl-blacklist-extra -y
sudo apt-get install curl libcurl3 libcurl3-dev php5-curl -y
sudo apt-get install php5-tidy -y
sudo apt-get install php5-gd -y
sudo apt-get install php-apc -y
sudo apt-get install memcached -y
sudo apt-get install php5-memcache -y
sudo a2enmod ssl
sudo a2enmod rewrite
sudo a2enmod headers 
sudo a2enmod expires 
sudo a2enmod php5
```

Have I missed something?

Thanks,
Houman

---

### Post by lisati on 2012-06-06
Once you've done the a2enmod stuff, don't forget to reload or restart apache2.

---

### Post by Houmie on 2012-06-06
> **lisati said:**
> Once you've done the a2enmod stuff, don't forget to reload or restart apache2.

My appologies as I had forgotten to mention when I get this error shown:

```
sudo /etc/init.d/apache2 restart
```

So in fact after entering those changes in the config files and restart the server I get:

```
Syntax error on line 11 of /etc/apache2/sites-enabled/000-default:
Illegal override option FileInfo,
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

When I remove FileInfo back to None

```
 * Restarting web server apache2  ... waiting        [OK]

```

I can't see anything unusual in the error.log

```
[Wed Jun 06 08:23:51 2012] [notice] caught SIGTERM, shutting down
[Wed Jun 06 08:23:52 2012] [warn] RSA server certificate CommonName (CN) `mySite.com' does NOT match server name!?
[Wed Jun 06 08:23:52 2012] [warn] RSA server certificate CommonName (CN) `mySite.com' does NOT match server name!?
[Wed Jun 06 08:23:52 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations

```

I get that warning because its a test server, nonetheless I get the same warning without the override FileInfo and yet it restarts the Apache server correctly. Therefore this warning should be harmless.

Any other idea please?

---

### Post by Houmie on 2012-06-06
I found it. There should be no commas in the list of overrides. It should be

```
AllowOverride FileInfo Indexes
```

:popcorn:

---


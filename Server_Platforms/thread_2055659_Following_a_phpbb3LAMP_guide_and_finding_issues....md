---
title: "Following a phpbb3/LAMP guide and finding issues..."
date: 2012-09-09
forum: Server Platforms
---

### Post by felinoel on 2012-09-09
[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

```
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
granting access to database phpmyadmin for phpmyadmin@localhost: success.
verifying access for phpmyadmin@localhost: success.
creating database phpmyadmin: success.
verifying database phpmyadmin exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password
Lighttpd not installed, skipping
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

I am on the last step on that guide which is to go to either of these sites```
http://ip/phpmyadmin   or http://localhost/phpmyadmin
```and it is just simple phpbb stuff from there... but... those sites give me a 404 error?

---

### Post by SeijiSensei on 2012-09-10
Did you restart apache with "sudo service apache2 restart"?  If so, look in /var/log/apache2/error.log to see if it threw any errors?

---

### Post by felinoel on 2012-09-10
> **SeijiSensei said:**
> Did you restart apache with "sudo service apache2 restart"?  If so, look in /var/log/apache2/error.log to see if it threw any errors?

The guide gave the option of lighttp or apache, after some reading I went with lighttp... should I not have?

---

### Post by SeijiSensei on 2012-09-10
Apache is more commonly used, and what I have used for years.  So someone else will have to help with lighttpd.

If you have a file called /etc/init.d/lighttpd, then you can try restarting it with "sudo service lighttpd restart" and see if that works.

---

### Post by felinoel on 2012-09-10
> **SeijiSensei said:**
> Apache is more commonly used, and what I have used for years.  So someone else will have to help with lighttpd.

If you have a file called /etc/init.d/lighttpd, then you can try restarting it with "sudo service lighttpd restart" and see if that works.

Nope, no file there, guess I am installing apache.



EDIT:
...it isn't letting me?! Do I have to remove lighttp first?

---

### Post by felinoel on 2012-09-10
Ok got it to work with apache... I think, if I use this.
[http://127.0.1.1/info.php](http://127.0.1.1/info.php)

It gets the first part to work.
[http://i671.photobucket.com/albums/vv77/ZINOVSKY/phpinfo-MozillaFirefox_003.png](http://i671.photobucket.com/albums/vv77/ZINOVSKY/phpinfo-MozillaFirefox_003.png)

But not the final part, the part I need... x.x
[http://i671.photobucket.com/albums/vv77/ZINOVSKY/127001-localhost|phpMyAdmin337deb1-MozillaFirefox_004.png](http://i671.photobucket.com/albums/vv77/ZINOVSKY/127001-localhost|phpMyAdmin337deb1-MozillaFirefox_004.png)



> **SeijiSensei said:**
> Did you restart apache with "sudo service apache2 restart"?  If so, look in /var/log/apache2/error.log to see if it threw any errors?

```
[Sun Sep 09 07:41:33 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Sep 09 14:03:21 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Sep 09 14:03:21 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Sep 09 14:04:33 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin, referer: http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/
[Sun Sep 09 14:04:33 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Sep 10 17:55:18 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Sep 10 19:32:12 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin, referer: http://ubuntuforums.org/showthread.php?p=12230906
[Mon Sep 10 19:32:12 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Sep 10 19:32:12 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Sep 10 22:43:12 2012] [notice] caught SIGTERM, shutting down
[Mon Sep 10 22:43:13 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Sep 10 22:43:29 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin, referer: http://ubuntuforums.org/showthread.php?p=12230906
[Mon Sep 10 22:43:30 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin, referer: http://ubuntuforums.org/showthread.php?p=12230906
[Mon Sep 10 22:43:32 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin
[Mon Sep 10 22:43:48 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Sep 10 22:45:42 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin
```

```
[Sat Sep 08 01:42:40 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sat Sep 08 01:42:51 2012] [notice] caught SIGTERM, shutting down
[Sat Sep 08 01:42:52 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 08 01:46:43 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 01:46:44 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 08 01:49:17 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 01:49:17 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 08 01:51:05 2012] [notice] caught SIGTERM, shutting down
[Sat Sep 08 01:51:51 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sat Sep 08 01:51:55 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 01:51:55 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sat Sep 08 01:52:47 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 01:52:47 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 08 01:53:42 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 01:53:42 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 08 01:55:46 2012] [notice] caught SIGTERM, shutting down
[Sat Sep 08 01:57:24 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sat Sep 08 01:57:27 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 01:57:27 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sat Sep 08 01:58:45 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 01:58:45 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 08 02:18:51 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 02:18:51 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 08 02:19:23 2012] [notice] caught SIGTERM, shutting down
[Sat Sep 08 02:19:58 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sat Sep 08 02:20:00 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Sep 08 02:20:00 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sat Sep 08 13:16:39 2012] [notice] caught SIGTERM, shutting down
[Sat Sep 08 13:26:20 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Sep 09 03:21:55 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Sep 09 07:41:33 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

---

### Post by SeijiSensei on 2012-09-11
I just followed the same steps as you.  My guess is that you did not remove phpmyadmin after installing apache.  The errors you report show that apache cannot find the phpmyadmin directory which should be /var/www/phpmyadmin on a standard installation.  So I'd guess removing and reinstalling phpmyadmin might do the trick:

```

sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin

```

Then select apache when prompted.  This worked for me.

---

### Post by felinoel on 2012-09-11
> **SeijiSensei said:**
> I just followed the same steps as you.  My guess is that you did not remove phpmyadmin after installing apache.  The errors you report show that apache cannot find the phpmyadmin directory which should be /var/www/phpmyadmin on a standard installation.  So I'd guess removing and reinstalling phpmyadmin might do the trick:

```

sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin

```

Then select apache when prompted.  This worked for me.

O_O
The php boards screen came up?!!!?!?!?!?!?!?!?
OMFG yes finally, this has been such an arduous task that started with a faulty ethernet port and ended up to here but finally I think there won't be any more issues.

There needs to be some kind of fame system, something to send you beans or even grinds since the post count is counted by beans.
It is required that you are given all the grinds, all of them.

---


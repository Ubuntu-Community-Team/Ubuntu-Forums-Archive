---
title: "phpmyadmin errors after login"
date: 2009-06-07
forum: Server Platforms
---

### Post by Stoneface on 2009-06-07
I had some phpmyadmin problems onmy local server installed on Ubuntu Desktop on my laptop. The whole style or lay-out fell apart and I had a controluser warning. So I radically decided to reinstall pma using ```
sudo apt-get install phpmyadmin
``` after ```
sudo apt-get remove phpmyadmin
``` and did it even once using synaptic. But after each install I got these errors after trying to login:
```
#0  PMA_sendHeaderLocation(http://localhost/phpmyadmin/index.php?token=7e5ae2ccb9f77209cec3cf5d93bb835a) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```

These errors mean nothing to me. PMA worked like a charm before. My Apache, PHP and MySQL are still ok. I don't know what to change to fix this. My Firefox does accept cookies and the passsword and user name in config.inc.php is the one I use.
I decided to start this new thread hoping someone can tell me I just overlooked something silly and I can fix this.. I don't want to reinstall for the third time..

---

### Post by Stoneface on 2009-06-07
Polite bump

---

### Post by bjk03 on 2009-06-07
Is this on 9.04? Did you install all the packages that phpmyadmin depends on: dbconfig-common, libmcrypt4, php5-mcrypt? I just installed it and it is working fine on my system.

---

### Post by Stoneface on 2009-06-08
Yes 9.0.4 Jaunty. I installed phpmyadmin using sudo apt-get install phpmyadmin so I presume that all needed packages were installed automagically. What package do you think I miss?

---

### Post by Stoneface on 2009-06-08
Well I reinstalled it again via Synaptic package manager. But no pma database was created in mysql. Then I ran sudo dpkg-reconfigure phpmyadmin. Now I do have a database phpmyadmin. But I still cannot login from the working phpmyadmin login screen with root as user and my password. I still get:
```
#0  PMA_sendHeaderLocation(http://localhost/phpmyadmin/index.php?token=174757b47a822bea0d7836085e2d8788) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```
This is really driving me nuts

---

### Post by bjk03 on 2009-06-08
This is just a wild guess but I would have to guess that its the mcrypt stuff.

---

### Post by Stoneface on 2009-06-08
@ bjk03. What do you mean by mcrypt stuff?

---

### Post by kapi on 2009-06-08
if its any consolation I have been trying to get the login screen to access phpmyadmin for pretty close to a week now and am getting no where.

will try to install the extra packages mentioned here and get back to you concerning the results

Kapi

---

### Post by kapi on 2009-06-08
No joy - just checked the synaptic package manager and they are already installed, 

back to the drawing board

---

### Post by VK7HSE on 2009-06-08
Don't forget, unless you have already created a mysql login for yourself, you need to login in as **root** and provide the password that you setup when you installed mysql. Also as previously mentioned, run dpkg-reconfigure phpmyadmin to create the pma database, and answer YES to that!

---

### Post by Stoneface on 2009-06-08
> **VK7HSE said:**
> Don't forget, unless you have already created a mysql login for yourself, you need to login in as **root** and provide the password that you setup when you installed mysql. Also as previously mentioned, run dpkg-reconfigure phpmyadmin to create the pma database, and answer YES to that!

I can login @ MySQL as root: ```
jasper@jasper-laptop:~$ mysql -u root -p
```. And the phpmyadmin database exists:```
Database changed
mysql> show tables;
+----------------------+
| Tables_in_phpmyadmin |
+----------------------+
| pma_bookmark         | 
| pma_column_info      | 
| pma_designer_coords  | 
| pma_history          | 
| pma_pdf_pages        | 
| pma_relation         | 
| pma_table_coords     | 
| pma_table_info       | 
+----------------------+
8 rows in set (0.00 sec)
```
And config-db.php in /etc/phpmyadmin/ has:```
$dbuser='root';
$dbpass='password';
$basepath='';
$dbname='phpmyadmin';
$dbserver='';
$dbport='';
$dbtype='mysql';
``` All locally stored so passwords don't need to be hidden here..
I use the same p/w and user for phpmyadmin and thats how I entered it after reconfiguring. So now I do have a phpmyadmin database and the phpmyadmin login screen. So what am I missing here?

---

### Post by Stoneface on 2009-06-08
Well anybody any suggestions?

---

### Post by Stoneface on 2009-06-08
Bump.

---

### Post by Stoneface on 2009-06-09
@  Kapi Have you had any luck yet?

---

### Post by Stoneface on 2009-06-11
Anybody out there who could explain step by step how I can get phpmyadmin to run again on my Desktop? Apache2, MySQL and PHP are running, phpmyadmin is just broken and I have installed it 4 times, but no luck whatsoever. I wonder if the version I got is broken..

---

### Post by ocgstyles on 2009-06-18
> **Stoneface said:**
> Anybody out there who could explain step by step how I can get phpmyadmin to run again on my Desktop? Apache2, MySQL and PHP are running, phpmyadmin is just broken and I have installed it 4 times, but no luck whatsoever. I wonder if the version I got is broken..

I had a little difficulty too.  Here's what I did.

Create a soft link in your document root that points to your phpmyadmin install.

$ sudo ln -s /usr/share/phpmyadmin /var/www/pma

You can then load it by going to:

[http://localhost/pma/index.php](http://localhost/pma/index.php)

It didn't work for me without the index.php at the end, although in other places index.php loads without explicitly stating so...

HTH

keith

---

### Post by Stoneface on 2009-06-19
@ OCGStyles Thanks for your input. I appreciate it a lot! 

I will reboot into Ubuntu in a few minutes and give this a try. I never worked with soft links before, but this could maybe help pma te get started up properly and to send my login details properly.
I will post back the result asap.

---

### Post by Stoneface on 2009-06-19
Well I created the sof link or symbolic link. I went to [http://localhost/pma/index.php](http://localhost/pma/index.php). And when I tried to login I was sent to the SAME error page indicating
#0  PMA_sendHeaderLocation([http://localhost/pma/index.php?token=a33899b2f73edb1d9fa7192b204e3bb8](http://localhost/pma/index.php?token=a33899b2f73edb1d9fa7192b204e3bb8)) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

---

### Post by Stoneface on 2009-06-19
Bump

---

### Post by Stoneface on 2009-06-20
Well I checked my Apache2 error logs (summary):```

[Thu Jun 11 13:16:45 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 11 14:31:11 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Jun 11 16:45:51 2009] [notice] caught SIGTERM, shutting down
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Fri Jun 19 13:58:21 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 19 14:03:37 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Jun 19 14:30:28 2009] [notice] caught SIGTERM, shutting down
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Fri Jun 19 14:31:49 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 19 15:17:14 2009] [notice] caught SIGTERM, shutting down
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Fri Jun 19 15:18:30 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 19 15:19:46 2009] [notice] caught SIGTERM, shutting down
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Fri Jun 19 15:25:19 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 19 15:50:26 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Jun 19 16:14:42 2009] [notice] caught SIGTERM, shutting down
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Fri Jun 19 19:03:50 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 19 20:19:57 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Fri Jun 19 20:19:57 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 19 20:21:16 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Fri Jun 19 20:21:16 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 19 20:21:40 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

```

I saw this PHP warning:```
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
``` So maybe mcrypt is somehow making pma not handle the login details properly. So maybe that's why I keep on getting this error:```
#0  PMA_sendHeaderLocation(http://localhost/pma/index.php?token=b221053cf85ad9224973ad16ca120acf) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```. I saw that people posted a bug related to this mcrypt error @ launchpad:[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/305254](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/305254). When I followed the instuctions there and added a # in front of extension=mcrypt.so in mcrypt.ini and tried to login again it did not work. But maybe I need a reboot first..
I will continue my research on this PHPMyadmin problem and will post again when I have more data.

---

### Post by Kareeser on 2009-06-20
Yes, to complete the mcrypt extension installation, you have to restart your apache server.

---

### Post by Stoneface on 2009-06-20
Well I rebooted and I still have the same errors when I try to log into pma:
```
#0  PMA_sendHeaderLocation(http://localhost/pma/index.php?token=313a434ee4e7f2927375ad45a5244e32) called at [/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php:612]
#1  PMA_auth_set_user() called at [/usr/share/phpmyadmin/libraries/common.inc.php:821]
#2  require_once(/usr/share/phpmyadmin/libraries/common.inc.php) called at [/usr/share/phpmyadmin/index.php:34]

```. It was not a question of installation but an mcrypt error (see earlier apache error log).

When I checked the error log again (/var/log/apache2/error.log)  I saw this:
```
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Sat Jun 20 08:05:15 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sat Jun 20 10:55:57 2009] [notice] caught SIGTERM, shutting down
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
[Sat Jun 20 12:09:21 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sat Jun 20 12:52:54 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sat Jun 20 13:11:21 2009] [notice] caught SIGTERM, shutting down
[Sat Jun 20 20:43:46 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sat Jun 20 21:03:16 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
```

Strange that I still get the mcrypt error as I added # in front of that line following the launchpad temporary fix.. Oh eh and after reboot I did a sudo /etc/init.d/apache2 restart and tried another login. But to no avail.

---

### Post by Kareeser on 2009-06-20
mcrypt is not a required component in the running of phpmyadmin. My server didn't have the mcrypt extension for months, and phpmyadmin worked fine, only outputting warnings during operation.

Have you tried uninstalling and purging phpmyadmin completely, and then reinstalling?

```
sudo apt-get purge phpmyadmin
```

Alternatively, you could try installing phpmyadmin by hand. This is the way it is traditionally done (and I really don't see the point in packaging phpmyadmin, since it's not a "program", per se, but a collection of scripts &ndash; one possible reason is security, since packages can be updated, but I digress).

```

cd /var/www
sudo wget http://voxel.dl.sourceforge.net/sourceforge/phpmyadmin/phpMyAdmin-3.2.0-all-languages.tar.gz
sudo tar xfvz phpMyAdmin-3.2.0-all-languages.tar.gz
sudo rm phpMyAdmin-3.2.0-all-languages.tar.gz

```

Then edit config.inc.php manually to include your mysql root login and password, and you should be good to go.

Remember, manually installing phpmyadmin won't open you up to updates, so you'll have to monitor that yourself.

---

### Post by Stoneface on 2009-06-20
Gonna try a purge now (never that did before) and after that follow your installation instructions the best way I can.

---

### Post by Stoneface on 2009-06-20
I did a purge and then followed you instructions:
```
cd /var/www
sudo wget http://voxel.dl.sourceforge.net/sourceforge/phpmyadmin/phpMyAdmin-3.2.0-all-languages.tar.gz
sudo tar xfvz phpMyAdmin-3.2.0-all-languages.tar.gz
sudo rm phpMyAdmin-3.2.0-all-languages.tar.gz
```

But when I entered /etc/phpmyadmin/ to go to the config file I got an error..
But I found the file where pma was stored, renamed it to pma and ound a config.sample.inc.php. I will either do an install or rename the file and edit it.

---

### Post by Stoneface on 2009-06-20
Yes! It is working now! Kareeser, you're an angel fallen from the sky! Why didn't I consider a standard installation before... Thanks a million! Now I can login usinf MySQL root credentials!

---

### Post by Kareeser on 2009-06-20
Glad to hear!

In my instructions, I had you install phpmyadmin into the /var/www/ folder. Make sure you keep it safe!

---

### Post by Stoneface on 2009-06-26
Yeah I did. Just got a little confused

---

### Post by Kareeser on 2009-06-26
When installing phpmyadmin in /var/www, the entire program directory is being served to the web, which *could* be a security problem, if not secured properly.

For example, if you do your file editing in gedit, the program will, by default, save a backup file with a ~ appended to the extension. Apache does not understand this and **will serve the file in plaintext**, which, when served from a configuration file, will expose your login names and passwords.

---

### Post by Stoneface on 2009-06-28
I see. I do not want that even though this is all done on my local server.. I might make it public some time in the future. And this would be a security threat indeed. So where should I install it then and have it work as well? In /var/?

---

### Post by Stoneface on 2009-07-09
Well I removed and reinstalled via Synaptic Manager and now it is just working!! Don't ask me why. Maybe a new PMA version... But boy I'm happy!!

---

### Post by gl-ru on 2010-12-31
The solution is to force an URL. Add the following line to "config.inc.php", changing the obvious.
```

$cfg['PmaAbsoluteUri'] = 'http://yourdomain.com/phpmyadmin/';

```

---


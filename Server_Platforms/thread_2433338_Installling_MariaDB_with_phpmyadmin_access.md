---
title: "Installling MariaDB with phpmyadmin access"
date: 2019-12-17
forum: Server Platforms
---

### Post by mangonels on 2019-12-17
Hello.
My objective is to install a MariaDB database which is accessible through phpmyadmin remotely for convenience.

I've been following these instructions, they are the closest I found to my Ubuntu version (19.10):[URL="https://websiteforstudents.com/install-apache2-mariadb-and-php-7-2-with-phpmyadmin-on-ubuntu-16-04-18-04-18-10-lamp-phpmyadmin/"]
https://websiteforstudents.com/install-apache2-mariadb-and-php-7-2-with-phpmyadmin-on-ubuntu-16-04-18-04-18-10-lamp-phpmyadmin/[/URL]

In theory I already installed Apache2 (verified the server is active (running), with the command "service apache2 status"), and MariaDB (verified by logging in).

However, on step 4 (Install PHP 7.2-FPM and Related Modules), when I must locate the php.ini file for configuring, The tutorial says it's probably located at: "/etc/php/7.2/apache2/php.ini", for PHP version 7.2.
However, this absolute path does not exist. It exists up to "/etc/php/7.2/", and then there's the "cli" and "fpm" folders, which both contain a php.ini file.

Should I edit both or any of these in order to comply with the rest of the tutorial? Or does the fact that the "apache2" folder doesn't exist maybe indicate some problem with my apache2 installation?...

Thank you in advance for any hints or help!

---

### Post by howefield on 2019-12-17
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by SeijiSensei on 2019-12-17
Must you use Mariadb? If you're willing to use MySQL you can install everything you need with these commands:

```

sudo apt update
sudo apt install lamp-server^

```

Personally I use PostgreSQL rather than either of those.

---

### Post by mangonels on 2019-12-18
I'm not entirely sure, but I think everything I need to connect to the database will only accept mysql or derivate such as mariadb.

So I guess I can use mysql, but I already started those steps on the tutorial (which installed quite a lot of stuff), so what about all the stuff I already downloaded, will it be overwritten? Should I at least remove mariadb?
Also, I'm not familiar with the installation/configuration process, I'll still need external phpmyadmin access, which I wouldn't know how to configure. That's why I followed such a detailed tutorial. Could you maybe explain or point out to some other source?

I must also say, I made a backup of my previous mariadb files in "/var/lib/mysql". I asume I'll be capable of re-applying this backup even on a mysql database? The directory name seems to comply at least.

---

### Post by SeijiSensei on 2019-12-18
If you install "lamp-server" you'll have working versions of Apache, MySQL, and PHP.  With those you can install phpmyadmin from the repositories with
```
sudo apt install phpmyadmin
```
MySQL will likely remove MariaDB when it installs, but if you want to be sure use

```
sudo apt remove mariadb mariadb-*
```

I suspect MySQL will simply use the files it finds in /var/lib/mysql after it is installed.

---

### Post by mangonels on 2019-12-18
Ok.
I did exactly what you suggested (exact order). I installed lamp-server, then I installed phpmyadmin.

I also:
Verified apache was installed with: ```
service apache2 status
``` shows as active(running)

I verified MySQL was installed by attempting to log in. However using root with an empty password yelds this error:
```
root@ubuntu:~# mysql -u root -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

I read online this probably means mysql is not installed. But right now I'm not even sure if I'm using mysql or mariadb.

I also did try your mariadb removal comand for making sure only mysql remains, however it returns quite a few of these messages: 
```
"Package (...) is not installed, so not removed"
```

```
php --version
``` shows php is installed.

Not sure if phpmyadmin was installed propperly:
```
root@ubuntu:~# apt install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package phpmyadmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'phpmyadmin' has no installation candidate
```

**Edit:** I didn't get to install it on the tutorial I was following, since that was on step 5, and I got to 4 and a half. So if the comand you gave me didn't do it, it's not installed.

---

### Post by LHammonds on 2019-12-18
I think you were just fine with MariaDB which is a superior product to MySQL.

You might want to look at alternatives to PHPMySQL...maybe a single PHP file called [Adminer](https://www.adminer.org/)

If possible, I would keep my database server separate from the web server.

LHammonds

---

### Post by SeijiSensei on 2019-12-18
> **mangonels said:**
> Ok.
I verified MySQL was installed by attempting to log in. 

I'd use "sudo systemctl status mysql". 

> However using root with an empty password yelds this error:
```
root@ubuntu:~# mysql -u root -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

I read online this probably means mysql is not installed. But right now I'm not even sure if I'm using mysql or mariadb.

No, it could be installed, but the server is not running. Check with the systemctl command above.  If it's not running, use
```
sudo systemctl start mysql
```
to start the server.

> 
I also did try your mariadb removal comand for making sure only mysql remains, however it returns quite a few of these messages: 
```
"Package (...) is not installed, so not removed"
```


I had you use mariadb-* which matches a very large number of software packages most of which connect the database to other programs. It's not surprising that many of them were not installed on a basic system.

> 
```
php --version
``` shows php is installed.


On my 19.10 system that returns
```
PHP 7.3.11-0ubuntu1 (cli) (built: Nov 20 2019 14:21:42) ( NTS )
```
Notice the "cli". That refers to the "command-line interface" version of PHP.  Typing "php" at the command prompt runs the program /usr/bin/php, but for your purposes you're much more interested in the version of PHP that works with the Apache web server.

If you want to check that the web module is installed, the best solution is to create an "info.php" file in /var/www/html like this:
```

cd /var/www/html
echo "<?php phpinfo()?>" | sudo tee /var/www/html/info.php
```
Now if you navigate with the web browser on the machine to the URL [http://localhost/info.php](http://localhost/info.php) you should see an enormous amount of information about your system, the Apache server, and the PHP installation.

> Not sure if phpmyadmin was installed propperly:
```
root@ubuntu:~# apt install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package phpmyadmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'phpmyadmin' has no installation candidate
```

No, that quite clearly says that the installer couldn't find phpmyadmin and thus couldn't install it.

phpmyadmin resides in the "universe" repository. Maybe your system doesn't have that enabled by default.  Try this:
```

cd /etc/apt
grep universe sources.list

```
You should see results that look like this:
```
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
```
If the lines begin with a hash mark ("#") then the repositories have been disabled. You can use the nano editor to fix this. Run the command "sudo nano /etc/apt/sources.list" then scroll down to the lines ending in "universe".  Delete the hash mark from these lines, then save by typing Ctrl+X and answering yes when you are prompted.  Now run
```

sudo apt update
sudo apt install phpmyadmin

```
Any better?

---

### Post by mangonels on 2019-12-18
I don't really know what to say to mariadb's superiority, I've always been advised to use it, but I'm not familiar with the details to why exactly it's better. I just checked a comparison and indeed, it even says mariadb is actually faster. 
It pains me to say this, but right now the only help I can get is with mysql... maybe I can eventually replace it.

---

MySQL: Starting mysql failed and service status

```
root@ubuntu:~# systemctl start mysql
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.
root@ubuntu:~# systemctl status mysql
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; bad; vendor preset: enable
   Active: failed (Result: exit-code) since Wed 2019-12-18 21:57:25 UTC; 47s ago
  Process: 6810 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exit


Dec 18 21:57:25 ubuntu systemd[1]: mysql.service: Service RestartSec=100ms expir
Dec 18 21:57:25 ubuntu systemd[1]: mysql.service: Scheduled restart job, restart
Dec 18 21:57:25 ubuntu systemd[1]: Stopped MySQL Community Server.
Dec 18 21:57:25 ubuntu systemd[1]: mysql.service: Start request repeated too qui
Dec 18 21:57:25 ubuntu systemd[1]: mysql.service: Failed with result 'exit-code'
Dec 18 21:57:25 ubuntu systemd[1]: Failed to start MySQL Community Server.
lines 1-11/11 (END)...skipping...
```


PHP:[COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR]Can I actually navigate with a web browser on a terminal only ubuntu installation? **Edit: **I found out aparently yeah, but will it be good enough?


PHPMyAdmin:

I uncommented every line ending in "universe". I also had to uncomment one ending in "universe multiverse" for the full list extracted with the grep command to have no hashes (I'm guessing thats what you implied). But phpmyadmin still won't install:
```
root@ubuntu:/etc/apt# grep universe sources.list
## team. Also, please note that software in universe WILL NOT receive any
deb http://nova.clouds.archive.ubuntu.com/ubuntu/ eoan universe
deb-src http://nova.clouds.archive.ubuntu.com/ubuntu/ disco universe
deb http://nova.clouds.archive.ubuntu.com/ubuntu/ eoan-updates universe
deb-src http://nova.clouds.archive.ubuntu.com/ubuntu/ disco-updates universe
deb http://nova.clouds.archive.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse
deb-src http://nova.clouds.archive.ubuntu.com/ubuntu/ disco-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu eoan-security universe
deb-src http://security.ubuntu.com/ubuntu disco-security universe
root@ubuntu:/etc/apt# apt install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package phpmyadmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

---

### Post by SeijiSensei on 2019-12-19
As I said, you have to run "sudo apt update" after uncommenting the universe repositories. In fact, you should do that each time you begin installing software from the repositories. That command tells Ubuntu to update its software lists.

You can use the elinks web browser on text-only machines. I don't know if it's installed by default.

Did you look at "journalctl -xe" as the error message said? What about the logs in /var/log/mysql? Logs are your friends.

You might consider renaming /var/lib/mysql to /var/lib/mysql.old then trying to start the server again. Maybe it doesn't like those mariadb files.

Beyond this, I'm at a loss. As I said, I don't use either MySQL or MariaDB unless an application requires them like WordPress does. I'm much happier using PostgreSQL.

---

### Post by mangonels on 2019-12-19
Hi. I decided for now I'm just going to leave it at a regular mariadb installation. I would have prefered using phpmyadmin with it, but since it got so complicated, I just decided I'd do it some other time. I can survive with just the core database, + mariadb is better than mysql anyway.

I also managed to apply the backup onto the new mariadb database by simply stopping the mariadb service, replacing backed up contents in /var/log/mysql and changing permisions with chmod, then starting the mariadb service again.

In any case, I REALLY appreciate your assistance and patience with this :)

---

### Post by LHammonds on 2019-12-20
It is best to let the database server just be a database server.  You could setup a different machine to be a web server though and plop the adminer file on it.  I have a tutorial on [how to setup an Apache server]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261") as well as others that might interest you.

LHammonds

---


---
title: "dependancy hell with mysql"
date: 2019-09-26
forum: Server Platforms
---

### Post by lxme on 2019-09-26
Hello aLL!

Ok, I have a server running Bionic, it was running an owncloud and another website for my lan.
Sadly it crashed pretty badly after repeated power failure.

I'am trying to get it back on track, but my current problem is with mysql, I feel db where corrupter and I wrecked the installation further trying to force install some package (can't remember which ones, it was a while ago)

Today I am having difficulties with mysql I would like to reinstall it from scratch but it won't let me

```
 dpkg --get-selections | grep mysql-server
mysql-server					install
mysql-server-5.5				deinstall
mysql-server-5.7				install
mysql-server-core-5.7				install

```

I started with a ```
sudo dpkg --configure -a
Setting up mysql-server-5.7 (5.7.27-0ubuntu0.18.04.1) ...
Checking if update is needed.
Checking server version.
Running queries to upgrade MySQL server.
mysql_upgrade: [ERROR] 130: Incorrect file format 'tables_priv'
mysql_upgrade failed with exit status 5
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

```

and now I'm stuck..

It seems my problem come from 
mysql_upgrade: [ERROR] 130: Incorrect file format 'tables_priv'

can ayone help ?
Thank you

---

### Post by SeijiSensei on 2019-09-26
Try moving the directory /var/lib/mysql out of the way, e.g.,
```
sudo mv /var/lib/mysql /var/lib/mysql.old
```

That will probably eliminate the tables_priv issue.

Do you have a backup of your databases from using mysqldump?

---

### Post by Tadaen_Sylvermane on 2019-09-26
^ most important. safest way to backup i've found. i only have media dbs running on mariadb, and they get dumped every morning at 3 am. I've debated doing it twice a day but it's not super critical. this is also a good time for you to get a basic ups, save this from happening again. get one with a usb connection that you can configure to shutdown safely / or run a shutdown script if you need.

---

### Post by LHammonds on 2019-09-27
#1 - Make sure you have backups available to you before doing anything.  Make sure you have mysqldump (.sql) files of your database before it crashed.  Make sure you have your website files and configuration files backed up.  Make sure those backups are NOT physically on the machine having the problem.
#2 - Be mentally prepared to wipe out the server and re-install it from scratch.
#3 - Continue with troubleshooting steps.

If you are unsure about being able to re-install from scratch, I would recommend testing this in a virtual environment to see if you can install a new OS, database, webserver and restore your backups to the VM.

LHammonds

---


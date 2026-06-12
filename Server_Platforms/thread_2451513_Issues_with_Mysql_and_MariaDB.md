---
title: "Issues with Mysql and MariaDB"
date: 2020-10-05
forum: Server Platforms
---

### Post by masaro on 2020-10-05
Hello people,

i am running an ubuntu server with Plesk on it, and yesterday i have made a dist-upgrade to Ubuntu 20.04 LTS through SSH.
I had some configuration trouble with the mysql-server-8.0 version that had been installed due to the strict mode, but i had managed to fix it and send my website back online.
I don't know what the hell happened overnight but the database wasn't working again the morning after, apparently mariadb had been installed automatically (maybe a cron job), and looking at /var/log/mysql/error.log i've found

[FONT=Lato]InnoDB: Invalid flags 0x4000 in ./ibdata1

so i have tried to remove mariadb unsuccesfully and i am now stuck in what looks like a mutual dependency issue:

[/FONT]```

sudo apt-get upgrade


Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 dbconfig-mysql : Depends: default-mysql-client or
                           virtual-mysql-client
 mariadb-server : Depends: mariadb-server-10.4 (>= 1:10.4.14+maria~focal) but it is not installed
 mysql-server-8.0 : Depends: mysql-client-8.0 (>= 8.0.21-0ubuntu0.20.04.4) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```[FONT=Lato]

ok, so

[/FONT]```
apt --fix-broken install[FONT=Lato]

[/FONT]Preconfiguring packages ...
dpkg: mysql-server-8.0: dependency problems, but removing anyway as you requested:
 plesk-mysql-server depends on mariadb-server | virtual-mysql-server; however:
  Package mariadb-server is not configured yet.
  Package virtual-mysql-server is not installed.
  Package mysql-server-8.0 which provides virtual-mysql-server is to be removed.
  Package mysql-server-5.7 which provides virtual-mysql-server is not installed.
  Package mariadb-server-10.3 which provides virtual-mysql-server is not installed
.
 plesk-mysql-server depends on mariadb-server | virtual-mysql-server; however:
  Package mariadb-server is not configured yet.
  Package virtual-mysql-server is not installed.
  Package mysql-server-8.0 which provides virtual-mysql-server is to be removed.
  Package mysql-server-5.7 which provides virtual-mysql-server is not installed.
  Package mariadb-server-10.3 which provides virtual-mysql-server is not installed
.
 plesk-mysql-server depends on mariadb-server | virtual-mysql-server; however:
  Package mariadb-server is not configured yet.
  Package virtual-mysql-server is not installed.
  Package mysql-server-8.0 which provides virtual-mysql-server is to be removed.
  Package mysql-server-5.7 which provides virtual-mysql-server is not installed.
  Package mariadb-server-10.3 which provides virtual-mysql-server is not installed
.
 plesk-mysql-server depends on mariadb-server | virtual-mysql-server; however:
  Package mariadb-server is not configured yet.
  Package virtual-mysql-server is not installed.
  Package mysql-server-8.0 which provides virtual-mysql-server is to be removed.
  Package mysql-server-5.7 which provides virtual-mysql-server is not installed.
  Package mariadb-server-10.3 which provides virtual-mysql-server is not installed
.


dpkg: error processing package mysql-server-8.0 (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
dpkg: too many errors, stopping
Errors were encountered while processing:
 mysql-server-8.0
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

[FONT=Lato]and finally

[/FONT]```
sudo apt-get --reinstall install mysql-server-8.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 dbconfig-mysql : Depends: default-mysql-client or
                           virtual-mysql-client
 mariadb-server : Depends: mariadb-server-10.4 (>= 1:10.4.14+maria~focal) but it is not going to be installed
 mysql-server-8.0 : Depends: mysql-client-8.0 (>= 8.0.21-0ubuntu0.20.04.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```[FONT=Lato]

Basically, whatever i try to install or remove i keep ending inside his loop and of course i can't run any mysql or mariadb server and my website is down since 24 hours now.

Please help![/FONT]

---

### Post by darkod on 2020-10-06
OK, I know you are in panic but that's the worst way to work on a server...

I don't know much about plesk but if this message is true, why do you keep trying to work with mysql-server instead of mariadb-server?
```
plesk-mysql-server depends on mariadb-server
```

That message would tell me plesk wants mariadb, not mysql.

Also, with such mixed interdependencies, I wouldn't try to fix them with apt-get. First make sure you know and understand which packages you need to keep (mariadb for example) and then I would try to remove packages like mysql-server by dpkg and using --force is necessary.

You can clean up other dependencies later, I see more important here to figure our which database server package you need to use for plesk and to get rid of the other one directly with dpkg (which doesn't take dependencies in count in some cases).

And just to clarify your first sentence, you did dist-upgrade or do-release-upgrade? Because saying you did "dist-upgrade to 20.04" makes no sense. dist-upgrade does not upgrade ubuntu from one version to another. It only upgrades packages to their latest version.

---

### Post by LHammonds on 2020-10-06
I am not familiar with Plex either.  If they changed from MySQL backend to MariaDB, it is no longer a drop-in replacement.  Meaning you cannot uninstall MySQL and install MariaDB on top of the databases that were there and expect it to work.  If this scenario needs to happen, you HAVE TO get MySQL running again and export the databases, users/grants to .sql files.  Then completely remove MySQL and its databases/configs.  The install a fresh/clean install of MariaDB and import the databases and then users/grants.

Or, if you already have the database backups to .sql files (including the users/grants) then you proceed to purging MySQL.

EDIT: [Related topic](https://ubuntuforums.org/showthread.php?t=2451195)

LHammonds

---


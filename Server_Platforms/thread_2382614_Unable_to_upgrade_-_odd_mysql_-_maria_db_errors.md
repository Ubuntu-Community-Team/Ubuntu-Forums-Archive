---
title: "Unable to upgrade - odd mysql - maria db errors"
date: 2018-01-15
forum: Server Platforms
---

### Post by amcorona on 2018-01-15
Attempting to update all packages on a production server.  Seeing the following:
This is 14.04 and I am new here. First time I had a problem like this.
```
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 68964 files and directories currently installed.)
Preparing to unpack .../mariadb-server-5.5_5.5.58-1ubuntu0.14.04.1_amd64.deb ...
 * Stopping MariaDB database server mysqld                                                                                                                  [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
 * Stopping MariaDB database server mysqld                                                                                                                  [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/mariadb-server-5.5_5.5.58-1ubuntu0.14.04.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MariaDB database server mysqld                                                                                                                  [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MariaDB database server mysqld                                                                                                                  [ OK ] 
dpkg: considering deconfiguration of mariadb-server-5.5, which would be broken by installation of mariadb-client-5.5 ...
dpkg: yes, will deconfigure mariadb-server-5.5 (broken by mariadb-client-5.5)
Preparing to unpack .../mariadb-client-5.5_5.5.58-1ubuntu0.14.04.1_amd64.deb ...
De-configuring mariadb-server-5.5 (5.5.54-1ubuntu0.14.04.1) ...
 * Stopping MariaDB database server mysqld                                                                                                                  [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/mariadb-client-5.5_5.5.58-1ubuntu0.14.04.1_amd64.deb (--unpack):
 subprocess installed pre-removal script returned error exit status 1
 * Stopping MariaDB database server mysqld                                                                                                                  [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
postinst called with unknown argument 'abort-deconfigure'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mariadb-server-5.5_5.5.58-1ubuntu0.14.04.1_amd64.deb
 /var/cache/apt/archives/mariadb-client-5.5_5.5.58-1ubuntu0.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
I have tried sudo apt-get update && sudo apt-get upgrade but afraid to use purge.

I have the following installed:```

mariadb-client-5.5/now 5.5.54-1ubuntu0.14.04.1 amd64 [installed,upgradable to: 5.5.58-1ubuntu0.14.04.1]
mariadb-client-core-5.5/trusty-updates,now 5.5.58-1ubuntu0.14.04.1 amd64 [installed,automatic]
mariadb-common/trusty-updates,now 5.5.58-1ubuntu0.14.04.1 all [installed,automatic]
mariadb-server/now 5.5.54-1ubuntu0.14.04.1 all [installed,upgradable to: 5.5.58-1ubuntu0.14.04.1]
mariadb-server-5.5/now 5.5.54-1ubuntu0.14.04.1 amd64 [installed,upgradable to: 5.5.58-1ubuntu0.14.04.1]
mariadb-server-core-5.5/trusty-updates,now 5.5.58-1ubuntu0.14.04.1 amd64 [installed,automatic]

```
and

```
mysql-common/trusty-updates,now 5.5.58-0ubuntu0.14.04.1 all [installed,automatic]
```

---

### Post by slickymaster on 2018-01-15
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2018-01-15
I've seen this before but because I tried so many things to correct it, I cannot remember what it was that solved it (didn't write it down like I usually do).

I think I ended up just backing up the databases, uninstalling MySQL (MariaDB), then doing the OS updates, installed MySQL again and then restored the databases.

If you have upgraded the database engine to different versions over time, the databases might be getting krusty too.  I didn't see the exact error message in your logs as I have on mine for this but you might want to run "mysql_upgrade" once you get your database engine running again.  Reference: [Migrate Database from Old Server](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=225#p548)

LHammonds

---


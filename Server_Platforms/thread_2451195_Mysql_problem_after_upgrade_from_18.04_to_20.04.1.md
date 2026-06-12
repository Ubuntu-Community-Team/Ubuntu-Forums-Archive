---
title: "Mysql problem after upgrade from 18.04 to 20.04.1"
date: 2020-09-29
forum: Server Platforms
---

### Post by ahbart on 2020-09-29
I finally decided to upgrade my Ubuntu server from 18.04 to 20.04.1 with a do-release-upgrade.
This was a big mistake!

No there is a Mysql problem:
```

sudo apt list --installed |grep mysql
dbconfig-mysql/focal,focal,now 2.0.13 all [installed,automatic]
default-mysql-client/focal,focal,now 1.0.5ubuntu2 all [installed,automatic]
libdbd-mysql-perl/focal,now 4.050-3 amd64 [installed]
libmysqlclient20/now 5.7.31-0ubuntu0.18.04.1 amd64 [installed,local]
libmysqlclient21/focal-updates,focal-security,now 8.0.21-0ubuntu0.20.04.4 amd64 [installed,automatic]
mysql-client-8.0/focal-updates,focal-security,now 8.0.21-0ubuntu0.20.04.4 amd64 [installed,automatic]
mysql-client-core-8.0/focal-updates,focal-security,now 8.0.21-0ubuntu0.20.04.4 amd64 [installed,automatic]
mysql-common/focal,focal,now 5.8+1.0.5ubuntu2 all [installed]
mysql-server-8.0/focal-updates,focal-security,now 8.0.21-0ubuntu0.20.04.4 amd64 [installed,automatic]
mysql-server-core-8.0/focal-updates,focal-security,now 8.0.21-0ubuntu0.20.04.4 amd64 [installed,automatic]
mysql-server/focal-updates,focal-updates,focal-security,focal-security,now 8.0.21-0ubuntu0.20.04.4 all [installed]

```

systemctl -xe:
```
Sep 29 11:52:21 server.net systemd[1]: Failed to start MySQL Community Server.
```
It looks to me that something went wrong in the upgrade. There are different versions of mysql packages installed as you can see. 5.7 5.8 and 8.0.
I'm having problems fixing this. Someone could help me out here please?!

Edit:
continuing struggling with this.
I installed mysql-apt-config_0.8.15-1_all.deb from mysql.com and so the repo.
After that I now have only mysql 8.0 packages, but still the mysql server does not start. 

```
sudo systemctl status mysql.service
&#9679; mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2020-09-29 12:21:51 CEST; 17s ago
       Docs: man:mysqld(8)
             http://dev.mysql.com/doc/refman/en/using-systemd.html
    Process: 59003 ExecStartPre=/usr/share/mysql-8.0/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
    Process: 59055 ExecStart=/usr/sbin/mysqld (code=exited, status=1/FAILURE)
   Main PID: 59055 (code=exited, status=1/FAILURE)
     Status: "Server startup in progress"

Sep 29 12:21:49 server.net systemd[1]: Starting MySQL Community Server...
Sep 29 12:21:51 server.net systemd[1]: mysql.service: Main process exited, code=exited, status=1/FAILURE
Sep 29 12:21:51 server.net systemd[1]: mysql.service: Failed with result 'exit-code'.
Sep 29 12:21:51 server.net systemd[1]: Failed to start MySQL Community Server.
```

Is this a incompatibility in the database? Should the database been converted during upgrade?
Ooh I'm tearing my hair out!

---

### Post by ahbart on 2020-09-29
I managed to restart the database server!!! But ...
When I commented out:
```
#innodb_large_prefix=true
#innodb_file_format=barracuda
#innodb_file_per_table=1
```
from: /etc/mysql/mysql.conf.d/mysqld.cnf
The server is starting up. 
But I was using this setting for Nextcloud. Is there a another way to enable this?

edit:
I notice that Nextcloud is not complaining about this. So maybe this is not necessary any more.

---

### Post by LHammonds on 2020-09-29
When upgrading database versions, be sure to upgrade your database schema by running this command after updating the database engine:

```
mysql_upgrade
```

I avoid such issues by installing the server from a fresh start (e.g. Ubuntu Server 20.04) and then install the current database engine (e.g. MariaDB 10.5.5).

Then import the .sql files from the mysqldump on the old server.  I avoid the "all databases" dump file in such a situation because I want to avoid the old "mysql" databases that come with the system.  I just import the user databases and the associated users/grants.

LHammonds

---

### Post by ahbart on 2020-09-30
Thank you LHammonds,
I assume that the 'conversion' had taken place, but in my case the problem was the different versions of mysql, mysql-server, mysql-common and -client, and the configuration items innodb in mysqld.cnf.
At least that fixed the issue. Bit I'm not sure about the real cause en what solved it.

---

### Post by LHammonds on 2020-09-30
Was everything originally installed from the official repositories or did you have .deb manual installs or compiled from source code?

If everything was installed from repository, version incompatibility issues in components are rare.  Also, config files if not reviewed over time can contain deprecated references and missing new options.  Always to compare your old config to the current default to see if any adjustments need to be made.

I have not run MySQL proper since the original devs moved over to MariaDB so I am not familiar with changes in MySQL over time (it was VERY static when Oracle took it over...thus the move to MariaDB)

LHammonds

---

### Post by ahbart on 2020-09-30
I only install from repo on my server. Not even from ppa before. There was a warning about phpmyadmin during upgrade. I skipped it, assuming I could fix that later. But I was not aware of any other problem with mysql packages. 
I used mariadb before. Is it possible to replace Mysql and replace it with mariadb? Without breaking the system? ;)

---

### Post by LHammonds on 2020-09-30
> **ahbart said:**
> Is it possible to replace Mysql and replace it with mariadb? Without breaking the system? ;)
MariaDB is a "drop-in" replacement.  Meaning that if you uninstall MySQL, then install MariaDB, your databases should just work.  Make sure you know where the databases are living though.  I think the default location is /var/lib/mysql but it might be different.  I move mine under /opt and have to reference that in the .cnf file.

I have not done it recently but when I did the switch, it was quite painless.  It was a version jump so I needed to do the "mysql_upgrade" command.

But as always, before doing such a change, make sure you have the mysqldump exports of each database and also pull out the users/grants which are contained in the "mysql" system database.

I export my user grants like this:

```
mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT CONCAT('SHOW GRANTS FOR ''',user,'''@''',host,''';') FROM mysql.user WHERE user<>''" | sort | mysql --skip-column-names --no-auto-rehash | sed 's/$/;/g' > /tmp/db-grants.sql
```

I export each user database into it's own .sql file (I avoid the "all databases" backup to a single .sql file because I don't want to include the system databases)
```

mysqldump userdb1 > /tmp/userdb1.sql
mysqldump userdb2 > /tmp/userdb2.sql
mysqldump userdb3 > /tmp/userdb3.sql

```

I also export the system databases for restore of the exact same system but when migrating, I do not import system databases.

The only thing I really have in the system databases are the grants so this would be enough for me.  If you have stored procedures, roles, etc. you may need to export those in your backup to ensure you have everything.

LHammonds

---

### Post by ahbart on 2020-09-30
hmm. another problem. 
I made some backups. etc.
Then apt install mariadb-client mariadb-server mariadb-common 
automatically mysql packages where removed. 
It looked good.
But now mysql won't start:
```
Sep 30 15:32:53 server.net mysqld[133129]: 2020-09-30 15:32:53 0 [Note] InnoDB: Starting shutdown...
Sep 30 15:32:54 server.net mysqld[133129]: 2020-09-30 15:32:54 0 [ERROR] Plugin 'InnoDB' init function returned error.
Sep 30 15:32:54 server.net mysqld[133129]: 2020-09-30 15:32:54 0 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
Sep 30 15:32:54 server.net mysqld[133129]: 2020-09-30 15:32:54 0 [Note] Plugin 'FEEDBACK' is disabled.
Sep 30 15:32:54 server.net mysqld[133129]: 2020-09-30 15:32:54 0 [ERROR] Could not open mysql.plugin table. Some plugins may be not loaded
Sep 30 15:32:54 server.net mysqld[133129]: 2020-09-30 15:32:54 0 [ERROR] Unknown/unsupported storage engine: InnoDB
Sep 30 15:32:54 server.net mysqld[133129]: 2020-09-30 15:32:54 0 [ERROR] Aborting
Sep 30 15:32:54 server.net systemd[1]: mariadb.service: Main process exited, code=exited, status=1/FAILURE
Sep 30 15:32:54 server.net systemd[1]: mariadb.service: Failed with result 'exit-code'.
Sep 30 15:32:54 server.net systemd[1]: Failed to start MariaDB 10.3.22 database server.
```
again something with innodb? Any help is very welcome!

---

### Post by CelticWarrior on 2020-09-30
[https://websiteforstudents.com/switch-from-mysql-to-mariadb-10-2-database-on-ubuntu-16-04-lts-server/](https://websiteforstudents.com/switch-from-mysql-to-mariadb-10-2-database-on-ubuntu-16-04-lts-server/)

> [COLOR=#000000]Then apt install mariadb-client mariadb-server mariadb-common[/COLOR]
[COLOR=#000000]automatically mysql packages where removed.[/COLOR]
[COLOR=#000000]It looked good.[/COLOR]

No, it didn't.
The comment above and this link show why it didn't and it couldn't.

---

### Post by ahbart on 2020-09-30
I do not really understand what you mean. The comments under article show that the database is not converted? 
But is it possible to continue with mariadb, or should I better go back to mysql 8.0?

Edit:
I went back to mysql 8.0.
It is not as easy as I hoped for. Maybe I will find a good tutorial. 
Thank you all. If you have a suggestion how go to mariadb, you're welcome!!!

---

### Post by ahbart on 2020-10-01
hmm. I did some experiments trying to migrate from Mysql 8.0 to mariadb 10.3, 10.4 or 10.5. 
Without success. 
I've found this post on [cPanel Forum]("https://forums.cpanel.net/resources/how-to-install-mariadb-10-3-in-favor-of-mysql-8-0.729/").
I do not use cPanel, but this article suggestes that migrating is possible. 

with this script:```
#!/bin/bash
mysql -ANe "SELECT schema_name FROM information_schema.schemata WHERE schema_name NOT IN ('mysql','information_schema','performance_schema', 'sys')" > databases.txt

DBLIST=""
for DB in `cat databases.txt` ; do DBLIST="${DBLIST} ${DB}" ; done

MYSQLDUMP_OPTIONS="--routines --triggers --single-transaction"
mysqldump ${MYSQLDUMP_OPTIONS} --databases ${DBLIST} > all-dbs.sql
```
I am able to create a database backup.
I created a dump of the user table of the mysql database as an user.sql file.
Is there a way to restore my different databases with these two files?

---

### Post by LHammonds on 2020-10-01
The 1st line gets a list of all databases that are NOT system databases.  Essentially, it issues the "show databases" command but strips out the system databases so you just have a list of user databases.
The "for" loop cleans up the output and the mysqldump creates a single .sql file of all your user databases.

You can test this out using a virtual machine on your PC (e.g. VirtualBox) to install MariaDB and import the "all-dbs.sql" file and then the "user.sql" file.

What seems to be the issue with the drop-in update has to do with your settings...which seem to have also caused issue with MySQL.

I would uninstall everything mysql, then rename/move the config files and the database files to a backup location so they are NOT found when you install MariaDB.

After installing MariaDB and verify there are no residual issues from the prior install.

Start and stop the database service:
```

sudo systemctl stop mysql
sudo systemctl start mysql

```

Check the logs to ensure nothing is wrong:
```
tail -n50 /var/log/mysql/mariadb.err
```

Run some basic queries such as:
```

mysql -e "SHOW DATABASES;"
mysql -e "SELECT user,host FROM mysql.user;"

```

Once you are satisfied that MariaDB is working fine, then import the databases and users.  Here is how I import large .sql files and avoid creating an unnecessary log:

```

mysql
SET sql_log_bin = 0;
source /tmp/all-dbs.sql
source /tmp/user.sql
exit

```

You have me curious enough though that I will probably install MySQL 8, create a sample database and user and see if uninstalling MySQL and then MariaDB 10.5.5 will work as a drop-in replacement.  If not, I don't want to get caught recommending something that is no longer true.

LHammonds

---

### Post by ahbart on 2020-10-01
Thank you LHammonds,
This time I test with an new virtual server but same Ubuntu 20.04.
Mariadb 10.3
As soon as I import the both databases and restart the mysql server I get an:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```
(I had to switch to the mysql database to import the user table. Is it not?)
This is same kind of error I get about /var/run/mysqld/mysqld.sock as on the VPS. 
Suggestions?

Edit: When I update Mariadb to 10.5 I get the mysql database up and running! 
I will try this later on the VPS!

---

### Post by LHammonds on 2020-10-01
MariaDB 10.5 is the current [stable version for Ubuntu 20.04]("https://downloads.mariadb.org/mariadb/repositories/#distro=Ubuntu&distro_release=focal--ubuntu_focal&mirror=digitalocean-nyc") and what I'd recommend going using.  I happen to be installing MySQL 8.0 right now to test the drop-in ability.

NOTE: The 1st 14 lines in the user.sql should not be needed for importing into the MariaDB database (default install of MySQL 8.0).  Those are system accounts which won't be needed on an existing/working server so be sure to remove those before import.  Line 15 "should" be the 1st user account you added but make sure.

---

### Post by LHammonds on 2020-10-01
TEST #1 - Install MySQL 8, create a database and user.  Export to .sql.  Then remove MySQL 8, install MariaDB 10.5, import the .sql to restore the database and user.
TEST #1 - Success....see steps performed below:

```

administrator@ubuntu:~$ sudo su
root@ubuntu:/# apt install mysql-server mysql-client mysql-common
root@ubuntu:/# mysql_secure_installation
root@ubuntu:/# mysql
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
SELECT user,host FROM mysql.user;
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| debian-sys-maint | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
+------------------+-----------+
CREATE DATABASE test CHARACTER SET utf8 COLLATE utf8_bin;
CREATE USER 'u_test'@'localhost' IDENTIFIED BY 'abcd1234';
GRANT SELECT,INSERT,UPDATE,DELETE ON test.* to 'u_test'@'localhost';
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test               |
+--------------------+
SELECT user,host FROM mysql.user;
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| debian-sys-maint | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
| u_test           | localhost |
+------------------+-----------+
exit
 root@ubuntu:/# mysqldump --databases test > /tmp/all-dbs.sql
root@ubuntu:/# mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT CONCAT('SHOW GRANTS FOR ''',user,'''@''',host,''';') FROM mysql.user WHERE user<>''" | sort | mysql --skip-column-names --no-auto-rehash | sed 's/$/;/g' > /tmp/user.sql
vi /tmp/user.sql                     <--- NOTE: I cleaned up the output by removing the system accounts which are not needed in this case.
root@ubuntu:/#systemctl stop mysql
root@ubuntu:/# apt purge mysql-server mysql-client mysql-common
root@ubuntu:/# apt autoremove
root@ubuntu:/# rm -rf /etc/mysql
root@ubuntu:/# mv /var/lib/mysql /tmp/mysql.old
root@ubuntu:/# apt-key adv --fetch-keys 'https://mariadb.org/mariadb_release_signing_key.asc'
root@ubuntu:/# add-apt-repository 'deb [arch=amd64,arm64,ppc64el] http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.5/ubuntu focal main'
root@ubuntu:/# apt update
root@ubuntu:/# apt upgrade
root@ubuntu:/# apt install mariadb-server mariadb-client mariadb-common
root@ubuntu:/# tail -n50 /var/log/mysql/mariadb.err
tail: cannot open '/var/log/mysql/mariadb.err' for reading: No such file or directory
root@ubuntu:/# mysql_secure_installation
root@ubuntu:/# mysql
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
SELECT user,host FROM mysql.user;
+-------------+-----------+
| User        | Host      |
+-------------+-----------+
| mariadb.sys | localhost |
| mysql       | localhost |
| root        | localhost |
+-------------+-----------+
SET sql_log_bin = 0;
source /tmp/all-dbs.sql
source /tmp/user.sql
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| test               |
+--------------------+
SELECT user,host FROM mysql.user;
+-------------+-----------+
| User        | Host      |
+-------------+-----------+
| mariadb.sys | localhost |
| mysql       | localhost |
| root        | localhost |
| u_test      | localhost |
+-------------+-----------+
SHOW GRANTS FOR u_test@localhost;
+---------------------------------------------------------------------------------------------------------------+
| Grants for u_test@localhost                                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO `u_test`@`localhost` IDENTIFIED BY PASSWORD '*4AD47E08DAE2BD4F0977EED5D23DC901359DF617' |
| GRANT SELECT, INSERT, UPDATE, DELETE ON `test`.* TO `u_test`@`localhost`                                      |
+---------------------------------------------------------------------------------------------------------------+

```

---

### Post by LHammonds on 2020-10-01
TEST #2 - Install MySQL 8, create a database and user. Remove MySQL 8, install MariaDB 10.5 on top of the prior left-over files.

TEST #2 - Drop-in replacement Failure

```
administrator@ubuntu:~$ sudo su
root@ubuntu:/# apt install mysql-server mysql-client mysql-common
root@ubuntu:/# mysql_secure_installation
root@ubuntu:/# mysql
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
SELECT user,host FROM mysql.user;
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| debian-sys-maint | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
+------------------+-----------+
CREATE DATABASE test CHARACTER SET utf8 COLLATE utf8_bin;
CREATE USER 'u_test'@'localhost' IDENTIFIED BY 'abcd1234';
GRANT SELECT,INSERT,UPDATE,DELETE ON test.* to 'u_test'@'localhost';
SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test               |
+--------------------+
SELECT user,host FROM mysql.user;
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| debian-sys-maint | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
| u_test           | localhost |
+------------------+-----------+
exit
root@ubuntu:/# systemctl stop mysql
root@ubuntu:/# apt purge mysql-server mysql-client mysql-common
root@ubuntu:/# apt autoremove
root@ubuntu:/# apt-key adv --fetch-keys 'https://mariadb.org/mariadb_release_signing_key.asc'
root@ubuntu:/# add-apt-repository 'deb [arch=amd64,arm64,ppc64el] http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.5/ubuntu focal main'
root@ubuntu:/# apt update
root@ubuntu:/# apt upgrade
root@ubuntu:/# apt install mariadb-server mariadb-client mariadb-common

WARNING about /var/lib/mysql being renamed to /var/lib/mysql-8.0 due to bin-log format.


```

Because it moved the old database repository, it therefore did not pull in the old databases.

You have to change the system from binlog format BEFORE replacing with MariaDB at a minimum...but if you have .sql backup files, you can just use those to restore the databases as noted above.

So, I now know I cannot say MariaDB is a "drop-in" replacement because of this.  I think how roles are defined/used are different as well and may not translate well either.  MariaDB came up with roles first and MySQL implemented later but in a different way.

It was a good exercise.  I should have guessed they would not work like when they first diverged.  Too many changes on both sides for them to be perfect matches anymore.  And just like with upgrading a database of the same engine to a much higher version number, it is still best to export the database and users into .sql format and import them cleanly.

LHammonds

---

### Post by ahbart on 2020-10-02
LHammonds, This is absolutely excellent and very interesting. I will do some testing today! Thank you.

---

### Post by ahbart on 2020-10-02
hmm. No. a lots off error then when I source import te user sql. Created as you did.
```
ERROR 1064 (42000) at line 1 in file: '/home/bart/backup/database/2020-10-02-user.sql': You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'ROLE, DROP ROLE ON *.* TO `bart`@`%` WITH GRANT OPTION' at line 1
ERROR 1064 (42000) at line 2 in file: '/home/bart/backup/database/2020-10-02-user.sql': You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'AUDIT_ADMIN,BACKUP_ADMIN,BINLOG_ADMIN,BINLOG_ENCRYPTION_ADMIN,CLONE_ADMIN,CON...' at line 1
Query OK, 0 rows affected (0.002 sec)

```
What is this error and do you know how to fix this? I did not have this on the virtual machine.

I managed to import the users. It looks like I had to use mysql; But I'm not sure about that. 
The users where imported. 
But all the user passwords where lost. I was able to login to phpmyadmin with root and fix these passwords again.
Now everything is up and running.

I notice that there are several system users: mariadb.sys mysql.infoschema mysql.session mysql.sys
Is there a user between these that is mysql specific what I could drop/delete?
Is it right that these users have no passwords?

---

### Post by LHammonds on 2020-10-02
> **ahbart said:**
> 
```
ERROR 1064 (42000) at line 1 in file: '/home/bart/backup/database/2020-10-02-user.sql': You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'ROLE, DROP ROLE ON *.* TO `bart`@`%` WITH GRANT OPTION' at line 1
```

Notice the word "role" here?  As I noted earlier, roles did not exist in mysql when mariadb split in a different direction.  MariaDB came up with roles 1st and years later MySQL implemented the "idea" but in a different way...and as such, cannot be directly exported/imported.

You can analyze how the roles work in MySQL and re-create a similar function in MariaDB though but you need to understand how they work in both engines and the differences between them.  [Let's compare MariaDB and MySQL Roles.pdf]("https://mariadb.org/wp-content/uploads/2020/02/Lets-compare-MariaDB-and-MySQL-Roles.pdf")

> **ahbart said:**
> 
```
ERROR 1064 (42000) at line 2 in file: '/home/bart/backup/database/2020-10-02-user.sql': You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'AUDIT_ADMIN,BACKUP_ADMIN,BINLOG_ADMIN,BINLOG_ENCRYPTION_ADMIN,CLONE_ADMIN,CON...' at line 1
```

AUDIT_ADMIN?
BACKUP_ADMIN?
BINLOG_ADMIN?

Are those your user accounts or accounts related to the MySQL engine? Maybe those are roles being assigned to a single account. I did not document what users exist in a base install of MySQL while it was up but those do NOT need to be imported into a working MariaDB installation which already has its own and working system accounts.  In fact, you don't want to cross those over since it very-likely will break MariaDB if it did.

I prefix all my users with "u_" and all my roles with "r_" and as such, I never get them mixed up with system accounts which I never mess with.

> **ahbart said:**
> What is this error and do you know how to fix this? I did not have this on the virtual machine.
That error is talking about syntax problems.  Likely related to the role.  But without seeing it, I cannot say.  Again, a syntax error means there is a feature/command in the SQL that was used during the dump that does not exist during the import (an engine difference).  I am also assuming you did not make any edits/changes to the .sql file.  If you did, you might have goofed something in there such as a missing semicolon.

> **ahbart said:**
> I managed to import the users. It looks like I had to use mysql; But I'm not sure about that.
Make sure that you not only imported the users but also their grants/privileges.  The ID is no good if they cannot access the data they are supposed to access.

```
SHOW GRANTS FOR 'user1'@'localhost';
```

If they were part of a role on MySQL, look into the permissions granted to those role(s).  iirc Role in MySQL were cumulative automatically but in MariaDB only 1 active role is allowed at a time but you can configure inheritance.

> **ahbart said:**
> But all the user passwords where lost.This should not have happened...but, I did not verify that field in my test.  Should be fairly easy to see if the password hash is included in the user.sql file.  At the very least, you can run this command to verify the passwords are identical (even if hashed) on both systems:

```
SELECT user,host,password FROM mysql.user ORDER BY user ASC;
```

LHammonds

---

### Post by ahbart on 2020-10-02
Thank you LHammonds, I do not see this AUDIT_ADMIN, BACKUP_ADMIN, BINLOG_ADMIN in the user table now. So it might is a role. I'm using the database from Nextcloud, Wordpress, (Joomla), PhPMyAdmin, Roundcube and spamassassin. It looks like everything is working again, but I assume that thit is more my luck then wisdom. 
The migration from MySQL 8.0 to Mariadb 10.5 is in my opinion not as smooth as it was from earlier versions of MySQL. But of what I've read on internet, also that is as expected. 
Thanks again!

---

### Post by LHammonds on 2020-10-02
Yes, it used to be deadpan simple, uninstall MySQL and install MariaDB since at once point they were 100% compatible but that is becoming less and less the case so I will be more careful about recommending migrations from MySQL.  I still think MariaDB is the superior product of the two.

Glad you got it working.

**EDIT:** Please edit the thread title and change it to [SOLVED] in the dropdown.

LHammonds

---


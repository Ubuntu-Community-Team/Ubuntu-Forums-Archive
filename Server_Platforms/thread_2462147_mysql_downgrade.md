---
title: "mysql downgrade"
date: 2021-05-14
forum: Server Platforms
---

### Post by pawelzaw on 2021-05-14
Hi.
Two days ago my Ubuntu 20.04 LTS Focal Fossa upgrade sql from 8.0.23 to 8.0.25. I don't know how this happens. After update server stops working logs : 
```
mysqld[2382626]: 2021-05-14T07:58:44.203429Z 4 [System] [MY-013381] [Server] Server upgrade from '80023' to '80025' started.
[Server] Execution of server-side SQL statement 'ALTER TABLE user   MODIFY max_updates int unsigned DEFAULT 0 NOT NULL,   MODIFY max_connections int unsigned DEFAULT 0 NOT NULL,   MODIFY max_user_connections int unsigned DEFAULT 0  NOT NULL,   MODIFY ssl_cipher BLOB NOT NULL,   MODIFY x509_issuer BLOB NOT NULL,   MODIFY x509_subject BLOB NOT NULL; ' failed with error code = 1138, error message = 'Invalid use of NULL value'.
mysqld[2382772]: 2021-05-14T07:59:36.690598Z 0 [ERROR] [MY-013380] [Server] Failed to upgrade server.
mysqld[2382772]: 2021-05-14T07:59:36.691077Z 0 [ERROR] [MY-010119] [Server] Aborting
amoniak mysqld[2382772]: 2021-05-14T07:59:40.539655Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.25-0ubuntu0.20.04.1)  (Ubuntu).
```
Is there any way to downgrade back to 8.0.23. I have backup of /var/lib/mysql so I just can install fresh copy of 8.0.23 stops server replace all /var/lib/mysql  from my backup and start working server again.
Or maybe there is so smart way to run this on 8.0.25 ?

---

### Post by CharlesA on 2021-05-14
You should fix the cause of the error, which seems to stem from the user table, which should hold any mysql database users. That seems pretty strange.

EDIT: Found someone else with a similar issue to yours, but they didn't have a resolution to it. You can find their thread here: [https://stackoverflow.com/questions/67492214/mysql-server-not-starting-server-side-sql-bad-statement-corrupted-table-cpane](https://stackoverflow.com/questions/67492214/mysql-server-not-starting-server-side-sql-bad-statement-corrupted-table-cpane)



In any case, you can check to see which versions of mysql-server are out there via this command:
```

apt-cache madison mysql-server

```

Then install the version you want. via:
```

sudo apt install my-sqlserver=version

```

Where version is the version returned from the apt-cache command.

---

### Post by LHammonds on 2021-05-15
If you have backups, I would uninstall MySQL, delete (or move) the existing data files.  The install a fresh current version of MySQL and restore your data from backup.

I would not trust the current data if suspected as corrupted.  I would restore if that is a viable option.  Last resort, I'd try fixing the data.

LHammonds

---

### Post by in2dave on 2021-05-16
> **pawelzaw said:**
> Hi.
Two days ago my Ubuntu 20.04 LTS Focal Fossa upgrade sql from 8.0.23 to 8.0.25. I don't know how this happens. After update server stops working logs : 
```
mysqld[2382626]: 2021-05-14T07:58:44.203429Z 4 [System] [MY-013381] [Server] Server upgrade from '80023' to '80025' started.
[Server] Execution of server-side SQL statement 'ALTER TABLE user   MODIFY max_updates int unsigned DEFAULT 0 NOT NULL,   MODIFY max_connections int unsigned DEFAULT 0 NOT NULL,   MODIFY max_user_connections int unsigned DEFAULT 0  NOT NULL,   MODIFY ssl_cipher BLOB NOT NULL,   MODIFY x509_issuer BLOB NOT NULL,   MODIFY x509_subject BLOB NOT NULL; ' failed with error code = 1138, error message = 'Invalid use of NULL value'.
mysqld[2382772]: 2021-05-14T07:59:36.690598Z 0 [ERROR] [MY-013380] [Server] Failed to upgrade server.
mysqld[2382772]: 2021-05-14T07:59:36.691077Z 0 [ERROR] [MY-010119] [Server] Aborting
amoniak mysqld[2382772]: 2021-05-14T07:59:40.539655Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.25-0ubuntu0.20.04.1)  (Ubuntu).
```
Is there any way to downgrade back to 8.0.23. I have backup of /var/lib/mysql so I just can install fresh copy of 8.0.23 stops server replace all /var/lib/mysql  from my backup and start working server again.
Or maybe there is so smart way to run this on 8.0.25 ?

I've recently encountered the exact same problem - running a straightforward **apt update**, **apt upgrade** resulted in the above messages appearing.  The issue seems to be with a new SQL statement trying to be executed which fails - this must be something introduced within the upgrade process (my old version of MySQL was 8.0.23)

Causing no end of problems, in that if I try to start mysql, the process runs, but there's no .sock file to connect to, so unable to make a connection to the server :(
Also, there seems to be no way to prevent this ALTER TABLE statement from running.....

Any clues?

---

### Post by LHammonds on 2021-05-16
Can you switch to MariaDB?  The original developers of MySQL jumped ship some time after Oracle took over and created MariaDB out of frustration with Oracle.

LHammonds

---

### Post by pawelzaw on 2021-05-16
Hi.
I manage to fix it sort of :/ I had a backup but it contains /var/lib/mysql directory not sqldump so this is what I do :

1. I download MySQL in version 8.0.23  from here [https://downloads.mysql.com/archives/community/](https://downloads.mysql.com/archives/community/) 
2. I install this version on my debian local pc 
3. after install I stop server rename /var/lib/mysql and copy files from backup top /var/lib/mysql
4. after start mysql everything works all database was accessible 
5. I do mysqldump -u root -p --flush-privileges --add-drop-table --routines --all-databases > backup.sql 
6. I log to my server remove /var/lib/mysql and install version 8.0.25
7. In the end I just recover backup from point 5 and everything starts working 

unfortunately  apt-cache madison mysql-server shows only 8.0.19 and  8.0.25 

I don't try copy /var/lib/mysql to my local server after this update starts I had a backup from 8.0.23 so if someone else will have this issue I cant guarantee this trick works on files between  8.0.23 and  8.0.25

I try to create empty database stop server and move only /var/lib/mysql/roundcubemail/ to 8.0.25 but it contains only *.ibd and after start database was empty. On mariadb I can see database just after copy directory to /var/lib/mysql/roundcubemail/ but database was empty don't contain any tables.

There is one important question how this server was updated ? I check logs no one was log in when this update was done and in /var/cache/apt/archives/ was only dpkg from mysql. I there any auto update in ubuntu ?

---

### Post by CharlesA on 2021-05-16
> **in2dave said:**
> I've recently encountered the exact same problem - running a straightforward **apt update**, **apt upgrade** resulted in the above messages appearing.  The issue seems to be with a new SQL statement trying to be executed which fails - this must be something introduced within the upgrade process (my old version of MySQL was 8.0.23)

Causing no end of problems, in that if I try to start mysql, the process runs, but there's no .sock file to connect to, so unable to make a connection to the server :(
Also, there seems to be no way to prevent this ALTER TABLE statement from running.....

Any clues?

No clue here, but that's pretty bizarre. Did you try to open a bug report in Ubuntu ([https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)) or mySQL itself ([https://bugs.mysql.com/)?](https://bugs.mysql.com/)?)

> **pawelzaw said:**
> 
There is one important question how this server was updated ? I check logs no one was log in when this update was done and in /var/cache/apt/archives/ was only dpkg from mysql. I there any auto update in ubuntu ?

The dpkg log should be the one you want, but that really only shows what packages were update, not if there were any errors during the update.

As far as automatic updates go, you can install the unattended-upgrades package, but that's only going to install security updates for you.

---

### Post by in2dave on 2021-05-17
Managed to "fix" it by remove (purging) existing mysql-* packages, removing /var/lib/mysql and installing mysql-server and dependencies again
Then reimporting all databases previously backed up

It's not a solution per se, but it gets the latest version and all DBs back.

Interestingly I noted that with the failed "upgrade" it tries to start the new X Plugin by using mysqlx.sock, but this stopped the mysqld.sock from running, so I couldn't connect.  Now, with the new install, it's running both mysqlx.sock and mysqld.sock in /var/run/mysqld, so all is well (for now)

Thank heavens for recent backups!!!

---

### Post by CharlesA on 2021-05-17
> **in2dave said:**
> Managed to "fix" it by remove (purging) existing mysql-* packages, removing /var/lib/mysql and installing mysql-server and dependencies again
Then reimporting all databases previously backed up

It's not a solution per se, but it gets the latest version and all DBs back.

Interestingly I noted that with the failed "upgrade" it tries to start the new X Plugin by using mysqlx.sock, but this stopped the mysqld.sock from running, so I couldn't connect.  Now, with the new install, it's running both mysqlx.sock and mysqld.sock in /var/run/mysqld, so all is well (for now)

Thank heavens for recent backups!!!

That makes no sense at all! Glad you were able to get it back into a working state.

---


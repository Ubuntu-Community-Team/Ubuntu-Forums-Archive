---
title: "mysql won't start"
date: 2022-07-30
forum: Server Platforms
---

### Post by edvigil on 2022-07-30
II. SYSTEM INFORMATION

  OS type and version  Ubuntu 22.04
 Webmin version            1.994     
  Virtualmin version        7.1-1   
  
2 months ago I was not able to start Apache server and also mysql server. I was able to fix Apache server by removing directives to php in sites-available -Thanks!
but mysql has me scratching my head.

1. "sudo systemctl status mysql" gives me:

me@ubuntu:~$ sudo systemctl status mysql
[sudo] password for edword:
? mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset:>
     Active: failed (Result: exit-code) since Sat 2022-07-30 05:17:57 MDT; 1h 1>
    Process: 73778 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=>
    Process: 73786 ExecStart=/usr/sbin/mysqld (code=exited, status=1/FAILURE)
   Main PID: 73786 (code=exited, status=1/FAILURE)
     Status: "Server shutdown complete"

Jul 30 05:17:57 ubuntu systemd[1]: mysql.service: Scheduled restart job, restar>
Jul 30 05:17:57 ubuntu systemd[1]: Stopped MySQL Community Server.
Jul 30 05:17:57 ubuntu systemd[1]: mysql.service: Start request repeated too qu>
Jul 30 05:17:57 ubuntu systemd[1]: mysql.service: Failed with result 'exit-code>
Jul 30 05:17:57 ubuntu systemd[1]: Failed to start MySQL Community Server.

2. "mysqladmin ping" gives: 

me@ubuntu:~$ mysqladmin ping
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

3. "/var/log/mysql" gives me:
2022-07-30T11:17:39.782287Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.30-0ubuntu0.20.04.2) starting as process 73492
2022-07-30T11:17:39.864725Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2022-07-30T11:17:42.902203Z 1 [ERROR] [MY-012526] [InnoDB] Upgrade is not supported after a crash or shutdown with innodb_fast_shutdown = 2. This redo log was created with MySQL 8.0.29, and it appears logically non empty. Please follow the instructions at [http://dev.mysql.com/doc/refman/8.0/en/upgrading.html](http://dev.mysql.com/doc/refman/8.0/en/upgrading.html)
2022-07-30T11:17:42.902278Z 1 [ERROR] [MY-012930] [InnoDB] Plugin initialization aborted with error Generic error.
2022-07-30T11:17:43.037545Z 1 [ERROR] [MY-010334] [Server] Failed to initialize DD Storage Engine
2022-07-30T11:17:43.037961Z 0 [ERROR] [MY-010020] [Server] Data Dictionary initialization failed.
2022-07-30T11:17:43.038061Z 0 [ERROR] [MY-010119] [Server] Aborting

Thanks in advance! Off to work.

---

### Post by TheFu on 2022-07-30
Did you do what [http://dev.mysql.com/doc/refman/8.0/en/upgrading.html](http://dev.mysql.com/doc/refman/8.0/en/upgrading.html) says?  Until you do, it won't work.

webmin and virtualmin are useless for non-working stuff.  They are fine, if you have some noob-admins to train, but only if they are setup to be extremely secure and never, ever, allow any external IPs to have access - ever.

---

### Post by edvigil on 2022-07-31
Thanks TheFu! I will try your advice and let you know the result.
Off to work
Eddie

---

### Post by LHammonds on 2022-08-01
Quick question.  Was this ever working on 22.04?   Are these new databases to 22.04 or did you perform some kind of migration from an older version....or in-place (ugg) upgrade?

If you migrated from an older version, did you backup / export all databases and user accounts to .sql files?  Or did you just copy over the raw database files to the new system?

LHammonds

---

### Post by edvigil on 2022-08-04
Thanks LHammonds
Yes, MySQL was working fine. No Migration. Maybe an upgrade was interrupted.  Your question is a little beyond my expertise. 
I don't know what happened that night, but I was unable to start Apache and MySQL servers.
I was able to fix Apache by removing any directives to php in sites-available, but MySQL was still a problem. 
This is what I eventually did to try and fix MySQL. 


Maybe this was a mistake, but this is what I did:

Purge Relevant Packages

    Make sure MySQL is not running:

sudo systemctl stop mysql

    Then purge all of the MySQL packages:

sudo apt purge mysql-server mysql-client mysql-common mysql-server-core-* mysql-client-core-*

    Then delete all of the MySQL files:

sudo rm -rf /etc/mysql /var/lib/mysql /var/log/mysql

    Finally clean all packages that are not needed:

sudo apt autoremove
sudo apt autoclean

    And it never hurts to do a reboot before moving on

sudo reboot

I can now start MySQL, but something is still amiss. My non-Wordpress sites still show up, but my Wordpress sites say "Error establishing a database connection."

Thanks for your help

---

### Post by LHammonds on 2022-08-04
> **edvigil said:**
> 
sudo rm -rf /var/lib/mysql


> **edvigil said:**
> 
my Wordpress sites say "Error establishing a database connection."


Just highlighting the cause / effect parts of what you did.

You in-effect purged the database system and all databases making it a "clean" install....no user databases exist anymore...such as your wordpress database.

You need to restore your wordpress database and re-create your database credentials for the user database.

Well, I hope you have a backup.  Either the wordpress database files themselves or the .sql exported database that you can re-import.  If you have the .sql file, you will need to create the empty database and credentials first, then import the .sql data into that database.

**EDIT**: I know it was not asked but I'll go ahead and recommend migrating to MariaDB from MySQL once you get everything fixed...however, you will need the .sql export from MySQL in order to migrate to MariaDB since they are no longer binary-compatible like they once were....meaning you cannot just install MariaDB and expect it to load the existing database files.

LHammonds

---

### Post by edvigil on 2022-08-05
Thanks LHammonds. 
I do have a back up of all my websites. I will follow your advice and let you know how it worked.
Thanks again my friend and have a great weekend!
Edword Louis Vigil

---


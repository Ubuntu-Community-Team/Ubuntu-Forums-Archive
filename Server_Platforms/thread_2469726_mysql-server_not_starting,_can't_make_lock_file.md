---
title: "mysql-server not starting, can't make lock file ?"
date: 2021-12-07
forum: Server Platforms
---

### Post by byenary on 2021-12-07
Hi i'm trying to get mysql-server back to work on ubuntu 20.04 After purging everything related to mysql or mariadb I reinstalle mysql-server with apt. upon running the mysql_sercure_installation I got this Error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Looking in the logs gave me this
```

021-12-07T21:27:03.965725Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.27-0ubuntu0.20.04.1) starting as process 7999
2021-12-07T21:27:03.984880Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2021-12-07T21:27:04.160815Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2021-12-07T21:27:04.258932Z 0 [ERROR] [MY-011292] [Server] Plugin mysqlx reported: 'Preparation of I/O interfaces failed, X Protocol won't be accessible'
2021-12-07T21:27:04.258998Z 0 [ERROR] [MY-011300] [Server] Plugin mysqlx reported: 'Setup of socket: '/var/run/mysqld/mysqlx.sock' failed, can't create lock file /var/run/mysqld/mysqlx.sock.lock'
2021-12-07T21:27:04.356398Z 0 [Warning] [MY-013746] [Server] A deprecated TLS version TLSv1 is enabled for channel mysql_main
2021-12-07T21:27:04.356422Z 0 [Warning] [MY-013746] [Server] A deprecated TLS version TLSv1.1 is enabled for channel mysql_main
2021-12-07T21:27:04.357045Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
2021-12-07T21:27:04.357077Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
2021-12-07T21:27:04.357238Z 0 [ERROR] [MY-010273] [Server] Could not create unix socket lock file /var/run/mysqld/mysqld.sock.lock.
2021-12-07T21:27:04.357255Z 0 [ERROR] [MY-010268] [Server] Unable to setup unix socket lock file.
2021-12-07T21:27:04.357499Z 0 [ERROR] [MY-010119] [Server] Aborting
2021-12-07T21:27:05.785023Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.27-0ubuntu0.20.04.1)  (Ubuntu).

```

Not sure why this does not work out of the box I then did this

```
/var/run$ sudo mkdir mysqld
/var/run$ sudo chown mysql /var/run/mysqld
/var/run$ sudo chmod -R 775 /var/run/mysqld
/var/run$ sudo service mysql start
```

That seemed to fix it but in the starting process it also gets stopped by user signal ?



```

2021-12-07T21:31:20.583470Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2021-12-07T21:31:20.740519Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2021-12-07T21:31:20.916182Z 0 [Warning] [MY-013746] [Server] A deprecated TLS version TLSv1 is enabled for channel mysql_main
2021-12-07T21:31:20.916205Z 0 [Warning] [MY-013746] [Server] A deprecated TLS version TLSv1.1 is enabled for channel mysql_main
2021-12-07T21:31:20.916892Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
2021-12-07T21:31:20.916925Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
2021-12-07T21:31:20.924194Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Socket: /var/run/mysqld/mysqlx.sock
2021-12-07T21:31:20.924212Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.0.27-0ubuntu0.20.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 0  (Ubuntu).
2021-12-07T21:31:20.932884Z 0 [System] [MY-013172] [Server] Received SHUTDOWN from user <via user signal>. Shutting down mysqld (Version: 8.0.27-0ubuntu0.20.04.1).
2021-12-07T21:31:22.352606Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.27-0ubuntu0.20.04.1)  (Ubuntu).

```

Not sure where this 'signal would come from'... Also noticed that after reboot the folder mysqld in /var/run is gone and i'm back to the start... Any pointers to fix this ?

---

### Post by LHammonds on 2021-12-08
> **byenary said:**
> After purging everything related to mysql or mariadb
Was this a functioning MySQL server or MariaDB server?  Or are you trying to switch database engines or perform an upgrade?

Curious what the most-likely action was that caused this issue.

Also, when you have everything purged, did you run commands similar to this to make sure?

```

sudo apt list --installed | grep mysql
sudo apt list --installed | grep mariadb
find / -name my.cnf
find / -name mariadb.cnf
ls -l /etc/mysql
ls -l /var/lib/mysql
ls -l /var/log/mysql

```

LHammonds

---

### Post by byenary on 2021-12-08
Hi,

I verified this with your commands en was all good. Nothing left after purging mysql, I also manualy removed /etc/mysql and var/lilb/mysql
Tried again en same result.
Don't realy remember bu i think i originaly set up this machine with mariadb then did not use it for a while so not sure, but I could not log in and since db's were empty I decided to purge the whole thing to have a quick fix but that turned out wrong... 
Sorf of gave up now and setup a vm voor the local dev work (easy for backup )

---

### Post by LHammonds on 2021-12-09
I used to use MySQL until Oracle took over and basically halted development on it and made it stagnate.  The original MySQL community developers forked the code to make MariaDB and at the beginning they were binary-compatible so you could switch between them at will.  But at some point, the code base diverged because MariaDB team was making significant changes and improvements.

I switched to MariaDB and rarely looked back.  So I am unfamiliar with what would happen in a situation where MariaDB being on a server was uninstalled and then installing MySQL.  Normally, you'd expect a package removed would be complete except any data it creates after and would be separate from a different package but because they both use the same IDs, commands, data, configs, services and common locations, things can be a bit tricky.

The fastest solution would probably be to just re-install MariaDB.  If you really want MySQL, the next fastest and safest solution might be to reformat the system and re-install the OS.

If I find myself with free time, I will try the scenario of installing MariaDB on a fresh system, then uninstall it and install MySQL but I know this will not exactly replicate your situation since 2 people installing a system can do things differently and there is also the matter of what was done since it was installed on your machine...which is an unknown factor.  A complete log of all your bash command history might shed some light but command-line history is only part of the picture.

LHammonds

---

### Post by rsteinmetz70112 on 2021-12-09
Just a dumb question what are the permissions of the files in question? Sounds a lot like the ownership may be wrong.

---


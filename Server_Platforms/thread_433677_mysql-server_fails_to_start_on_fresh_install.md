---
title: "mysql-server fails to start on fresh install"
date: 2007-05-05
forum: Server Platforms
---

### Post by loucomballa on 2007-05-05
Hi all,
In my fresh Feisty install whenever i try to install mysq-server (both from synaptic and commmand line) it raises an configure error. When i try to start it from init.d it fails. However, If i reboot the system, mysql is apparently up and i can log in as root. But if i restart the daemon, it again fails to start. Any ideas?

---

### Post by loucomballa on 2007-05-05
the error on syslog reads:
May  5 14:43:00 nitrogen mysqld[6664]: 070505 14:43:00  InnoDB: Started; log sequence number 0 43655
May  5 14:43:00 nitrogen mysqld[6664]: 070505 14:43:00 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
May  5 14:43:00 nitrogen mysqld[6664]: 070505 14:43:00 [ERROR] Do you already have another mysqld server running on port: 3306 ?
May  5 14:43:00 nitrogen mysqld[6664]: 070505 14:43:00 [ERROR] Aborting
May  5 14:43:00 nitrogen mysqld[6664]: 
May  5 14:43:00 nitrogen mysqld[6664]: 070505 14:43:00  InnoDB: Starting shutdown...
May  5 14:43:02 nitrogen mysqld[6664]: 070505 14:43:02  InnoDB: Shutdown completed; log sequence number 0 43655
May  5 14:43:02 nitrogen mysqld[6664]: 070505 14:43:02 [Note] /usr/sbin/mysqld: Shutdown complete
May  5 14:43:02 nitrogen mysqld[6664]: 
May  5 14:43:02 nitrogen mysqld_safe[6694]: ended
May  5 14:43:15 nitrogen /etc/init.d/mysql[6836]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May  5 14:43:15 nitrogen /etc/init.d/mysql[6836]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May  5 14:43:15 nitrogen /etc/init.d/mysql[6836]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
May  5 14:43:15 nitrogen /etc/init.d/mysql[6836]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
May  5 14:43:15 nitrogen /etc/init.d/mysql[6836]:

---


---
title: "mysql does not start"
date: 2008-05-05
forum: Server Platforms
---

### Post by JanKruis on 2008-05-05
under version 7.10 changes below working well but under version 8.04 MySql will not start (see the error in syslog below


mkdir -p /usr/lib/dovecot/var/run/mysqld
cd /usr/lib/dovecot/var/run
chown mysql:root mysqld


invoke-rc.d mysql stop
rm -fr /var/run/mysqld
cd /var/run/
ln -s /usr/lib/dovecot/var/run/mysqld/



i change /etc/mysql/my.cnf and fix the paths :


nano /etc/mysql/my.cnf

[client]
port            = 3306
socket          = /usr/lib/dovecot/var/run/mysqld/mysqld.sock

[mysqld_safe]
socket          = /usr/lib/dovecot/var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
user            = mysql
pid-file        = /usr/lib/dovecot/var/run/mysqld/mysqld.pid
socket          = /usr/lib/dovecot/var/run/mysqld/mysqld.sock


And finally also edit /etc/mysql/debian.cnf and fix the paths :


nano /etc/mysql/debian.cnf

[client]
host     = localhost
user     = debian-sys-maint
password = xxx
socket   = /usr/lib/dovecot/var/run/mysqld/mysqld.sock
[mysql_upgrade]
user     = debian-sys-maint
password = xxx
socket   = /usr/lib/dovecot/var/run/mysqld/mysqld.sock
basedir  = /usr


Restart MySQL :
# 

invoke-rc.d mysql restart


I get the following error message in /var/log/syslog


May  5 22:17:22 ubuntu810 mysqld[4795]: 080505 22:17:22 [Note] /usr/sbin/mysqld: Normal shutdown
May  5 22:17:22 ubuntu810 mysqld[4795]: 
May  5 22:17:22 ubuntu810 mysqld[4795]: 080505 22:17:22  InnoDB: Starting shutdown...
May  5 22:17:22 ubuntu810 mysqld[4795]: 080505 22:17:22  InnoDB: Shutdown completed; log sequence number 0 43655
May  5 22:17:22 ubuntu810 mysqld[4795]: 080505 22:17:22 [Note] /usr/sbin/mysqld: Shutdown complete
May  5 22:17:22 ubuntu810 mysqld[4795]: 
May  5 22:17:22 ubuntu810 mysqld_safe[9042]: ended
May  5 22:24:19 ubuntu810 mysqld_safe[9173]: started
May  5 22:24:19 ubuntu810 mysqld[9177]: 080505 22:24:19  InnoDB: Started; log sequence number 0 43655
May  5 22:24:19 ubuntu810 kernel: [ 2146.054541] audit(1210019059.160:3): operation="inode_mknod" request_mask="w::" denied_mask="w::" name="/usr/lib/dovecot/var/run/mysqld/mysqld.sock" pid=9175 profile="/usr/sbin/mysqld" namespace="default"
May  5 22:24:19 ubuntu810 mysqld[9177]: 080505 22:24:19 [ERROR] Can't start server : Bind on unix socket: Permission denied
May  5 22:24:19 ubuntu810 mysqld[9177]: 080505 22:24:19 [ERROR] Do you already have another mysqld server running on socket: /usr/lib/dovecot/var/run/mysqld/mysqld.sock ?
May  5 22:24:19 ubuntu810 mysqld[9177]: 080505 22:24:19 [ERROR] Aborting
May  5 22:24:19 ubuntu810 mysqld[9177]: 
May  5 22:24:19 ubuntu810 mysqld[9177]: 080505 22:24:19  InnoDB: Starting shutdown...
May  5 22:24:21 ubuntu810 mysqld[9177]: 080505 22:24:21  InnoDB: Shutdown completed; log sequence number 0 43655
May  5 22:24:21 ubuntu810 mysqld[9177]: 080505 22:24:21 [Note] /usr/sbin/mysqld: Shutdown complete
May  5 22:24:21 ubuntu810 mysqld[9177]: 
May  5 22:24:21 ubuntu810 mysqld_safe[9208]: ended
May  5 22:24:33 ubuntu810 /etc/init.d/mysql[9339]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May  5 22:24:33 ubuntu810 /etc/init.d/mysql[9339]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May  5 22:24:33 ubuntu810 /etc/init.d/mysql[9339]: error: 'Can't connect to local MySQL server through socket '/usr/lib/dovecot/var/run/mysqld/mysqld.sock' (2)'
May  5 22:24:33 ubuntu810 /etc/init.d/mysql[9339]: Check that mysqld is running and that the socket: '/usr/lib/dovecot/var/run/mysqld/mysqld.sock' exists!
May  5 22:24:33 ubuntu810 /etc/init.d/mysql[9339]: 


When i change the file back to the orig


May  5 21:54:06 ubuntu810 mysqld[4320]: 080505 21:54:06  InnoDB: Starting shutdown...
May  5 21:54:09 ubuntu810 mysqld[4320]: 080505 21:54:09  InnoDB: Shutdown completed; log sequence number 0 43655
May  5 21:54:09 ubuntu810 mysqld[4320]: 080505 21:54:09 [Note] /usr/sbin/mysqld: Shutdown complete
May  5 21:54:09 ubuntu810 mysqld[4320]: 
May  5 21:54:09 ubuntu810 mysqld_safe[4716]: ended
May  5 21:54:10 ubuntu810 mysqld_safe[4791]: started
May  5 21:54:10 ubuntu810 mysqld[4795]: 080505 21:54:10  InnoDB: Started; log sequence number 0 43655
May  5 21:54:10 ubuntu810 mysqld[4795]: 080505 21:54:10 [Note] /usr/sbin/mysqld: ready for connections.
May  5 21:54:10 ubuntu810 mysqld[4795]: Version: '5.0.51a-3ubuntu5'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
May  5 21:54:11 ubuntu810 /etc/mysql/debian-start[4832]: Upgrading MySQL tables if necessary.
May  5 21:54:11 ubuntu810 /etc/mysql/debian-start[4841]: Looking for 'mysql' in: /usr/bin/mysql
May  5 21:54:11 ubuntu810 /etc/mysql/debian-start[4841]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
May  5 21:54:11 ubuntu810 /etc/mysql/debian-start[4841]: This installation of MySQL is already upgraded to 5.0.51a, use --force if you still need to run mysql_upgrade
May  5 21:54:11 ubuntu810 /etc/mysql/debian-start[4845]: Checking for insecure root accounts.
May  5 21:54:11 ubuntu810 /etc/mysql/debian-start[4849]: Checking for crashed MySQL tables.

---


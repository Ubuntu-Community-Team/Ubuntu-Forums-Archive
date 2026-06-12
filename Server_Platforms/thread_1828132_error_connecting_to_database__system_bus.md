---
title: "error connecting to database / system bus ?"
date: 2011-08-18
forum: Server Platforms
---

### Post by 007casper on 2011-08-18
I am getting a database connection error on the app server.  So, I wanted to check the database server.

When I log in as a user, and service mysql status, I get
 status: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

When I enter, service mysql start
 start: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

then, I try it as root... it says it is running.
root@servery:/etc/mysql# service mysql restart
mysql start/running, process 3126

root@servery:/etc/mysql# service mysql start
start: Job is already running: mysql

?

---

### Post by 007casper on 2011-08-19
I believe system bus has to do with permission issue.  If you have the right permission it works.

---


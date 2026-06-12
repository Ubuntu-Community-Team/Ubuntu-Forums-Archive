---
title: "error 2002 installing phpmyadmin"
date: 2018-04-02
forum: Server Platforms
---

### Post by ferjero989 on 2018-04-02
im trying to use an old version of mysql (5.5.57) and unpacked the tar and followed the instructions in mysql site to install it. 
the service runs and i can login and run queries (internally)
my.cnf shows the sqld.sock running from /tmp/
and an LS into the /tmp shows it there
when i try to install phpmyadmin he gives an error trying to connect to SQL tru /var/run/mysqld/mysql.sock
i edited /etc/mysql/my.cnf (moved the socket to /var/run/mysqld/mysql.sock) and restarted the server  but the mysql.sock still runs from /tmp
i might not be editing the right one? is mysql not picking up my cnf file?

---

### Post by ferjero989 on 2018-04-02
you know what.. im just gonna link it and be done with it.

---


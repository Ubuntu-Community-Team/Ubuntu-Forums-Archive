---
title: "Problem starting Mysql Safemode"
date: 2008-08-13
forum: Server Platforms
---

### Post by Kingy_uk on 2008-08-13
Hi I'v been trying to start mysql in safemode using the mysqld_safe --grant-grant-tables and get this error.


root@kingy-linux:/var/run/mysqld# sudo invoke-rc.d mysql stop
 * Stopping MySQL database server mysqld                                                                              [ OK ] 
root@kingy-linux:/var/run/mysqld# mysqld_safe --grant-grant-tables
nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[12647]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[12653]: ended
root@kingy-linux:/var/run/mysqld# 


  Has anyone got any idea on how to let the mysql boot into safemode.

Thanks

---


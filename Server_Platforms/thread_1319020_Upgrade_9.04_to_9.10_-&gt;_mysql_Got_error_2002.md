---
title: "Upgrade 9.04 to 9.10 -&gt; mysql Got error: 2002"
date: 2009-11-08
forum: Server Platforms
---

### Post by m_morph on 2009-11-08
Hello,

Last night I have made the upgrade from (Ubuntu server) 8.10 to 9.04. All went fine. Than I made upgrade from 9.04 to 9.10 and for some reason mysql will not start. 

I am running ISPConfig on my server. All the other services are running like they should. From the console if I type "/etc/init.d/mysqld" -> "fail". 

When I do "mysql_upgrade" i get:[INDENT]Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck with default connection arguments
mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect
FATAL ERROR: Upgrade failed

[/INDENT]... any ideas whats wrong?

---


---
title: "MySQL-server woes"
date: 2008-05-13
forum: Server Platforms
---

### Post by rsteckly7 on 2008-05-13
hi,

I'm having some trouble getting My-sql server to work on Hardy Heron.  I installed mysql-server and mysql-server-5.0 through the synaptic package manager.  its telling me that 
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet

However, it says the same thing for mysql-server when the machine tries to install it.

I only reinstalled mysql because I couldn't get it to accept a remote connection.  I tried changing the my.cnf file to allow it do so, but without success.  When I type mysql, it tells me that it can't connect:

 Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

This is why I tried reinstalling it.  But as you can see, I'm not having much success with that either.

---

### Post by windependence on 2008-05-14
> **rsteckly7 said:**
> hi,

I'm having some trouble getting My-sql server to work on Hardy Heron.  I installed mysql-server and mysql-server-5.0 through the synaptic package manager.  its telling me that 
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet

However, it says the same thing for mysql-server when the machine tries to install it.

I only reinstalled mysql because I couldn't get it to accept a remote connection.  I tried changing the my.cnf file to allow it do so, but without success.  When I type mysql, it tells me that it can't connect:

 Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

This is why I tried reinstalling it.  But as you can see, I'm not having much success with that either.

Did you restart MySQL after you made the changes? Also, MySQL only listens on the localhost unless you change the config file and have it listen on an outside port. the configuration it is referring to is setting up a MySQL user and password among other things. More can be found on the MySQL web site.

-Tim

---


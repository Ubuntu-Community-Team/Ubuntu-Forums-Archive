---
title: "ERROR: PleskFatalException"
date: 2008-02-02
forum: Server Platforms
---

### Post by b06dqn on 2008-02-02
I've recently moved my websites to a dedicated server (CentOS) and from time to time the server gives this error:

ERROR: PleskFatalException
Unable to connect to database: mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (11)

0: /usr/local/psa/admin/plib/common_func.php3:158
psaerror(string 'Unable to connect to database: mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (11)')
1: /usr/local/psa/admin/auto_prepend/auth.php3:87

The websites sometime give a blank page or don't load at all. 

If anyone knows how to fix this please help. Thanks

---

### Post by soulresin on 2008-02-05
> **b06dqn said:**
> I've recently moved my websites to a dedicated server (CentOS) and from time to time the server gives this error:

ERROR: PleskFatalException
Unable to connect to database: mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (11)

0: /usr/local/psa/admin/plib/common_func.php3:158
psaerror(string 'Unable to connect to database: mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (11)')
1: /usr/local/psa/admin/auto_prepend/auth.php3:87

The websites sometime give a blank page or don't load at all. 

If anyone knows how to fix this please help. Thanks


Hello.  Post is a little old, but I deal with Plesk on a daily basis (ugh) so I thought I'd give it a whirl.

Evidently, this error is because Plesk can't connect to MySQL.  Plesk uses MySQL for pretty much everything.

Something like this is usually 2 things:

1.  MySQL has blown up, crashed out.  This is A Bad Thing.
tail /var/log/mysqld.log for any errors.  Get your dedicated server support to help out if it shows anything ugly about db corruption.  You're doing regular mysqldumps right?

2.  MySQL has become unavailable due to too many connections.  Could be queries stacked up for whatever reason.  Usually if this is the case you'll get a "Too many connections" error from MySQL, but stranger things have happened.
Get mysqltuner.pl from [http://mysqltuner.com/mysqltuner.pl](http://mysqltuner.com/mysqltuner.pl) and run that bad boy, which will make recommendations on MySQL config changes.
Set wait_timeout = 600 and interactive_timeout = 600 in /etc/my.cnf to help with weird queries stacking up.  Enable slow query logging to see any queries that are causing things to stack up.

---


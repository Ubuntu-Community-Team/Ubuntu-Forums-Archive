---
title: "Access Denied for User-Upgrading to Mysql5.5"
date: 2011-05-03
forum: Server Platforms
---

### Post by thoufiq on 2011-05-03
[COLOR=Red][COLOR=Black]Hello All,
              When am trying to upgrade from mysql5.1 to mysql5.5, i got many errors and at-last i upgraded to mysql5.5. It is going inside the mysql root and have permissions to create new databases, but still i am facing one problem is when giving command **[COLOR=Red]mysql_upgrade[/COLOR]**, i got error like this
[/COLOR][/COLOR][B][COLOR=Red]
root@dhcppc4:~# mysql_upgrade
Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock'
Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock'
Running 'mysql_fix_privilage_tables'...
ERROR 1044 (42000): Access denied for user ''@' localhost to database 'mysql'
FATAL ERROR: Upgrade failed[/COLOR][/B]

Can anyone suggest me to resolve this error.

Thanks in advance.

---


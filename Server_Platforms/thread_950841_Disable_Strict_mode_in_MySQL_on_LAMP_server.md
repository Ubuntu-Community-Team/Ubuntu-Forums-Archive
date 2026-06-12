---
title: "Disable Strict mode in MySQL on LAMP server"
date: 2008-10-17
forum: Server Platforms
---

### Post by davidshere on 2008-10-17
Referencing:  [http://ubuntuforums.org/showthread.php?t=487216&highlight=mysql+strict+mode](http://ubuntuforums.org/showthread.php?t=487216&highlight=mysql+strict+mode)

I have the same problem as these two folks.  I need to turn off "strict mode" in MySQL.  I am installing Mambo and it says that you have to turn off "strict mode": [http://forum.mambo-foundation.org/showthread.php?t=5254](http://forum.mambo-foundation.org/showthread.php?t=5254)

When I try the first suggestion, it fails because there is no "my.ini" file.  "my.cnf" is available, but inserting the suggested configuration change into this file yields no results.

When I try the second suggestion, I get:

```
mysql> SET @@global.sql_mode= '';
Query OK, 0 rows affected (0.00 sec)

```

and it also yields no results.

Any suggestions would be greatly appreciated.

---

### Post by cdenley on 2008-10-17
Did you try inserting
```

sql-mode=""

```
into my.cnf in the mysqld section? You can also modify the startup script (/etc/init.d/mysql).
[http://dev.mysql.com/doc/refman/5.0/en/server-sql-mode.html](http://dev.mysql.com/doc/refman/5.0/en/server-sql-mode.html)

---


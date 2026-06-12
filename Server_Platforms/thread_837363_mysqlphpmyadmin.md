---
title: "mysql/phpmyadmin"
date: 2008-06-22
forum: Server Platforms
---

### Post by xaco1234 on 2008-06-22
i set up a normal lamp server, (it's a test server for when i learn php/mysql) and i installed php, apache, mysql and phpmyadmin. now i added a user,
 (since i won't use the root account for obvius reasons) and the pw is wrong what ever script i use.
 (i used some normal scripts also just to test if it's my code or not). then getting
 "#1045 - Access denied for user 'stats'@'localhost' (using password: YES)".

i know the pw is correct as i have changed it several times in phpmyadmin to be sure.

---

### Post by mbeach on 2008-06-22
the password may be correct, but you need to apply permissions to the stats user to access those databases you are trying to get to.

look up the "GRANT" statement, or in phpmyadmin to see what 'stats' can do run the following sql statement:
SHOW GRANTS FOR 'stats'@'localhost';

see:
[http://dev.mysql.com/doc/refman/5.0/en/privileges.html](http://dev.mysql.com/doc/refman/5.0/en/privileges.html)

---

### Post by xaco1234 on 2008-06-23
the "stats" account got all the perimissions on the DB in question.

---

### Post by mbeach on 2008-06-23
perhaps post a sample of the php code you are attempting to connect with.

---

### Post by xaco1234 on 2008-06-23
it not only the php script, it won't even let me login to phpmyadmin with that account.

---

### Post by forger on 2008-06-23
> **xaco1234 said:**
> 
 "#1045 - Access denied for user 'stats'@'localhost' (using password: YES)".

i know the pw is correct as i have changed it several times in phpmyadmin to be sure.

Have you looked at:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[http://ubuntuforums.org/showthread.php?t=746449](http://ubuntuforums.org/showthread.php?t=746449)
[http://ubuntuforums.org/showthread.php?t=87373](http://ubuntuforums.org/showthread.php?t=87373)
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
[http://www.webmasterworld.com/forum88/1621.htm](http://www.webmasterworld.com/forum88/1621.htm)
[http://www.google.com/search?q=ubuntu "1045 - Access denied for user"]("http://www.google.com/search?q=ubuntu "1045 - Access denied for user"")

---

### Post by mbeach on 2008-06-23
are apache and mysql on the same server?

---

### Post by xaco1234 on 2008-06-23
yep

---

### Post by forger on 2008-06-25
Maybe it's a different port stated in mysqld.conf?

or.. Have you tried connecting using the mysql client command?
```
mysql -u stats -h localhost
mysql -u stats
```

---

### Post by xaco1234 on 2008-06-26
what atleast i think is very strange is that if i remove the pw on the user i can login, and i can ligin with the root account.

---


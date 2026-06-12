---
title: "mysqldump, ERROR 1064 (42000): You have an error in your SQL syntax;"
date: 2012-01-17
forum: Server Platforms
---

### Post by 1cookie on 2012-01-17
hi

My environment is: mysql ver 14.14 Distrib 5.1.58, running on Ubuntu, Apache localhost.

I'm in the MySQL CLI trying to run the command:

```

mysql> mysqldump -u cookie -p coffee_shop > /home/andy/backup/dump.sql;

```This should dump the coffee_shop database to a file named: dump.sql, pretty simple. It doesn't work?

I get a MySQL error: 

```

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysqldump -u cookie -p coffee_shop > /home/andy/backup/dump.sql' at line 1


```It should be pretty standard stuff, what's wrong with my syntax? :(

---

### Post by Wayne_V on 2012-01-17
you are running mysqldump from within mysql?

---

### Post by 1cookie on 2012-01-17
> **Wayne_V said:**
> you are running mysqldump from within mysql?

What a noob! Me that is. Thanks Wayne.

---


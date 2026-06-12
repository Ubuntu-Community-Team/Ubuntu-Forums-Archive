---
title: "phpmyadmin, see quries?"
date: 2013-02-13
forum: Server Platforms
---

### Post by wlraider70 on 2013-02-13
Hi,

I used phpMyAdmin to backup my database. Can I see the actual query that it is submitting?

I would like to see anything that it does not just backup.

---

### Post by stmiller on 2013-02-17
From the command line, you can enter mysql:

```

$ mysql -uroot -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1243162
Server version: 5.1.67-0ubuntu0.10.04.1 (Ubuntu)

```

Then type this to see running mysql processes: 

```
mysql> show processlist;

```

There is also an app called mytop that will show mysql activity.

```
sudo apt-get install mytop
```

---

### Post by MrKaliman on 2013-02-17
mysqldump is the cli command you need! Very simple to use.

[http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html)

mysqldump -u username [database] -p > /var/tmp/database.sql
Hit Enter and provide password

---


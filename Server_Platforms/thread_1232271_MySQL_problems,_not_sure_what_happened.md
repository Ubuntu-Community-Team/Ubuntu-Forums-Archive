---
title: "MySQL problems, not sure what happened"
date: 2009-08-05
forum: Server Platforms
---

### Post by Jago6060 on 2009-08-05
Running Ubuntu 9.04 Server
Server version: Apache/2.2.11 (Ubuntu)
Server built:   Jul 10 2009 18:37:31
Can't get mysql version because of error below.

```

root@supermicro:/etc/mysql# mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
root@supermicro:/etc/mysql# 

```For some reason I can't connect to mysql anymore, which is a real problem because I have some important programs using it.  Any idea what causes this error?

P.S. mysqld.sock is no where to be found via "locate mysqld.sock"

---

### Post by Jago6060 on 2009-08-05
Ok I figured it out already, haha.  The computer running MySQL had a bind address defined in my.cnf, just had to change that to the new address.  But I have a new question.  I managed to restart mysql but now the output looks like this...

```

root@supermicro:/# /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                                             [ OK ] 
 * Starting MySQL database server mysqld                                                                                                             [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```

What does the last line mean?  And how do I fix it?

---

### Post by Cheesemill on 2009-08-05
Nothing to fix. It's telling you that it's checking for any tables that weren't closed cleanly, not that it's found any.

---

### Post by Jago6060 on 2009-08-05
Ah I see, thanks a bunch--TOPIC SOLVED

---


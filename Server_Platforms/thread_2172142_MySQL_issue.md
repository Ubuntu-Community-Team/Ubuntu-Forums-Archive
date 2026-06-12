---
title: "MySQL issue"
date: 2013-09-03
forum: Server Platforms
---

### Post by athf-president on 2013-09-03
Hello all,
 I was working on a wiki for my server and so far things have been going fine. I am changing alot of logins from the previous network administrator to myself, so I do apologize if I am asking some basic questions. I am currently trying to change my mediawiki credentials, and ran into a problem. I have already asked a question in their forums and got the answer I needed to at least get me back up and going. My question is that when I ran this command:

mysqld_safe --skip-grant-tables

I was doing so because I don't know what the SQL password currently is. Now when I navigate to my wiki, or try to execute "mysql" inside my linux server, I get these errors

[SIZE=1]Wiki[/SIZE] = (Cannot contact the database server: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) (localhost))

Server = ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Thank you

---

### Post by Habitual on 2013-09-03
the mysqld_safe --skip-grant-tables routine is commonly used to 'reset' and unknown mysql root password.
After it has been reset, then it should be restarted in the usual fashion .
[Stop the             MySQL server, then restart it in normal mode again.]("https://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html")

Good luck!

---


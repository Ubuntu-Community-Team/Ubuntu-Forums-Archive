---
title: "phpMyAdmin #1045 - Access denied for user 'root'@'localhost' (using password: NO)"
date: 2008-04-05
forum: Server Platforms
---

### Post by Madman6510 on 2008-04-05
Ugh, this sucks. I keep getting an error #1045 - Access denied for user 'root'@'localhost' (using password: NO)

I don't get it, the default login for phpmyadmin is supposed to be username root, password blank.

I enter it, but I get error #1045. If I try to open the PostgreSQL console to change the password, I get "psql: FATAL:   database "root" does not exist".

This is really bugging me, I need to get MySQL up and running soon...

The server is a Debian server, if that helps.

---

### Post by mhmjr on 2008-04-06
You are getting an error related to MySQL authentication. You state you are using phpmyadmin, which is a front end for MySQLl, and you also state you need to get MySQL up and running. But you mention you attempted to resolve this by attempting to reset the Postgres password. Postgres is not the same thing as MySQL. Perhaps changing the MySQL password will help:

[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix)


[http://www.netadmintools.com/art90.html](http://www.netadmintools.com/art90.html)

Either of those should be handy.

-mhmjr

---


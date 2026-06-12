---
title: "ERROR 2002 (HY000): Can't connect to local MySQL server through socket"
date: 2011-05-09
forum: Security
---

### Post by Tonata on 2011-05-09
Goodday All,

I have installed the mysql server on my ubuntu. I need to assign or reset the root password. I followed the article at [http://www.ubuntugeek.com/reset-the-root-password-on-mysql.html](http://www.ubuntugeek.com/reset-the-root-password-on-mysql.html). When I ran the command ```
mysql reset-password
```I get the error ```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```and then I ran the command ```

mysqld_safe --skip-grant-tables
``` then I got the following results ```
110509 09:09:58 mysqld_safe mysqld from pid file /var/lib/mysql/Richard-HP4520s.pid ended
```. Then I executed the command ```
mysql --user=root mysql
``` and I got the following results ```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```Please explain what am i doing wrong, and explain to someone who almost has no experience with ubuntu. I am new to this.

Thank you

---

### Post by Ryan Dwyer on 2011-05-09
Running "mysql reset-password" is not the same as running "/etc/init.d/mysql reset-password".

As it turns out, that tutorial appears to be outdated so it won't work anyway. Try searching Google for "mysqladmin reset root password".

---


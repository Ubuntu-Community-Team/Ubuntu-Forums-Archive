---
title: "Mysql"
date: 2005-10-06
forum: Server Platforms
---

### Post by waynejkruse10 on 2005-10-06
I finally got my server working using the guide on wiki.ubuntu.com

But occasionly, i go to phpmyadmin and i get this:

> Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Which means mysql isnt running. I re-install mysql and it works, but then stops running again after a little while.

Why does this happen?? and how can i fix it.

Wayne

---

### Post by diebels on 2005-10-07
Check if running:
ps aux | grep mysqld
Start:
sudo /etc/init.d/mysqld start
Why it happens:
:??
How to fix:
Look for error messages in /var/log/mysql*

Good luck

---

### Post by waynejkruse10 on 2005-10-07
ok, i tried typing in this: /etc/init.d/mysqld start but it says there us no such file or directory. So i took a look in /etc/init.d and i found a file called "mysql" so i try /etc/init.d/mysql start instead and i get:

starting database server failed, take a look at syslog.

So i go to /var/log/syslog and check that out and the last entry was: "check that mysqld is running and the socket /var/run/mysqld/mysqld.sock exists

---

### Post by diebels on 2005-10-07
Ok, did it exist?
Looks something like this:
```
ls /var/run/mysqld/mysqld.sock -lh
srwxrwxrwx  1 mysql mysql 0 2005-10-07 10:08 /var/run/mysqld/mysqld.sock
```
```
file /var/run/mysqld/mysqld.sock
/var/run/mysqld/mysqld.sock: socket
```

---

### Post by elvisalexei on 2005-10-07
Hi,

I used to hav the same error, so I modify my php.ini file (/etc/php4/apache2/php.ini), look for the mysql.default_socket variable and write the socket u'r using (mine's: /var/lib/mysql/mysql.sock).

that should work.

---

### Post by badarras on 2005-10-20
I was having the same socket problem.  My fix was as follows:

1.  apt-get remove --purge mysql-server

2.  apt-get install mysql-server-4.1

This solved the problem for me.

Cheers.

---


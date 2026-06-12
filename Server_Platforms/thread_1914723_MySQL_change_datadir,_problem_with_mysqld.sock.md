---
title: "MySQL change datadir, problem with mysqld.sock"
date: 2012-01-24
forum: Server Platforms
---

### Post by Trotel on 2012-01-24
Hi everyone,

I tried to change the database dirrectory, datadir, I did the following steps.
My machine: Laptop Ubuntu 11.10 64-bit

Install: sudo apt-get install mysql-server mysql-client
All Ok, I can create databases, tables, all ok.
Change the datadir:
> 
1) $ /etc/init.d/mysql stop
2) $ cp -R -p /var/lib/mysql /new_path
3) $ rm /new_path                      (this only remove files unnecessary)
4) $ gedit /etc/mysql/my.cnf

Change the "databir = var/lib/mysql" to the new path.
> 
5) $ gedit /etc/apparmor.d/usr.sbin.mysqld

Change the "/var/liv/mysql" to the new lines wit "/new_path/mysql"
> 
6) $ /etc/init.d/apparmor reload
7) $ /etc/init.d/mysql restart
8. $ service mysql status     (is Ok)


The error is the following.
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
```

I tried to change the permissions in /new_path/mysql and didn't work.

I tried to copy only the databases (not all files in mysql dir) and it didn't work

I saw in other forum that I have to change the /etc/apparmor.d/usr.sbin.mysqld  the following

 /var/run/mysqld/mysqld.pid w,
 /var/run/mysqld/mysqld.sock w,

Replace "/var/run/mysqld/mysqld" by "/{,var/}run/mysqld/mysqld" but in my case it was with "/{,var/}run/mysqld/mysqld" by default.

Please I need help, I have 2 weeks with this problem.

Thanks.

---


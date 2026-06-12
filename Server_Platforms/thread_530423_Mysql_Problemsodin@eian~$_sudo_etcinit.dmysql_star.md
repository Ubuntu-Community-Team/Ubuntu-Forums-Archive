---
title: "Mysql Problemsodin@eian:~$ sudo /etc/init.d/mysql start"
date: 2007-08-20
forum: Server Platforms
---

### Post by zeveck on 2007-08-20
Trying to start MySQL, but getting noise:

```
$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                                              [ OK ]
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
odin@eian:~$ /usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
```

It actually appears to start okay...(I can connect as root through phpmyadmin)...but I am not sure what this error indicates nor how to fix it. Pointers?

~RMC

---

### Post by southernman on 2007-08-20
I just recently went through this too. Found a solution to my problem in the link below:

[http://ubuntuforums.org/showthread.php?t=112505&page=2]("http://ubuntuforums.org/showthread.php?t=112505&page=2")

If I recall right, what I did exactly was:

> sudo nano /etc/mysql/debian.cnf

deleted the password from the file ctrl x to close, y to save then ran
> 
mysql -u root -p

entered root's password when prompted then ran:
> 
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;

replace <password> with your root user password and do \q to exit mysql

now do:

> sudo /etc/init.d/mysql restart

You shouldn't get that error upon restarting now...

HTH's

---


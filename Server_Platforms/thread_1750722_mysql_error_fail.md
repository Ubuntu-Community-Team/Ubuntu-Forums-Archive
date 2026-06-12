---
title: "mysql error fail"
date: 2011-05-05
forum: Server Platforms
---

### Post by bigalittlea on 2011-05-05
i'm not the most knowlegable person but i have successfully installed mysql in the past. but now that i am attempting to install it again i'm getting this error during installation. has anyone seen this before?


mysql error:
* Starting MySQL database server mysqld                                                                                                           [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1

---

### Post by yakubori on 2011-05-05
How did you install MySQL this time? Did you try to start MySQL via init script as root?

---

### Post by yakubori on 2011-05-05
I was just able to install via apt on Ubuntu 11.04 x64 Desktop:

```

apt-get install mysql-server

```it asked me for a root password (for mysql) and proceeded to install the necessary server and client software, as well as some other lib packages...

---

### Post by bigalittlea on 2011-05-05
same way i've always installed it:

apt-get install mysql-server


root~# sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                                           [ OK ]
 * Starting MySQL database server mysqld                                                                                                           [fail]

---

### Post by apocalipsys2010 on 2011-05-05
Have you changed any path from the original ones? I mean... if you change any path from the original one remember to change AppArmor profile as well.

---

### Post by bigalittlea on 2011-05-05
no idea this is on a brand new vps

---

### Post by usatonycuba on 2011-05-06
> **bigalittlea said:**
> i'm not the most knowlegable person but i have successfully installed mysql in the past. but now that i am attempting to install it again i'm getting this error during installation. has anyone seen this before?


mysql error:
* Starting MySQL database server mysqld                                                                                                           [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
[COLOR=DarkRed]invoke-rc.d[/COLOR] mostly point to InnoDb memory load -related problem...
[COLOR=DarkRed]Before any change Back up your file(s) first[/COLOR]..!! that way, if something goes wrong, you always can  restore your original file.

At..
```
/etc/mysql/my.cnf
```Add [COLOR=DarkRed]skip-innodb[/COLOR] ... after thus lines that start with [COLOR=DarkRed]#[/COLOR] .... like this
```
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
skip-innodb
```Restart MySQL

---


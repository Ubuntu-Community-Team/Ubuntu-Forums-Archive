---
title: "trouble in getting lamp's mysql to work`"
date: 2008-01-14
forum: Server Platforms
---

### Post by asafche on 2008-01-14
hay, 
i've installed a the bitrockLAMPstack-5.5, in GUI. 
then i've ran Apache. its working fine.

but mysql is giving me some problems:
when i tried to activate with:

[HTML]home/user/lampstack-5.5/lampctl.sh start mysql[/HTML]

i get:
[HTML]/home/freeall/lampstack-5.5/mysql/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)'
Check that mysqld is running and that the socket: '/tmp/mysql.sock' exists![/HTML]

i've looked in "/tmp" and there isn't any sock file.

also, when i just enter, in the terminal "mysql", i get:
[HTML]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/home/freeall/lampstack-5.5/mysql/tmp/mysqld.sock' (2)[/HTML]

i didn't found the sock file anywhere. 
 
i really don't know were to start for solving this problem. i would like if any one that can pour some light on it, do it so i can understand what you're doing. 
thaks.

---

### Post by jingo811 on 2008-01-14
This one isn't really for Server-LAMP it's for desktop use when playing around with PHP and MySQL the security isn't even 70%.
I call this installation guide Desktop-LAMP.
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html](http://virtualseafarer.com/renaissance/desktop_lamp/index.html)

---

### Post by asafche on 2008-01-15
i got it. thanks.
this guide is very helpfull even though i didn't understand every command that i executed.
thanks.

---

### Post by jingo811 on 2008-01-16
If you want to understand all the commands then go to the official thingy
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---


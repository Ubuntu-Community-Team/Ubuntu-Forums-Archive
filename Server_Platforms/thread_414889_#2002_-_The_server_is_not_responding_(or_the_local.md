---
title: "#2002 - The server is not responding (or the local MySQL server's socket is not corre"
date: 2007-04-20
forum: Server Platforms
---

### Post by bandara772001 on 2007-04-20
before 2 months ago i install and configer LAMP server as datadase server it's work fine
last day it stop   local and remote (both)    when try to connect   localhost/phpmyadmin error ococer
[SIZE="4"]**#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)**[/SIZE]

when going to terminal trying to restaet the mysql using this

$ /etc/init.d/mysql restart

..failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

what i should do for this pls help

---

### Post by AllFather on 2007-04-21
got the same error  now :(

---

### Post by codingmaster on 2007-04-21
Hello!

What does:
```
ps aux | grep mysql
```
say?

Can you please post your syslog here.

If the mysql process is running, does it hang?
Try to kill it.
Then run again:
```
/etc/init.d/mysql start
```

When this should work, can you try to connect to the server using mysqladmin.
Does it work?

Best regards, Georgy Berdyshev

---

### Post by AllFather on 2007-04-21
Dont know is threadstarter is still around, but my problem remains.
Its running of a mac cube g4 (ppc) , and everything worked fine, then suddenly :o
 
1
> 
root@Euthanasia:/home/dta# /etc/init.d/mysql start
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
root@Euthanasia:/home/dta#

 
 
2
> 
root@Euthanasia:/home/dta# ls -l /var/run/mysqld/mysqld.sock
ls: /var/run/mysqld/mysqld.sock: No such file or directory

 
 
Tried apt-get remove then apt-get install.
Tried editing config, tried touch etc, but nothing seems to work for me :(

---

### Post by codingmaster on 2007-04-21
Hello!

Do not worry :)

We will try to find the problem now!

So, let's start:

> root@Euthanasia:/home/dta# ls -l /var/run/mysqld/mysqld.sock
ls: /var/run/mysqld/mysqld.sock: No such file or directory

This is normal. The mysql daemon creates the socket, when it is not working there 
is no socket!

I still need a syslog from you to say more :)

```
more /var/log/syslog | grep --color mysql
```

When it will be working at the end, it will say to you:
```
Apr 21 23:31:54 venus mysqld_safe[12402]: started
Apr 21 23:31:56 venus mysqld[12406]: 070421 23:31:56  InnoDB: Started; log sequence number 0 43655
Apr 21 23:31:56 venus mysqld[12406]: 070421 23:31:56 [Note] /usr/sbin/mysqld: ready for connections.
Apr 21 23:31:56 venus mysqld[12406]: Version: '5.0.38-Ubuntu_0ubuntu1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 21 23:31:58 venus /etc/mysql/debian-start[12471]: Upgrading MySQL tables if necessary.
Apr 21 23:32:00 venus /etc/mysql/debian-start[12484]: Checking for crashed MySQL tables.
root@venus:~# 
```

Best regards, Georgy Berdyshev

---

### Post by AllFather on 2007-04-22
> 
root@Euthanasia:/home/dta# more /var/log/syslog | grep --color mysql
root@Euthanasia:/home/dta#
 

 
Its run on a apple cube btw, g4 (ppc)
:confused:

---

### Post by codingmaster on 2007-04-22
Hello!

Can you try to run mysqld directly?

What does it say?

Regards, Georgy Berdyshev

---

### Post by AllFather on 2007-04-22
> 
[EMAIL="dta@Euthanasia:~$"]dta@Euthanasia:~$[/EMAIL] su root
Password:
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# mysqld
070422 13:55:08  InnoDB: Started; log sequence number 0 43655
070422 13:55:08 [ERROR] Can't start server: Bind on TCP/IP port: Permission denied
070422 13:55:08 [ERROR] Do you already have another mysqld server running on port: 21 ?
070422 13:55:08 [ERROR] Aborting
070422 13:55:08  InnoDB: Starting shutdown...
070422 13:55:10  InnoDB: Shutdown completed; log sequence number 0 43655
070422 13:55:10 [Note] mysqld: Shutdown complete
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]#

:(

---

### Post by codingmaster on 2007-04-22
Hello!

This is really strange:

```
070422 13:55:08 [ERROR] Do you already have another mysqld server running on port: 21 ?
```

Port 21 is for FTP.

MySQL uses by default Port 3306.

Can you change it back to 3306 and start the daemon again?

Best regards, Georgy Berdyshev

---

### Post by AllFather on 2007-04-22
> 

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sun Apr 22 14:37:07 2007 from 131.82-134-115.bkkb.no
[EMAIL="surodta@Euthanasia:~$"]surodta@Euthanasia:~$[/EMAIL] su root
Password:
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# nano -w /etc/mysql/my.cnf
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# nano -w /etc/mysql/my.cnf
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# nano -w /etc/mysql/my.cnf
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# /etc/init.d/mysql start
Starting MySQL database server: mysqld.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user [EMAIL="'debian-sys-maint'@'localhost'"]'debian-sys-maint'@'localhost'[/EMAIL] (using password: Y                                ES)'
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]# /usr/bin/mysqlcheck: Got error: 1045: Access denied f                                or user [EMAIL="'debian-sys-maint'@'localhost'"]'debian-sys-maint'@'localhost'[/EMAIL] (using password: YES) when trying to conn                                ect
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user [EMAIL="'debian-sys-maint'@'localhost'"]'debian-sys-maint'@'localhost'[/EMAIL] (using password: Y                                ES)'
[EMAIL="root@Euthanasia:/home/dta"]root@Euthanasia:/home/dta[/EMAIL]#

 
ithe client port was 3306, but the other port further down was 21.

---

### Post by AllFather on 2007-04-22
Fixed it now, or so it seems.
I had a power outage 4 times during a night here the same day this week, as the server reboots, and everything happened during 5-10 minutes, i think it got fubared somehow.
 
Root password was reset to none and some tabell corruption.
But how on gods green earth that port got changed to 21, i really really don't understand as i never touched that file :confused:

---

### Post by legal101205 on 2008-07-07
Hi, i have the same message with phpmyadmin, and can connect to localhost from Zend Studio for Eclipse.

I have the 8.04 version. MySQL was installed by Zend Platform in the Zend Platform folder. 

I had to create the mysql start file in /etc/init.d/.

The mysql server is started ('sudo /etc/init.d/mysql start' works correctly).

I am lost and totally new to linux (installed yesterday).

Thanks in advance, Nicolas.

---


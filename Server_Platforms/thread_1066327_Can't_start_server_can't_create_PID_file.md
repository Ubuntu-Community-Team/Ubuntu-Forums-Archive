---
title: "Can't start server: can't create PID file"
date: 2009-02-10
forum: Server Platforms
---

### Post by SterLo on 2009-02-10
So I seek the wisdom of the masses.

Trying to start MySQL up and it says failed...
/etc/init.d/mysqld start
Timeout error occurred trying to start MySQL Daemon.
Starting MySQL:                                            [FAILED]

Immediately WTF is stamped on my forehead. 

To find out why I run, tail -f /var/log/mysqld.log:
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
090210 15:54:02  InnoDB: Starting log scan based on checkpoint at
InnoDB: log sequence number 0 43655.
InnoDB: Doing recovery: scanned up to log sequence number 0 43655
090210 15:54:02  InnoDB: Started; log sequence number 0 43655
090210 15:54:02 [ERROR] /usr/libexec/mysqld: Can't create/write to file '/var/run/mysqld/mysqld.pid' (Errcode: 13)
090210 15:54:02 [ERROR] Can't start server: can't create PID file: Permission denied
090210 15:54:02  mysqld ended

**1**. The user MySQL does in fact exist in the passwd file.
**2**. The folder /var/run/mysqld is 755 and mysql:root
**3**. I am doing all of this as Root.
**4**. uname -a: Linux ***** 2.6.18-92.1.22.el5 #1 SMP Tue Dec 16 12:03:43 EST 2008 i686 i686 i386 GNU/Linux
**5**. cat /etc/my.cnf:
[mysqld]
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
user=mysql
# Default to using old password format for compatibility with mysql 3.x
# clients (those using the mysqlclient10 compatibility package).
old_passwords=1
**6**.Permissions for /usr/libexec/mysqld:
rwxr-xr-x 1 root root     7308960 May 25  2008 mysqld
**7**. rpm -qa | grep mysql
mysql-5.0.45-7.el5
mysql-server-5.0.45-7.el5
php-mysql-5.1.6-20.el5_2.1


[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

Where do I go from here?
[Just realized I posted this in the wrong section. Sorry about that.]

---

### Post by beno1990 on 2009-02-10
Try:

```

sudo chgrp mysql /var/run/mysqld/
sudo chmod g+w /var/run/mysqld/

```

It might also need you to change the permissions of the PID file itself. If so:

```

sudo chgrp mysql /var/run/mysqld/mysqld.pid
sudo chmod g+w /var/run/mysqld/mysqld.pid

```

---

### Post by SterLo on 2009-02-10
Thank you Beno,

But alas - no luck.
[root@*****libexec]# sudo chgrp mysql /var/run/mysqld/
[root@*****libexec]# sudo chmod g+w /var/run/mysqld/
[root@*****libexec]# /etc/init.d/mysqld start
Timeout error occurred trying to start MySQL Daemon.
Starting MySQL:                       [FAILED]

Also, /var/run/mysqld/mysqld.pid doesn't exist...
Do I need to create it?
I was expecting that the script was already trying to create it.

Am I wrong?

I checked on my other servers that have MySQL working fine...they don't have mysqld.pid - not sure what that means.
I tried creating it...then I ran /etc/init.d/mysql start...then it vanished.
So I am thinking it doesn't exist until the script runs (process ID would only be of use then right?).

> **beno1990 said:**
> Try:

```

sudo chgrp mysql /var/run/mysqld/
sudo chmod g+w /var/run/mysqld/

```

It might also need you to change the permissions of the PID file itself. If so:

```

sudo chgrp mysql /var/run/mysqld/mysqld.pid
sudo chmod g+w /var/run/mysqld/mysqld.pid

```

---

### Post by beno1990 on 2009-02-10
Has the error shown by tail -f /var/log/mysqld.log changed since you changed the permissions on the folder?

---

### Post by SterLo on 2009-02-10
tail -f /var/log/mysqld.log
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
090210 16:27:53  InnoDB: Starting log scan based on checkpoint at
InnoDB: log sequence number 0 43655.
InnoDB: Doing recovery: scanned up to log sequence number 0 43655
090210 16:27:53  InnoDB: Started; log sequence number 0 43655
090210 16:27:53 [ERROR] /usr/libexec/mysqld: Can't create/write to file '/var/run/mysqld/mysqld.pid' (Errcode: 13)
090210 16:27:53 [ERROR] Can't start server: can't create PID file: Permission denied
090210 16:27:53  mysqld ended

> **beno1990 said:**
> Has the error shown by tail -f /var/log/mysqld.log changed since you changed the permissions on the folder?

---

### Post by y@w on 2009-02-10
Maybe try creating the file and giving the proper permissions?

> touch /var/run/mysqld/mysqld.pid
chown mysql:mysql /var/run/mysqld/mysqld.pid

---

### Post by SterLo on 2009-02-11
Already tried that.
I create the file and then run MySQL...then it bombs...and then the file is gone.

A PID file just has a number in it...so I think it's created on the fly.

Like I said - I checked on other servers and it isn't in existence...me thinks that 

[root@***** ~]# touch /var/run/mysqld/mysqld.pid
[root@***** ~]# chown mysql:mysql /var/run/mysqld/mysqld.pid
[root@***** ~]# /etc/init.d/mysqld start
Timeout error occurred trying to start MySQL Daemon.
Starting MySQL:                                            [FAILED]
[root@***** ~]# ls /var/run/mysqld/
[root@***** ~]#


> **y@w said:**
> Maybe try creating the file and giving the proper permissions?

---

### Post by y@w on 2009-02-11
mysql isn't zombied is it?

---

### Post by SterLo on 2009-02-11
Nope:

[root@***** ~]# ps aux | awk '{ print $8 " " $2 }' | grep -w Z
[root@***** ~]#


> **y@w said:**
> mysql isn't zombied is it?

---

### Post by SterLo on 2009-02-11
For some reason it has just started working...for no reason as far as I can tell.

Looks like someone else in the office took a look at it and figured it out.

They said it was a permissions issue in the /var/run folder.

BAH!

---

### Post by hyper_ch on 2009-02-11
remove and resinstall mysql server.
What are the permissions of the mysqld folder? mine are:

```

drwxr-xr-x  2 mysql      root         80 2009-02-09 20:54 mysqld

```

---

### Post by SterLo on 2009-02-11
Removing and reinstalling isn't really an option.
But like I said it is solved.
I believe the ownership was changed to root:mysql for mysqld and that fixed it.

I know what you're thinking..."it's running as mysql though...why would that fix it?"
Honestly...I don't know...but it's working...and I'm happy.
So RAWR!

> **hyper_ch said:**
> remove and resinstall mysql server.
What are the permissions of the mysqld folder? mine are:

```

drwxr-xr-x  2 mysql      root         80 2009-02-09 20:54 mysqld

```

---


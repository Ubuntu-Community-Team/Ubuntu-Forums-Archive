---
title: "MySWL fails on startup"
date: 2010-07-18
forum: Server Platforms
---

### Post by Stoneface on 2010-07-18
I cannot get MySQL to start on startup. Every time I need to run the following command from the command line to get it going: ```
start mysql
```. If I try to use MySQL from the command line before starting MySQL I get ```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
``` How to resolve this once and for all

---

### Post by Stoneface on 2010-07-18
Will try ```
sudo update-rc.d -f mysql remove
sudo update-rc.d mysql defaults
``` and reboot now.

---

### Post by Stoneface on 2010-07-18
Did not help. After booting into Maverick Meerkat (in VMWare Fusion box) MySQL had not started up properly. In the MySQL log there was almost no data:```
$ cat /var/log/mysql/error.log
100715 16:38:02 [Note] /usr/sbin/mysqld: Normal shutdown

100715 16:38:03 [Note] Event Scheduler: Purging the queue. 0 events
100715 16:38:04  InnoDB: Starting shutdown...
```

And in syslog I found:```
$ tail /var/log/syslog
Jul 18 09:28:53 ubuntu tpvmlpd[2021]: bad device "/dev/**" given
Jul 18 09:29:08 ubuntu tpvmlpd[2025]: bad device "/dev/**" given
Jul 18 09:29:23 ubuntu tpvmlpd[2026]: bad device "/dev/**" given
Jul 18 09:29:38 ubuntu tpvmlpd[2028]: bad device "/dev/**" given
Jul 18 09:29:53 ubuntu tpvmlpd[2031]: bad device "/dev/**" given
Jul 18 09:30:08 ubuntu tpvmlpd[2034]: bad device "/dev/**" given
Jul 18 09:30:23 ubuntu tpvmlpd[2035]: bad device "/dev/**" given
Jul 18 09:30:38 ubuntu tpvmlpd[2038]: bad device "/dev/**" given
Jul 18 09:30:53 ubuntu tpvmlpd[2041]: bad device "/dev/**" given
```

Just realized there is nu file /var/run/mysqld/mysqld.socket nor does the directory mysqld exits. I wonder why..

---

### Post by Stoneface on 2010-07-20
I did: 
```

me@ubuntu:/var/run/mysqld$ sudo touch mysqld.sock
me@ubuntu:/var/run/mysqld$ ls -l
total 0
-rw-r--r-- 1 root root 0 2010-07-20 01:44 mysqld.sock
me@ubuntu:/var/run/mysqld$ sudo chown mysql:mysql mysqld.sock
me@ubuntu:/var/run/mysqld$ ls -l
total 0
-rw-r--r-- 1 mysql mysql 0 2010-07-20 01:44 mysqld.sock
me@ubuntu:/var/run/mysqld$ sudo chmod 755 mysqld.sock
me@ubuntu:/var/run/mysqld$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)
```
So a different error (number 13) now. But starting MySQL manually no longer works until I remove manually made mysqld directory and startup mysql using ```
sudo start mysql
``` And then mysqls is magically created in /var/run:```
me@ubuntu:/var/run$ ls -l | grep mysqld
drwxr-xr-x 2 mysql      root         60 2010-07-20 01:54 mysqld
me@ubuntu:/var/run$ cd mysqld
me@ubuntu:/var/run/mysqld$ ls -l
total 0
srwxrwxrwx 1 mysql mysql 0 2010-07-20 01:54 mysqld.sock

``` So why is this removed on reboot?

---

### Post by Stoneface on 2010-07-20
Somewhat older errors found in syslog:
```

$ cat /var/log/syslog | grep mysql
Jul 20 01:54:08 ubuntu kernel: [ 6086.630194] type=1400 audit(1279616048.377:20):  operation="profile_replace" pid=2610 name="/usr/sbin/mysqld" pid=2610 comm="apparmor_parser"
Jul 20 01:54:08 ubuntu init: mysql post-start process (2615) terminated with status 2
Jul 20 01:54:08 ubuntu kernel: [ 6086.923361] type=1400 audit(1279616048.665:21):  operation="getattr" pid=2614 parent=1 profile="/usr/sbin/mysqld" name="/usr/" pid=2614 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jul 20 01:54:08 ubuntu kernel: [ 6086.923386] type=1400 audit(1279616048.665:22):  operation="getattr" pid=2614 parent=1 profile="/usr/sbin/mysqld" name="/var/" pid=2614 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```

Start wondering if it is apparmor

---

### Post by Stoneface on 2010-07-20
Checking [http://ubuntuforums.org/showthread.php?t=977830](http://ubuntuforums.org/showthread.php?t=977830)

---

### Post by Stoneface on 2010-07-21
I fixed it with help as followed. I added ```
service mysql start
``` above the "exit 0" line in my /etc/rc.local and made it executable with ```
chmod +x /etc/rc.local
```. I did all these commands as sudouser.

---


---
title: "Mysql dpkg error"
date: 2016-02-25
forum: Ubuntu/Debian BASED
---

### Post by simon35 on 2016-02-25
Hi all,

I've got a totally fresh install of Elementary OS (Freya), I am posting here because I believe my issue to be more generic than the OS being part of the problem.

 I have successfully installed Apache2 and PHP 5.6. However the mysql install seems to fail

With a simple apt-get install mysql-server mysql-client

I get through the password setup, and then it comes back to terminal and almost finishes the process, then the error I receive is : dpkg: error processing package mysql-server-5.6 (--configure)

and here is the output from the last part of the install:

```
2016-02-24 22:48:16 9597 [Note] InnoDB: Shutdown completed; log sequence number 1625987
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.6 (--configure):
subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
mysql-server-5.6
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have looked at various 'solutions' across forums and helpdesks and a lot of users have solved this by upping the RAM on their VM. I am not running a VM and my computer has 8GB RAM and 4GB swap.
Here are the necessary specs from my machine:

```

/ 18GB
/home 28GB
swap 4GB
```

and from free: (apologies for formatting!)

```
...............................total.........used........free.... shared.buffers...cached
.................. Mem: 8119632 2838764 5280868 21752 103068 1955740
-/+ buffers/cache:  779956 7339676
..................Swap: 3905532 000000 3905532
```

I also tried the solution from this post:
[http://stackoverflow.com/a/18456553/5000727](http://stackoverflow.com/a/18456553/5000727)
Sadly this also did not work.

I also edited the /etc/mysql/conf.d/mysql.cnf and added:

```
[mysqld]
max_connections = 20
```

which was another suggestion, but nothing.
finally I tried the dpkg

```
simon@simon-MS-7821:/$ sudo dpkg --configure -a
Setting up mysql-server-5.6 (5.6.28-0ubuntu0.14.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.6 (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
mysql-server-5.6
```

I have absolutely no idea what to do any more it's driving me insane and I really need mysql! I hope one of you brilliant people out there may know how to fix this.
Many Thanks

---

### Post by howefield on 2016-02-25
Moved to the "*Ubuntu/Debian BASED*" forum.

---


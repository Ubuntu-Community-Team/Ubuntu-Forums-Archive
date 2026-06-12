---
title: "can't reinstall mysql-server after power failure during aptitude safe-upgrade"
date: 2010-06-02
forum: Server Platforms
---

### Post by snek on 2010-06-02
A week or so ago I ran an aptitude safe-upgrade and while it was updating mysql I suffered a power-failure. Now, this never really happens in Holland but of course this once it happened at the worst possible time.

I've tried a lot of different things to get mysql working again, but am running into all kinds of problems. First mysql won't shut off properly (it does startup with the computer but I can't connect to it at all) during an aptitude purge. If I kill the process mysql seems to purge properly, but I guess this is not the case because I wasn't able to install it then. 

Things seem to have gone a bit more smoothly this time, however:
```

snek@snek-server:~$ sudo aptitude install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  mysql-server mysql-server-5.1{a} mysql-server-core-5.1{a}
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.2MB of archives. After unpacking 29.4MB will be used.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
Get:1 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server-core-5.1 5.1.41-3ubuntu12.1 [4,999kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server-5.1 5.1.41-3ubuntu12.1 [7,103kB]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-server 5.1.41-3ubuntu12.1 [93.1kB]
Fetched 12.2MB in 3s (3,411kB/s)
Preconfiguring packages ...
Selecting previously deselected package mysql-server-core-5.1.
(Reading database ... 350845 files and directories currently installed.)
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.41-3ubuntu12.1_amd64.deb) ...
Selecting previously deselected package mysql-server-5.1.
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.41-3ubuntu12.1_amd64.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.41-3ubuntu12.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12.1) ...
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.1) ...
100602 11:35:33 [Note] Plugin 'FEDERATED' is disabled.
100602 11:35:33  InnoDB: Started; log sequence number 0 44233
100602 11:35:33  InnoDB: Starting shutdown...
100602 11:35:34  InnoDB: Shutdown completed; log sequence number 0 44233
start: Job failed to start

Setting up mysql-server (5.1.41-3ubuntu12.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

snek@snek-server:~$ ps aux |grep mysql
snek     21854  0.0  0.0   7616   912 pts/1    S+   11:36   0:00 grep --color=auto mysql

```As you can see mysql didn't start though...

From the syslog while trying a sudo service mysql start a few times:
```

Jun  2 12:49:43 snek-server init: mysql pre-start process (8610) terminated with status 1
Jun  2 12:49:45 snek-server init: mysql pre-start process (8651) terminated with status 1
Jun  2 12:49:45 snek-server init: mysql pre-start process (8655) terminated with status 1
Jun  2 12:49:46 snek-server init: mysql pre-start process (8677) terminated with status 1

```

I once emptied the whole /var/lib/mysql directory in an effort to purge mysql completely from the system. Could that be what's causing the problem? If so, how do I fix this? :)

---

### Post by Maleeq on 2010-06-13
I had a similar problem after I reinstalled my system. I got it to work following this link: 
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318)

Hope it helps out.

---

### Post by snake_eyes on 2011-03-22
I have the same problem how I can solved it?

Please note that the my.cnf is missing in /etc

---


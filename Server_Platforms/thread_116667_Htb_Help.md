---
title: "Htb Help"
date: 2006-01-13
forum: Server Platforms
---

### Post by mirza.k on 2006-01-13
[Kemayoran] root@tequila:/etc/sysconfig/htb# uname -a
Linux tequila 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

[Kemayoran] root@tequila:/etc/sysconfig/htb# ls -al
total 48
drwxr-xr-x  2 root root 416 2006-01-13 20:59 .
drwxr-xr-x  3 root root  96 2006-01-06 17:37 ..
-rw-r--r--  1 root root   6 2006-01-06 20:06 eth0
-rw-r--r--  1 root root  65 2006-01-11 18:59 eth0-2:101
-rw-r--r--  1 root root  65 2006-01-11 18:59 eth0-2:102
-rw-r--r--  1 root root  65 2006-01-11 18:59 eth0-2:103
-rw-r--r--  1 root root  65 2006-01-11 18:59 eth0-2:104
-rw-r--r--  1 root root  25 2006-01-06 20:06 eth0-2.root
-rw-r--r--  1 root root   6 2006-01-06 20:09 eth1
-rw-r--r--  1 root root  66 2006-01-11 19:00 eth1-2:101
-rw-r--r--  1 root root  66 2006-01-11 19:00 eth1-2:102
-rw-r--r--  1 root root  66 2006-01-11 19:00 eth1-2:103
-rw-r--r--  1 root root  66 2006-01-11 19:00 eth1-2:104
-rw-r--r--  1 root root  26 2006-01-06 20:10 eth1-2.root

you can see the entry of that file at sat-c[dot]net\server\htb [http://www.sat-c.net/server/htb/](http://www.sat-c.net/server/htb/)

when i type :
[Kemayoran] root@tequila:/etc/sysconfig/htb# htb compile
/sbin/tc qdisc del dev eth0 root
/sbin/tc qdisc add dev eth0 root handle 1 htb default 0 r2q 1

/sbin/tc qdisc del dev eth1 root
/sbin/tc qdisc add dev eth1 root handle 1 htb default 0 r2q 1

find: warning: you have specified the -maxdepth option after a non-option argument (, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument (, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

/sbin/tc class add dev eth0 parent 1: classid 1:2 htb rate 64Kbit

/sbin/tc class add dev eth0 parent 1:2 classid 1:101 htb rate 32Kbit ceil 64Kbit
/sbin/tc qdisc add dev eth0 parent 1:101 handle 101 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth0 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.101 classid 1:101

/sbin/tc class add dev eth0 parent 1:2 classid 1:102 htb rate 32Kbit ceil 64Kbit
/sbin/tc qdisc add dev eth0 parent 1:102 handle 102 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth0 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.102 classid 1:102

/sbin/tc class add dev eth0 parent 1:2 classid 1:103 htb rate 32Kbit ceil 64Kbit
/sbin/tc qdisc add dev eth0 parent 1:103 handle 103 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth0 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.103 classid 1:103

/sbin/tc class add dev eth0 parent 1:2 classid 1:104 htb rate 32Kbit ceil 64Kbit
/sbin/tc qdisc add dev eth0 parent 1:104 handle 104 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth0 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.104 classid 1:104

/sbin/tc class add dev eth1 parent 1: classid 1:2 htb rate 128Kbit

/sbin/tc class add dev eth1 parent 1:2 classid 1:101 htb rate 64Kbit ceil 128Kbit
/sbin/tc qdisc add dev eth1 parent 1:101 handle 101 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth1 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.101 classid 1:101

/sbin/tc class add dev eth1 parent 1:2 classid 1:102 htb rate 64Kbit ceil 128Kbit
/sbin/tc qdisc add dev eth1 parent 1:102 handle 102 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth1 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.102 classid 1:102

/sbin/tc class add dev eth1 parent 1:2 classid 1:103 htb rate 64Kbit ceil 128Kbit
/sbin/tc qdisc add dev eth1 parent 1:103 handle 103 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth1 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.103 classid 1:103

/sbin/tc class add dev eth1 parent 1:2 classid 1:104 htb rate 64Kbit ceil 128Kbit
/sbin/tc qdisc add dev eth1 parent 1:104 handle 104 sfq perturb 10 quantum 1500
/sbin/tc filter add dev eth1 parent 1:0 protocol ip prio 100 u32 match ip dst 192.168.1.104 classid 1:104

[Kemayoran] root@tequila:/etc/sysconfig/htb# htb start
find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

==== AND ====


[Kemayoran] root@tequila:/etc/sysconfig/htb# htb start
find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

====
====
whats worng with my htb ?

---


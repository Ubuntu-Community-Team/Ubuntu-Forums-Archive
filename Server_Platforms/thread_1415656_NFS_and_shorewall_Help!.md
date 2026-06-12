---
title: "NFS and shorewall Help!"
date: 2010-02-25
forum: Server Platforms
---

### Post by BarryDocks on 2010-02-25
I have successfully configured some NFS shares on my ubuntu server 8.04 by following this guide:
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

my problem is that it only works with shorewall disabled.  I have followed this guide to no avail:
[http://wiki.debian.org/SecuringNFS]("http://wiki.debian.org/SecuringNFS")

the relavent part of syslog:
```
Feb 25 08:37:31 server64 kernel: [   40.822892] Shorewall:lan2fw:REJECT:IN=eth1 OUT= MAC=00:19:99:0d:65:35:00:16:44:e7:a1:8c:08:00 SRC=10.10.64.17 DST=10.10.64.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=25547 DF PROTO=TCP SPT=40572 DPT=111 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 25 08:37:42 server64 kernel: [   52.264757] Shorewall:lan2fw:REJECT:IN=eth1 OUT= MAC=00:19:99:0d:65:35:00:16:44:e7:a1:8c:08:00 SRC=10.10.64.17 DST=10.10.64.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=4099 DF PROTO=TCP SPT=46807 DPT=111 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 25 08:37:48 server64 kernel: [   58.252795] Shorewall:lan2fw:REJECT:IN=eth1 OUT= MAC=00:19:99:0d:65:35:00:16:44:e7:a1:8c:08:00 SRC=10.10.64.17 DST=10.10.64.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=4700 DF PROTO=TCP SPT=46807 DPT=111 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 25 08:37:54 server64 kernel: [   64.242648] Shorewall:lan2fw:REJECT:IN=eth1 OUT= MAC=00:19:99:0d:65:35:00:16:44:e7:a1:8c:08:00 SRC=10.10.64.17 DST=10.10.64.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=5305 DF PROTO=TCP SPT=46807 DPT=111 WINDOW=5840 RES=0x00 SYN URGP=0 
```

Output of rpcinfo
```
rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32765  status
    100024    1   tcp  32765  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  42794  nlockmgr
    100021    3   udp  42794  nlockmgr
    100021    4   udp  42794  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  51094  nlockmgr
    100021    3   tcp  51094  nlockmgr
    100021    4   tcp  51094  nlockmgr
    100005    1   udp  32767  mountd
    100005    1   tcp  32767  mountd
    100005    2   udp  32767  mountd
    100005    2   tcp  32767  mountd
    100005    3   udp  32767  mountd
    100005    3   tcp  32767  mountd

```

relevant Shorewall rules added:
```
# Allow nfs mounts to local network
ACCEPT	fw	lan	udp	111
ACCEPT	fw	lan	tcp	111
ACCEPT	fw	lan	tcp	2049
ACCEPT	fw	lan	udp	2049
ACCEPT	fw	lan	tcp	32765:32769
ACCEPT	fw	lan	udp	32765:32769
```

I would be grateful for any help!

---

### Post by BarryDocks on 2010-02-25
Solved, just had to create reciprocal rules to access the firewall from ley LAN.  The appropriate shorewall rules now look like:
```
# Allow nfs mounts to local network
ACCEPT	fw	lan	udp	111
ACCEPT	fw	lan	tcp	111
ACCEPT	fw	lan	tcp	2049
ACCEPT	fw	lan	udp	2049
ACCEPT	fw	lan	tcp	32765:32769
ACCEPT	fw	lan	udp	32765:32769
ACCEPT	lan	fw	udp	111
ACCEPT	lan	fw	tcp	111
ACCEPT	lan	fw	tcp	2049
ACCEPT	lan	fw	udp	2049
ACCEPT	lan	fw	tcp	32765:32769
ACCEPT	lan	fw	udp	32765:32769
```

Not sure how secure this is, any comments would be great?

---


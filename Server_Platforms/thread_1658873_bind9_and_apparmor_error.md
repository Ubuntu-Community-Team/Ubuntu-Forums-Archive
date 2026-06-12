---
title: "bind9 and apparmor error"
date: 2011-01-03
forum: Server Platforms
---

### Post by klockren on 2011-01-03
Hi,
using Ubuntu Server 10.10 x86_64 on this machine.
It is used as a master DNS server for my domain.
We have migrated it to Ubuntu from Gentoo.
The problem is that AppArmor is spamming /var/log/syslog
```
Jan  3 14:38:40 hydra kernel: [2154828.893409] type=1400 audit(1294061920.141:660146): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/var/log/named_querylog" pid=15397 comm="named" requested_mask="c" denied_mask="c" fsuid=103 ouid=103
```

The zone files reside in /etc/bind/ and we have not changed anything in /etc/apparmor.d/usr.sbin.named .

We don't want to just uninstall apparmor, but how do we adjust its settings correctly?

---

### Post by blejzz on 2011-01-09
did you resolve the problem? I've got the same problem...  and i have bind running only for a local network domain. 
I've also noticed that after some time the domain stops working and if i restart the service everything is back to normal.

---

### Post by klockren on 2011-01-10
No, it is still unresolved for us.
But the service is working...

---

### Post by MatsB on 2011-01-29
Got the same problem when activating logging in BIND 9.7.1-P2 on Ubuntu 10.10 server

```

Jan 29 07:24:14 server kernel: [379508.124800] type=1400 audit(1296282254.692:255): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/named" name="/var/log/query.log" pid=19618 comm="named" requested_mask="ac" denied_mask="ac" fsuid=103 ouid=103

```

/etc/bind/named.conf.local
```

logging {
    channel query.log {
        file "/var/log/query.log" versions 7 size 2G;
        print-category yes;
        print-severity yes;
        print-time yes;
    };

    category queries { query.log; };
};

```

server:/$ ls -l /etc/bind/
```

-rw-r--r-- 1 root root  601 2010-08-04 22:39 bind.keys
-rw-r--r-- 1 root root  237 2010-08-04 22:39 db.0
-rw-r--r-- 1 root root  271 2010-08-04 22:39 db.127
-rw-r--r-- 1 root root  237 2010-08-04 22:39 db.255
-rw-r--r-- 1 root root  353 2010-08-04 22:39 db.empty
-rw-r--r-- 1 root root  270 2010-08-04 22:39 db.local
-rw-r--r-- 1 root root 2994 2010-08-04 22:39 db.root
-rw-r--r-- 1 root bind  463 2010-08-04 22:39 named.conf
-rw-r--r-- 1 root bind  490 2010-08-04 22:39 named.conf.default-zones
-rw-r--r-- 1 root bind  478 2011-01-29 07:17 named.conf.local
-rw-r--r-- 1 root bind  567 2011-01-29 07:04 named.conf.options
-rw-r----- 1 bind bind   77 2011-01-23 21:42 rndc.key
-rw-r--r-- 1 root root 1317 2010-08-04 22:39 zones.rfc1918

```

server:/$ ls -l /var/log
```

-rw-r--r-- 1 bind     root             0 2011-01-29 07:11 query.log

```

---

### Post by MatsB on 2011-01-29
Found a solution for this error

/etc/apparmor.d/usr.sbin.named expect log files in /var/log/named/
So I created /var/log/named and moved the query.log into /var/log/named/

Named now log to query.log

```

drwxr-xr-x 2 bind     root          4096 2011-01-29 17:30 named

```

---

### Post by jrobiii on 2011-07-17
I know this is a bit late, but I had a very similar problem: 
```
[FONT=Courier New]Jul 16 23:02:55 fs01 dhcpd: Unable to add forward map from mustang.home.local. to 192.168.10.198: timed out
Jul 16 23:02:55 fs01 kernel: [ 3398.358618] type=1400 audit(1310875375.000:27): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/zones/home.local.db.jnl" pid=2758 comm="named" requested_mask="c" denied_mask="c" fsuid=117 ouid=117[/FONT]

```I found the following lines in /etc/apparmor.d/usr.sbin.named:
```

[FONT=Courier New]# /var/lib/bind is for dynamically updated zone (and journal) files.
  /var/lib/bind/** rw,
  /var/lib/bind/ rw,
[/FONT]  
```After removing my palm from my forehead I moved /etc/bind/zones to /var/lib/bind/zones and modified /etc/bind/named.conf.local to reflect the file move... worked like a champ.

---


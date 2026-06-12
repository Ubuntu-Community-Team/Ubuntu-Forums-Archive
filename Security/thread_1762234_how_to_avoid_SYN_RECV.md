---
title: "how to avoid SYN_RECV"
date: 2011-05-18
forum: Security
---

### Post by cakka on 2011-05-18
Hello,

i am learning ubuntu and my server get SYN Flood
how to clear this problem ?

i have try :
```
echo 1 > /proc/sys/net/ipv4/tcp_syncookies

on /etc/sysctl.conf

net.ipv4.tcp_syncookies = 1

then

/sbin/sysctl -p /etc/sysctl.conf


```

but when i check using :

```
/sbin/sysctl -a
```

it still : 
```
net.ipv4.tcp_syncookies = 0
```

please help me, thanks

---

### Post by n0my on 2011-08-22
I use floodmon and it works nicely to stop these attacks.

[http://floodmon.sourceforge.net/](http://floodmon.sourceforge.net/)

---


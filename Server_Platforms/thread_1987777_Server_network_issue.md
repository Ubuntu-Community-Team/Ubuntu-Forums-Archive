---
title: "Server network issue"
date: 2012-05-26
forum: Server Platforms
---

### Post by roffisserver on 2012-05-26
So I have had this server for about 3 weeks and suddenly when I try to install webmin it tries to connect but fails every time. So I tried a reinstall when I got to the network setup part it said that it couldn't find the connection. I have a lot of code on server and I would hate to lose it. I would be grateful for help.:confused:

---

### Post by darkod on 2012-05-26
Reinstall what, webmin or the server OS?

---

### Post by volkswagner on 2012-05-26
Best to eliminate hardware issue first.

Try booting a live CD and see if network connection functions.  If not check cable, router/switch port, etc.

If all is well, post output of:

```
lspci
```

```
ifconfig
```

```
cat /etc/network/interfaces
```

```
cat /etc/resolv.conf
```

```
route
```

---

### Post by roffisserver on 2012-05-26
I meant the Server OS(Ubuntu Server). Oh and yes I will try booting from a live cd

---

### Post by darkod on 2012-05-26
I don't want to sound harsh, but did you try to troubleshoot first a little? Did you try to ping an internal and an external IP? Did you try to ping an external domain?

Sounds like connectivity issue, but the first thing you do shouldn't be a reinstall of the OS.

So, because you said you "tried a reinstall", what is the current situation? Does the old OS still boot? If you never did a reinstall I guess you should still have the old OS but it's really unclear.

I would focus on the ping first, like:
ping 8.8.8.8
ping [www.yahoo.com](www.yahoo.com)

Also try pinging your local router IP, what ever it is.

---

### Post by spynappels on 2012-05-26
> **roffisserver said:**
> I have a lot of code on server and I would hate to lose it.

A reinstall of the OS may not have helped with that...


Pinging the loopback interface will at least tell you if the TCP stack is ok.

---

### Post by roffisserver on 2012-05-26
Yes I still have the original OS. I will try pinging something

---


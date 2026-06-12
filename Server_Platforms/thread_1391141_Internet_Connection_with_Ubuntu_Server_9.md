---
title: "Internet Connection with Ubuntu Server 9"
date: 2010-01-26
forum: Server Platforms
---

### Post by sfox@duncan-oil.com on 2010-01-26
hi all i have a ubuntu server setup for static ip address and having troubles getting to the internet. ultimatly i am trying to get openvpn to install and found out that i cant even ping [www.google.com]("http://www.google.com"). i can ping another computer on the network with full feedback but once i try [www.google.com]("http://www.google.com") i get no response. any thoughts?

---

### Post by cdenley on 2010-01-26
Is it a name resolution problem? Did you configure a nameserver?
```

host google.com
nc -z -v 74.125.95.104 80
cat /etc/resolv.conf

```

---

### Post by computer13137 on 2010-01-26
Perhaps an easier way to determine if it's a name server issue, is to try pinging a well known Internet IP address, such as 4.2.2.1 or 208.67.222.222.  If one of those IPs is responding to pings, then the problem is most definitely a name resolution issue.

-Kirk

---

### Post by Iowan on 2010-01-26
Is the server the gateway? Also check results of **route -n**.

---


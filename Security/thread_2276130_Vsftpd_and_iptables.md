---
title: "Vsftpd and iptables"
date: 2015-04-30
forum: Security
---

### Post by Renaissance2011 on 2015-04-30
Hello friends,

I'm build my own file storage server (Ubuntu 14.04). Uploading goes trough Vsftpd. However, the firewall (iptables) will not allow a connection to outside.

My iptables rules looks like that:

INPUT DROP
FOWARD DROP
OUTSIDE DROP

-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp --dport 21 -j ACCEPT
-A INPUT -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT

and /etc/modules looks like that:
ip_conntrack_ftp

What is wrong ?

---

### Post by Doug S on 2015-04-30
By "OUTSIDE" I assume you mean "OUTPUT". You need to deal with that side of things. Start by setting it to ACCEPT.
You should also allow the local interface:```
-A INPUT -i lo -j ACCEPT
```

---


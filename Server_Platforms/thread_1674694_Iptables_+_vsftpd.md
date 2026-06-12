---
title: "Iptables + vsftpd"
date: 2011-01-24
forum: Server Platforms
---

### Post by alfamuzjak on 2011-01-24
Can someone help me with firewalling vsftpd with iptables?(ports 21,20;anonymous upload,download..).
How i can cover all that?

---

### Post by alfamuzjak on 2011-01-26
Is this enough?!

loading two iptables modules:
```
# modprobe ip_conntrack
# modprobe ip_conntrack_ftp
```

iptables rules for incoming request on port 21 (open port 21)

```
iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d 202.54.1.20 --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp -s 202.54.1.20 --sport 21 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```

AND:

```
iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d 202.54.1.20 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp -s 202.54.1.20 --sport 1024:65535 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```
 
AND:

```
iptables -A OUTPUT -p tcp -s 202.54.1.20 --sport 20 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d 202.54.1.20 --dport 20 -m state --state ESTABLISHED -j ACCEPT

```

---


---
title: "iptables -m recent conflicting"
date: 2008-10-19
forum: Security
---

### Post by Shwick2 on 2008-10-19
Running ubuntu 8.04.

I'm using the recent module in two different chains SSH_PROTECT and FTP_PROTECT.  What I want is for an ip to be allowed to make a new connection to SSH port 22 once every 60 seconds and FTP port 21 once every 30 seconds.

```
iptables -N SSH_PROTECT
iptables -A SSH_PROTECT -m recent --set
iptables -A SSH_PROTECT -m recent --update --seconds 60 --hitcount 2 -j DROP
iptables -A SSH_PROTECT -j DROP

iptables -N FTP_PROTECT
iptables -A FTP_PROTECT -m recent --set
iptables -A FTP_PROTECT -m recent --update --seconds 30 --hitcount 2 -j DROP
iptables -A FTP_PROTECT -j DROP

iptables -A INPUT 
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -p tcp --dport 22 -j SSH_PROTECT
iptables -A INPUT -m state --state NEW -i eth1 -p tcp --dport 21 -j FTP_PROTECT
iptables -P INPUT DROP
```

What actually happens is when an ip makes a new connection to either port 21 or 22, they cannot connect to port 21 for the next 30 seconds or port 22 for the next 60 seconds.

The recent module is only storing a session for an ip.  I need it to store a session for an ip/port, or one session for each chain it's in.  Is this possible?

---

### Post by kevdog on 2008-10-20
Yes you can do this by using the name directive like the following:

iptables -N SSH_PROTECT
iptables -A SSH_PROTECT -m recent --set --name SSH
iptables -A SSH_PROTECT -m recent --update --seconds 60 --hitcount 2 --name SSH -j DROP
iptables -A SSH_PROTECT -j DROP

Take a look here for more info:

[http://www.ducea.com/2006/06/28/using-iptables-to-block-brute-force-attacks/](http://www.ducea.com/2006/06/28/using-iptables-to-block-brute-force-attacks/)

---

### Post by uljanow on 2008-10-20
AFAIK the module nf_conntrack_ftp needs to be loaded in order to use the state module with the above rules.

---

### Post by Shwick2 on 2008-10-20
Thanks thats exactly what I needed it works now.

---

### Post by kevdog on 2008-10-21
Sorry about not listing the contrack modules -- I thought you had not listed your entire script, so I assumed there were other parts that you had omitted.

---


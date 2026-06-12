---
title: "How to unblock outgoing HTTP and HTTPS traffic in iptables?"
date: 2012-11-08
forum: Security
---

### Post by THPubs on 2012-11-08
With the following iptable rules, I was unable to do an apt update and ping a website. Whats wrong with the rules? How to fix it? What is the exact rule to fix it?

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:325 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

### Post by JKyleOKC on 2012-11-08
It looks as if you're only allowing incoming traffic addressed to port 325, and dropping all other packets.

Search this forum for threads dealing with iptables to see a wide range of possible solutions. It can be very simple, or very complicated. Many folk find that using "ufw" or "gufw" is simpler than trying to create a customized set of rules directly...

---

### Post by sammiev on 2012-11-08
This may give you a little info about the different ways of handling [firewalls]("http://ubuntuforums.org/showthread.php?t=1876124").

---

### Post by THPubs on 2012-11-09
> **JKyleOKC said:**
> It looks as if you're only allowing incoming traffic addressed to port 325, and dropping all other packets.

Search this forum for threads dealing with iptables to see a wide range of possible solutions. It can be very simple, or very complicated. Many folk find that using "ufw" or "gufw" is simpler than trying to create a customized set of rules directly...

Im in an OpenVZ server :) No gui and no ufw :(

---

### Post by CharlesA on 2012-11-09
iptables is the way to go.
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---


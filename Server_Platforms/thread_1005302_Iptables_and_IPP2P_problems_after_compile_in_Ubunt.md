---
title: "Iptables and IPP2P problems after compile in Ubuntu Hardy"
date: 2008-12-08
forum: Server Platforms
---

### Post by chr05210084 on 2008-12-08
Guys I tried to install layer7 and IPP2P, I installed IPP2P using patch-o-matic-ng, I compiled a new kernel 2.6.25 and iptables 1.4.0. The problem is when I tried to run

```
iptables -m ipp2p --help
```

it returns an error message that says: 

```
iptables v1.4.0: Couldn't load match 'ipp2p':(null)
```

I can't use IPP2P using iptables command, I tried loading the ipp2p module using modprobe and tried the command again but I got the same error. Please help me guys. I'm using Ubuntu Hardy Heron server. Thanks.

---

### Post by Andros87 on 2009-01-17
I also this same problem, please give easy tutorial how to install 7-layer and 1pp2p on ubuntu 8.04 or 8.10. 

th

---


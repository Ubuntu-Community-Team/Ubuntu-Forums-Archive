---
title: "Where did this IP come from?"
date: 2011-11-27
forum: Security
---

### Post by VcDeveloper on 2011-11-27
ISP: Comcast

When checking my interfaces and did a "route -n" and got this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
[COLOR=Red]**169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0**[/COLOR]
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

running two computers on my network; 1) Ubuntu,and 2) Windows 7... My IP start with a 67......... so where did this 169.254.0.0 came from and if it not suppose to be there how do I remove it?

Thanks!...

---

### Post by Doug S on 2011-11-27
the 169.254.X.X sub-net is used by Automatic Private IP Addressing. Generally, if not always, it means your were unable to get an "real" IP address via DHCP. You need to solve that underlying problem.

---

### Post by Lampi on 2011-11-27
Check out this article if you prefer to disable it:

[http://www.brennan.id.au/04-Network_Configuration.html#zeroconf](http://www.brennan.id.au/04-Network_Configuration.html#zeroconf)

---

### Post by VcDeveloper on 2011-11-27
Thanks for your help!...

---


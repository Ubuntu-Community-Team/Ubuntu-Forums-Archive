---
title: "graphical firewalls"
date: 2009-06-09
forum: Security
---

### Post by johnh10000 on 2009-06-09
Hi gang, I have just gotten broadband.  Until I installed 10.4 my local lan was fine.  With ssh, apache ftp working.

I got a router set that up so lan gets same IPs, pout my web site err sort of back.

Now connect locally fine, connect via dnydns errors like connection closed by host. WWW can't recall the error but it's like  its there but can't find it.  

When I first set my lan up I recall these issues locally, and used lokkit to resolve the problems.  Tried lokkit again no joy.

so any ideas on a graphical firewall, so I can open ports?

Something like zonealarm would be good.

Not good with fiddling with iptables.

---

### Post by johnh10000 on 2009-06-09
Something like zonealarm would be good.

Not good with fiddling with iptables.[/QUOTE]

don't worry about it gang, sorted it.  guarddog did the trick

---

### Post by lisati on 2009-06-09
Ufw?

---

### Post by prshah on 2009-06-09
```
sudo apt-get install gufw
```
then, System-Administration-Firewall configuration

---


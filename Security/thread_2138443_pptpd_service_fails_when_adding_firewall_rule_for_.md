---
title: "pptpd service fails when adding firewall rule for port 22"
date: 2013-04-24
forum: Security
---

### Post by Drenriza on 2013-04-24
So i have installed pptp vtp server service. And it is currently working as expected.

The problem is that when i add a rule to my firewall as follows
```
iptables -A INPUT -p tcp --dport 22 -i eth0 -j DROP
```

Note.
eth0 is my interface towards the WAN. And got a eth1 interface that points towards my LAN.

It drops the ssh traffic as it should, but it also drops pptp traffic on port 1723.....
So a VTP connection cannot be established, after the rule above has been added to iptables.

Has this something to do with the "-p tcp" section?

If anyone can explain to me, why the above make pptp fail.
Then that would be much appreciated.

Kind regards.

---

### Post by Drenriza on 2013-04-26
No one with any thoughts, suggestions or at the sort?

---


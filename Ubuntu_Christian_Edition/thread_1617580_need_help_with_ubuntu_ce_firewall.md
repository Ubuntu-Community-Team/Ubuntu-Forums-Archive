---
title: "need help with ubuntu_ce_firewall"
date: 2010-11-09
forum: Ubuntu Christian Edition
---

### Post by lig_15 on 2010-11-09
I can not connect to my mysql server which is running dansguadian from ubuntu ce, however, if I run:

/etc/init.d/ubuntu_ce_firewall stop

I can connect to mysql but dansguardian stops working

any ideas?

---

### Post by lig15 on 2010-11-09
nevermind I figured it out and in doing so I learned alot about iptables

iptables -A INPUT -p tcp --dport 3306 -m state --state NEW -j ACCEPT

is what allowed me access

in an unrelated topic do you know if adding

iptables -A INPUT -i eth0 -j ACCEPT

to ubuntu_ce_firewall would cause any damage? it does not seem to stop the web filtering

---

### Post by david_kt on 2010-11-09
> **lig15 said:**
> nevermind I figured it out and in doing so I learned alot about iptables

iptables -A INPUT -p tcp --dport 3306 -m state --state NEW -j ACCEPT

is what allowed me access

in an unrelated topic do you know if adding

iptables -A INPUT -i eth0 -j ACCEPT

to ubuntu_ce_firewall would cause any damage? it does not seem to stop the web filtering

It will open all ports on eth0.

DK

---


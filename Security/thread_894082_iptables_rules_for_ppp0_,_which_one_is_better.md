---
title: "iptables rules for ppp0 , which one is better?"
date: 2008-08-18
forum: Security
---

### Post by health_kxy on 2008-08-18
I use ppp to connect to internet and deny anyone connect to me.
the first rule can be that.
iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

the second can be that.
iptables -N block
iptables -A block -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A block -m state --state NEW -i ! ppp0 -j ACCEPT <--- another question?,why use ! ppp0
iptables -A block -j DROP
iptables -A INPUT -j block
iptables -A FORWARD -j block

my question is, are they the same ? which one is better?

thx all.

---


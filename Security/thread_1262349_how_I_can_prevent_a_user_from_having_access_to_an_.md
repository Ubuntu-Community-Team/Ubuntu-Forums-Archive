---
title: "how I can prevent a user from having access to an specific port on a network card?"
date: 2009-09-09
forum: Security
---

### Post by legolas_w on 2009-09-09
Hi
Thank you for reading my question.

Can someone please let me know how I can prevent a user from having access to an specific port on an specific interface?
for example username secuser, eth1 and 34700 as the port number.

Thanks

---

### Post by bodhi.zazen on 2009-09-10
sudo iptables -A INPUT -i eth1 -p tcp --dport 34700 -m owner --uid-owner secuser -j DROP
sudo iptables -A INPUT -i eth1 -p udp --dport 34700 -m owner --uid-owner secuser -j DROP

sudo iptables -A OUTPUT -o eth1 -p tcp --dport 34700 -m owner --uid-owner secuser -j DROP
sudo iptables -A OUTPUT -o eth1 -p udp --dport 34700 -m owner --uid-owner secuser -j DROP

---


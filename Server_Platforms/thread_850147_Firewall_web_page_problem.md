---
title: "Firewall web page problem"
date: 2008-07-05
forum: Server Platforms
---

### Post by hasanatacan on 2008-07-05
Hi,
I installed ubuntu server 7.10.
Used some iptables rules and configure it as an gateway. But although i deleted all firewall rules, XP clients at the office can't post data some site, for example some pages of facebook or yahoo mail when sending data. At forms.
All rules below.
Any idea??
Thanks..

iptables -F
iptables -t mangle -F
iptables -X
iptables -Z
iptables -t nat -F PREROUTING
iptables -t nat -F POSTROUTING
################
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
#Enable IP forwarding
echo "1" > /proc/sys/net/ipv4/ip_forward

---

### Post by kevdog on 2008-07-05
Can you list your firewall rules?

sudo iptables -L

---

### Post by hasanatacan on 2008-07-05
root@xxxx:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by hasanatacan on 2008-07-06
Any idea?

---


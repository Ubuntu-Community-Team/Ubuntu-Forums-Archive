---
title: "Losing Internet"
date: 2020-02-20
forum: Virtualisation
---

### Post by jaredy00 on 2020-02-20
When ever I try to run this I lose internet access

iptables -A FORWARD -o wlp3s0 -i vboxnet0 -s 192.168.56.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by wildmanne39 on 2020-02-20
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---


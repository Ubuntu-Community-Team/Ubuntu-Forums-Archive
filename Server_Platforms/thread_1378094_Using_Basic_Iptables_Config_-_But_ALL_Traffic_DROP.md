---
title: "Using Basic Iptables Config - But ALL Traffic DROPS. Pls. Help!"
date: 2010-01-11
forum: Server Platforms
---

### Post by AlexanderDGreat on 2010-01-11
Hi, I'm using Ubuntu server 9.10 with 2 NICS (Internet-router-eth0, eth1-LAN). I use iptables to generate rules for 20 computers, but when I execute the script, ALL TRAFFIC DROPS, including the server. What am I doing wrong?

```


[COLOR="Blue"]#!/bin/sh

#eth0 192.168.0.50 - connected to Internet
#eth1 192.168.1.51 - connected to LAN
#192.168.1.52 - workstation1[/COLOR]

[COLOR="Blue"]#set default policies[/COLOR]
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

[COLOR="Blue"]#flush all rules[/COLOR]
iptables -F
iptables -t nat -F

[COLOR="Blue"]#share internet connection with lan[/COLOR]
echo 1 > /proc/sys/net/ipv4/ip_forward

[COLOR="Blue"]#enable NAT[/COLOR]
iptables -t nat -A POSTROUTING -j MASQUERADE -s 192.168.1.0/24

[COLOR="Blue"]# allow ESTABLISHED and RELATED packets in all chains[/COLOR]
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

[COLOR="Blue"]#allow Internet on server 192.168.0.50 and workstation1[/COLOR]
iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -p tcp --dport 80 -s 192.168.1.52 -j ACCEPT


```

The reason I'm doing this is, I just want to open necessary ports in the server and restrict LAN usage. Pls. help. Thanks.

---

### Post by AlexanderDGreat on 2010-01-11
I'm sorry admins, I double posted on the networking and wireless category because I got confused, pls. delete this if necessary. Thanks.

---

### Post by AlexanderDGreat on 2010-01-11
Silly me, I found the answer. You just need to WAIT for the FIREWALL to TAKE EFFECT!

Thanks hope my impatience will help someone out there.

---


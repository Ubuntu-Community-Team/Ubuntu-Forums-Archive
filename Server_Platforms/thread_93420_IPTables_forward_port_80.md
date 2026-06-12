---
title: "IPTables forward port 80"
date: 2005-11-22
forum: Server Platforms
---

### Post by nverhaar on 2005-11-22
Hey all, I am having a minor drama with forwarding traffic on port 80 on my ubuntu gateway/firewall to an internal ubuntu web server.

I am currently using the following rules in IPTABLES to forward traffic to the web server, and it works great.

iptables -A FORWARD -i eth1 -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 80 -j DNAT --to-destination 10.0.0.80:80

My problem is, every connection to the web server from the outside world is being logged as the IP address of my gateway/firewall box, as opposed to logging the REAL client IP's. We need to run webalizer to determine hit counts and other statistics on our web server, however this is causing problems as all connections to the web server from the outside world are considered as a single connection. This is resulting in invalid statistics.

Does anyone know how I can somehow force the use of real IP's either with IPTABLES, or some other method?

Ive also tried running apache on the gateway/firewall machine and using the ProxyPass module to forward requests on to the internal web server, which also gave the same results.

---

### Post by LordHunter317 on 2005-11-22
It shouldn't be doing that, and that rule wouldn't cause that.  You need to post your whole ruleset.

---

### Post by nverhaar on 2005-11-22
Hope this helps, because I need to get this sorted. We really do need accurate statistics for web traffic.

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A OUTPUT -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE
iptables -A FORWARD -i eth1 -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -i eth1 -p tcp --dport 110 -j ACCEPT
iptables -A FORWARD -i eth1 -p tcp --dport 143 -j ACCEPT
iptables -A FORWARD -i eth1 -p tcp --dport 1494 -j ACCEPT
iptables -A FORWARD -i eth1 -p tcp --dport 3389 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 80 -j DNAT --to-destination 10.0.0.80:80
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 110 -j DNAT --to-destination 10.0.0.25:110
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 143 -j DNAT --to-destination 10.0.0.25:143
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 1494 -j DNAT --to-destination 10.0.0.91:1494
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 3389 -j DNAT --to-destination 10.0.0.105:3389

---

### Post by nverhaar on 2005-11-22
Actually I think I just solved the problem by turning off MASQUERADE'ing on the eth0 interface...

Now it is displaying all of the correct IP addresses as far as Apache is concerned.

---


---
title: "vnc server thru firewall"
date: 2009-02-04
forum: Server Platforms
---

### Post by xyrer on 2009-02-04
Hi, I've read many times my iptables script but I still can't find where I'm wrong, evrything works fine and there's some secutiry holes I'm aware of but will solve as soon as I know why this doesn't work.
Here's my script:

```

#!/bin/bash
INTERNET="eth0"
LAN="eth1"
AIX="eth2"
#
iptables -F
iptables -X
iptables -Z
iptables -t nat -F
#
#
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT
#
#
iptables -A INPUT -i lo -j ACCEPT
#
#
iptables -t nat -A POSTROUTING -s 192.168.2.0/24 -d 0.0.0.0/0 -j MASQUERADE
#
#
iptables -A INPUT -p icmp -j ACCEPT
#
iptables -A OUTPUT -m state --state NEW -j ACCEPT
#
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT
#
#telnet to unix server
iptables -A PREROUTING -t nat -p tcp -i $LAN --dport 23 -j DNAT --to-destination 192.168.1.1:23
iptables -A FORWARD -i $LAN -o $AIX -p tcp -m tcp --dport 23 -d 192.168.1.1 -j ACCEPT
#
#
#vnc redirect
#
iptables -A FORWARD -i $INTERNET -o $LAN -p tcp -m state --state NEW --dport 5900 -j ACCEPT
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 5900 -j DNAT --to 192.168.2.9:5900
#
#gmail
iptables -A FORWARD -i $LAN -o $INTERNET -p tcp -m tcp --dport 995 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -p tcp -m tcp --dport 993 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -p tcp -m tcp --dport 110 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -p tcp -m tcp --dport 25 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -p tcp -m tcp --dport 587 -j ACCEPT
#
#
#web browsing for some
#
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.10 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.17 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.22 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.254 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.236 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.93 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.24 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.50 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.246 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.25 -j ACCEPT
iptables -A FORWARD -i $LAN -o $INTERNET -s 192.168.2.45 -j ACCEPT
#
iptables -A INPUT -p tcp --dport 10000 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
iptables -A INPUT -i $LAN -p tcp --dport 8080 -m state --state NEW -j ACCEPT
iptables -A INPUT -i $LAN -p udp --dport 137 -m state --state NEW -j ACCEPT
iptables -A INPUT -i $LAN -p udp --dport 138 -m state --state NEW -j ACCEPT
iptables -A INPUT -i $LAN -p tcp --dport 139 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 9090 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 3306 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 5222 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 389 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 636 -m state --state NEW -j ACCEPT
iptables -A INPUT -i $LAN -p udp --dport 53 -m state --state NEW -j ACCEPT
#
#
#drop everything else
#
iptables -A INPUT -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -m state --state NEW,INVALID -j DROP
#
#
#kernel forward
#
echo 1 > /proc/sys/net/ipv4/ip_forward

```

I can't find my mistake anywhere, please someone point me out the problem.
Thanks.

---


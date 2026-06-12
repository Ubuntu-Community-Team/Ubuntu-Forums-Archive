---
title: "IP packet forwarding - how?"
date: 2006-05-29
forum: Server Platforms
---

### Post by el3ktro on 2006-05-29
Simple question: We have a 10.0.0.0 network, our gateway to the Internet is 10.0.0.1. We have a few computers with a 192.168.10.0 network though. I have one computer (ROUTER) with two network cards, one with 10.0.0.10 and one with 192.168.10.10, and I want to set 192.168.10.10 as the gateway for the computers which have an 192.168.10.0 address. The ROUTER computer has 10.0.0.1 as gateway, and I want that all traffic from 192.168.10.0 goes trough 192.168.10.10, to the other network card with 10.0.0.10 and from there to the Internet (10.0.0.1). I though enabling IP packet forwarding in /etc/sysctl.conf is enough ... but it isn't. What else do I need??

Tom

---

### Post by el3ktro on 2006-05-29
Damn I should have searched a little more. Found a solution:

```

## This script needs to be started at boot. When you made changes simply run the script manually.
## eth0 is the LAN-connected interface
## eth1 is the Internet-connected interface

# Enable IP Forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Clean up iptables (flush it)
iptables -F
iptables -t nat -F
iptables -X

# Enable IP MASQUERADING/NAT
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Set firewall policies (default behaviour)
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

# Allow all connections not from eth1
iptables -A INPUT -i ! eth1 -j ACCEPT

# Allow all ICMP connections (like ping)
iptables -A INPUT -p ICMP -j ACCEPT

# Allow all already established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

```

---

### Post by solonas33 on 2008-05-26
Thanks Tom, that was very helpfull for me!!!!!!

Sol

---


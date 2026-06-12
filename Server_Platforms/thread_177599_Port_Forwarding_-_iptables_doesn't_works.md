---
title: "Port Forwarding - iptables doesn't works"
date: 2006-05-16
forum: Server Platforms
---

### Post by zBoost on 2006-05-16
I have ubuntu x64 server and 2nd PC with windows XP. The server has 2 lan cards - eth1 (external, internet coming) and eth0 (lan, sharing internet to the 2nd windows PC with iptables MASQUERADE).

I want to forward port 80 for my apache server but something is wrong.

Using this script for iptables:

> 
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

## Make holes in the firewall for running different services

# Open HTTP (for running a web server)
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

#Forwarding
iptables -A PREROUTING -t nat -p tcp -i eth1 --dport 80 -j DNAT --to 192.168.0.2:80


eth1 - internet with static real ip
eth0 - 192.168.0.1
192.168.0.2 - windows pc

Even without any rules I type:
iptables -A PREROUTING -t nat -p tcp -i eth1 --dport 80 -j DNAT --to 192.168.0.2:80
and there is no forwarding. And when i check iptables -L, in Chain FORWARD there aren't any ip's and forwarding set. Where is the problem ?

---

### Post by NetOS on 2006-05-23
i'm have a similair problem. The thing is that:

 sudo echo 1 > /proc/sys/net/ipv4/ip_forward
 bash: /proc/sys/net/ipv4/ip_forward: Permission denied

probably this is what happens to you too.

Edit:
here's the solution:
[http://www.siliconvalleyccie.com/linux-hn/iptables-intro.htm#_Toc92808873](http://www.siliconvalleyccie.com/linux-hn/iptables-intro.htm#_Toc92808873)

---


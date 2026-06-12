---
title: "Setting up VPN in ubuntu server"
date: 2010-05-25
forum: Server Platforms
---

### Post by Nessaja on 2010-05-25
Hi all!
 
I want to set up our VPN router so that we can connect 2 branches together, I'm having trouble doing it with windows server 2003, so I thought, why not give Linux a go instead.
 
I currently have a transparent Proxy Server that has an extra network card, so maybe it could work.
 
The setup:
1x Router supplies the internet , it's ip is (192.168.0.1)
1x Router supllies VPN, it's ip is (10.0.3.2)
The proxy has 3x ethernet ports,
eth0 = 192.168.0.7
eth1 = 192.168.1.5
eth2 = 10.0.3.100
 
Thanks to benderisgreat on this forum, I've got the proxy set up to direct all port 80 traffic to 3128 (dansguardian), but now I want to combine the VPN network IPs so that PCs on this ip range (192.168.1.0/24) will be able to see pc's on the VPN ip range (10.0.3.0/24)
 
The current config that I use to forward ports to various servers looks like this:
```

#!/bin/sh
echo "Settings server rules..."
echo "Setting up port forwarding"
SQUID_SERVER="192.168.1.5"
INTERNET="eth0"
LAN_IN="eth1"
VPN="eth2"
SQUID_PORT="3128"
iptables -F
iptables -X
echo "Setting up NAT"
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
modprobe ip_conntrack
modprobe ip_conntrack_ftp
modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "Setting up IPTABLES..."
 
iptables -P OUTPUT ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT
iptables -A INPUT -i $LAN_IN -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -j ACCEPT
iptables -A INPUT -j LOG
#iptables -A INPUT -j DROP
echo "Benderisgreat additions:"
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o $INTERNET -j SNAT --to-source 192.168.0.7
iptables -P FORWARD DROP
iptables -A FORWARD -i $INTERNET -m state --state ESTABLISHED -j ACCEPT
iptables -A FORWARD -i $INTERNET -p icmp -m state --state RELATED -j ACCEPT
iptables -A FORWARD -i $LAN_IN -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT
iptables -A FORWARD -i $LAN_IN -j ACCEPT
iptables -A FORWARD -i $INTERNET -p tcp --dport 80 -d 192.168.1.9 -m state --state NEW -j ACCEPT
iptables -A FORWARD -i $INTERNET -p tcp --dport 8181 -d 192.168.1.6 -m state --state NEW -j ACCEPT
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 3308 -j DNAT --to-destination 192.168.1.9
iptables -t nat -A POSTROUTING -i $INTERNET -p tcp --dport 3308 -j SNAT --to-source :3389
iptables -A FORWARD -p tcp --sport 3389 --dport 3308 -d 192.168.1.9 -m state --state NEW -j ACCEPT
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j DNAT --to-destination 192.168.1.9
iptables -A FORWARD -p tcp --dport 80 -d 192.168.1.9 -m state --state NEW -j ACCEPT
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
 
 
echo "Special thanks to Benderisgreat from ubuntuforums.org for help setting up this script, thanks Bender!"
echo "IPTABLES configured..."
echo "Squid up and running :-)"
 
 
 

```
 
 
So now I want to combine the 10.0.3.0/24 range that comes from eth2 with the 192.168.1.0/24 range, is this even possible?
 
Here's an illustration of what I'm trying to do:
[IMG]http://img163.imageshack.us/img163/5926/linuxvpnsetup.jpg[/IMG]

---

### Post by zhangr on 2010-05-25
Check the route table on Squid server, if it knows how to reach 10.0.3.0/24, then every device in 192.168.1.0/24 do NOT have to know how to reach 10.0.3.0/24, just make 192.168.1.6 to be their default gw.

---

### Post by Nessaja on 2010-05-26
> **zhangr said:**
> Check the route table on Squid server, if it knows how to reach 10.0.3.0/24, then every device in 192.168.1.0/24 do NOT have to know how to reach 10.0.3.0/24, just make 192.168.1.6 to be their default gw.

Ok, I'll try that, thank you

---

### Post by zhangr on 2010-05-31
> **Nessaja said:**
> Ok, I'll try that, thank you

You've to install shorewall and setup Masq/NAT rules, also. Sorry for forgot to remind you this point.

---


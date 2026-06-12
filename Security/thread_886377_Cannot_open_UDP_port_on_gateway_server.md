---
title: "Cannot open UDP port on gateway server"
date: 2008-08-11
forum: Security
---

### Post by nehsa on 2008-08-11
Hello,

This is probably a very silly/simple question but I haven't been able to find the answer.

I simply need to adjust my iptable rules to accept (and maybe output?) UDP 1194 for OpenVPN.  

I have tried adding the following to my iptable rules:
/sbin/iptables -A INPUT -p udp --destination-port 6967 -i br0 -j ACCEPT

Prior to:
/sbin/iptables -P INPUT DROP

/sbin/iptables -A OUTPUT -p udp --destination-port 6967 -j ACCEPT
<Doesn't appear to be any policy to DROP>

From what I've read online, this should do it but when I have a site scan my site these ports changed from "Stealthed" to "Closed" and my clients cannot connect via OpenVPN.

I should note that this server is acting as a gateway server and I am adding these lines to the already existing rules that allow machines behind the gateway to access the internet.

Unfortunantely, as I took the "learn as I go" approach I merely followed a web page and did not implement the gateway rules myself and do not understand was some of them are accomplishing.

Also, due to my OpenVPN setup, the network card I wish to open these ports on is bridged.

Here is my complete gateway script:

~~~~~~~~~~~~START~~~~~~~~~~~~
/sbin/iptables -F
/sbin/iptables -t nat -F
/sbin/iptables -t mangle -F #ignore if you get an error here
/sbin/iptables -X #deletes every non-builtin chain in the table

/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A INPUT -m state --state NEW -i ! eth0 -j ACCEPT
**/sbin/iptables -A INPUT -p udp --destination-port 1194 -i br0 -j ACCEPT**
# only if both of the above rules succeed, use
/sbin/iptables -P INPUT DROP

**/sbin/iptables -A OUTPUT -p udp --destination-port 1194 -j ACCEPT**
/sbin/iptables -A FORWARD -i eth0 -o br0 -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -i br0 -o eth0 -j ACCEPT

/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

/sbin/iptables -A FORWARD -i eth0 -o eth0 -j REJECT
~~~~~~~~~~~~END~~~~~~~~~~~~

and here is my current routing table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0    192.168.1.150  255.255.255.255 UGH   0      0        0 br0
192.168.1.0    0.0.0.0         255.255.255.0   U     0      0        0 br0
INTERNET-IP    0.0.0.0         255.255.254.0   U     0      0        0 eth0
0.0.0.0         INTERNET-GW    0.0.0.0         UG    100    0        0 eth0

I am new to Linux and do not even know where (which logs) to look at to determine where the problem is.  I did try dmesg | tail and tail /var/log/ovenvpn.log and didn't see any problems.

Also, iptables -L shows udp port 1194 as ACCEPT on both INPUT and OUTPUT.

Thanks in advance for any help!

-Nehsa

---


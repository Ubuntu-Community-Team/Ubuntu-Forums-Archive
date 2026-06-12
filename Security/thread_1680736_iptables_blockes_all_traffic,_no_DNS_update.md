---
title: "iptables blockes all traffic, no DNS update"
date: 2011-02-03
forum: Security
---

### Post by dreamkhan on 2011-02-03
Friends, i am new with Ubuntu.
 
Try to block all traffic, using IPTABLES
 
I am using ubuntu server 10.10.
 
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
sudo iptables -A INPUT -p UDP --sport 53 -j ACCEPT
sudo iptables -A OUTPUT -p UDP --dport 53 -j ACCEPT
sudo iptables -A INPUT -p TCP --sport 53 -j ACCEPT
sudo iptables -A OUTPUT -p TCP --dport 53 -j ACCEPT
sudo iptables -A INPUT -p tcp -s XXder.XXXXzee.com -j ACCEPT
sudo iptables -A INPUT -p tcp -s GeXXX.NaXXXX.org -j DROP
 
sudo iptables -A INPUT -j DROP
 
First problem, if i reboot the computer i lose my iptables settings.
 
Second problem, when DNS-adress (XXder.XXXXzee.com ) changed.
 
No update of IP-adress.
 
Thanks for your reply and advice.

---

### Post by sodsada on 2011-02-03
Dear all 

i just setup my ubuntu to be my router as i have 3 network interface and i want to create iptables firewall to link between eth1 can go to eth0 (go to internet)and also eth1 can go to eth2 (go to zone DMZ) as i am very new with iptables and i do search from internet then i do copy one script for modify and it is working when the client access to an Internet but when the client access to zone DMZ it is not working.   

eth0 is WAN
eth1 is LAN
eth2 is DMZ

this is my script that i copy and modify.

#!/bin/sh
# 
# this script requires iptables package to be
# installed on your machine


# Where to find iptables binary
IPT="/sbin/iptables"
# The network interface you will use
# WAN is the one connected to the internet
# LAN the one connected to your local network
WAN="eth0"
LAN="eth1"
# First we need to clear up any existing firewall rules
# and chain which might have been created
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X

# Default policies: Drop any incoming packets
# accept the rest.
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT

# To be able to forward traffic from your LAN
# to the Internet, we need to tell the kernel
# to allow ip forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Masquerading will make machines from the LAN
# look like if they were the router
$IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE


$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 2222 -j DNAT --to-destination 192.168.29.95:22
$IPT -A FORWARD -i $WAN -p tcp  --dport 22 -m state --state NEW -j ACCEPT

# Do not allow other new or invalid connections to reach your internal network
$IPT -A FORWARD -i $WAN -m state --state NEW,INVALID -j DROP

# Accept any connections from the local machine
$IPT -A INPUT -i lo -j ACCEPT
# plus from your local network
$IPT -A INPUT -i $LAN -j ACCEPT

# log those packets and inform the sender that the packet was rejected
$IPT -N Rejectwall
$IPT -A Rejectwall -m limit --limit 10/minute -j LOG --log-prefix "Rejectwall: "
$IPT -A Rejectwall -j REJECT
# use the following instead if you want to simulate that the host is not reachable
# for fun though
#$IPT -A Rejectwall -j REJECT  --reject-with icmp-host-unreachable

$IPT -A INPUT -p icmp -j ACCEPT

# Accept ssh connections from the Internet
$IPT -A INPUT -i $WAN -p tcp --dport 22 -j ACCEPT

# Accept related and established connections
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop netbios from the outside, no log, just drop
$IPT -A INPUT -p udp --sport 137 --dport 137 -j DROP

# Finally, anything which was not allowed yet
# is going to go through our Rejectwall rule
$IPT -A INPUT -j Rejectwall


how can we define eth1<-->eth2 can anyone help me on this
it would appreciate thanks a lot for your helping

---

### Post by YesWeCan on 2011-02-03
> **dreamkhan said:**
> 
 First problem, if i reboot the computer i lose my iptables settings.
 
Solutions here: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
If you are using Network Manager (which is the installation default) you need to see the section titled "Configuration on Startup for NetworkManager"

---


---
title: "firewall iptables vpn passthrough pptp help please"
date: 2009-11-29
forum: Security
---

### Post by ssc351 on 2009-11-29
Hey guys,

I am set-up to use a vpn service like strongvpn.com/bananavpn.com etc.  I can get on the internet with no problems with the iptables down and connected to the vpn.  I can also connect to the internet without the vpn and the firewall up.

So I am having problems getting to the internet through the vpn while the iptables are up.  I have tried a couple of different things and I can't get any of them to work...also note, the vpn uses up to 6 different server addresses, i think this may be another problem as I don't think I can just use **.**.**.64/6 for the -destinationserver because when I use this script the iptables keep bringing up an error.  Lastly, my wireless card is on eth1 and the vpn gets connected through ppp0.  Not sure what interface I need to use or if something has to be set-up to read both interfaces.  Thanks for the help!

Try#1

#Allow VPN
vpnserver="**.**.**.64/6"
iptables -N pptp
iptables -A pptp -p tcp --dport 1723 --dst $vpnserver -j ACCEPT
iptables -A pptp -p 47 --dst $vpnserver -j ACCEPT
iptables -I FORWARD -j pptp
iptables -t nat -N pptp
iptables -t nat -A pptp -i ppp0 -p tcp --dport 1723 -j DNAT --to $vpnserver:1723
iptables -t nat -A pptp -i ppp0 -p 47 -j DNAT --to $vpnserver
iptables -t nat -A PREROUTING -j pptp

Try#2

#Allow VPN
iptables -I INPUT -i ppp0 -p 47 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -o ppp0 -p 47 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -I INPUT -i ppp0 -p tcp --sport 1723 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -o ppp0 -p tcp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT


Try#3

#Allow VPN
iptables -I INPUT -i eth1 -p 47 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -o eth1 -p 47 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -I INPUT -i eth1 -p tcp --sport 1723 -m state --state ESTABLISHED -j ACCEPT
iptables -I OUTPUT -o eth1 -p tcp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT

Try #4

#Allow VPN
iptables -A INPUT -p gre -j ACCEPT
iptables -A OUTPUT -p gre -j ACCEPT
iptables -A INPUT -p tcp --sport 1723 -s **.**.**.64/28 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1723 -d **.**.**.64/28 -j ACCEPT


Here is my iptables script:

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

---

### Post by ssc351 on 2009-12-02
bump...any experts willing to chime in?

---

### Post by ssc351 on 2009-12-13
no one knows how to do this?

---

### Post by movieman on 2009-12-13
> vpnserver="**.**.**.64/6"

Isn't that a completely bogus IP address? If you mean that the first three bytes are fixed and the last is variable, surely that would be something like 1.2.3.0/24?

---

### Post by ssc351 on 2009-12-14
i thought that would mean it works for the following ip's:

vpnserver="**.**.**.64"
vpnserver="**.**.**.65"
vpnserver="**.**.**.66"
vpnserver="**.**.**.67"
vpnserver="**.**.**.68"
vpnserver="**.**.**.69"

or do i have that wrong?  This may be an added issue, but i tried just doing a single ip address on the vpnserver and that didn't work either.

---

### Post by ssc351 on 2009-12-20
uhhh anyone?

---


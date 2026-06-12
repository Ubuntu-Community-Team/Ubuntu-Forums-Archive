---
title: "Please look at my firewall rules"
date: 2007-05-04
forum: Server Platforms
---

### Post by nomb on 2007-05-04
Guys,

Right now my firewall is completely off.  100% off and I think people are still having trouble connecting.  Can you please try to connect again ([www.nombyte.com](www.nombyte.com)) while the are off so we can figure this out once and for all?  I know my domain and router are setup correctly because when I had fedora installed I didn't have any problems.  Now that we know it isn't a firewall issue, what can I do to fix this?


Just incase, here is my firewall script.

```

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
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
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

# Allow http
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
# iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
# iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
# iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 113 -j DROP

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

And actually here is a really good question.

When my firewall is on i can ftp in.
When it is stopped I can't

How does this make sense?

---


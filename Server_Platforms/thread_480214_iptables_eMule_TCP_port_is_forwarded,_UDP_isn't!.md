---
title: "iptables: eMule TCP port is forwarded, UDP isn't!"
date: 2007-06-21
forum: Server Platforms
---

### Post by gianluigi.zanettini on 2007-06-21
Hi all, I've a *routerix* box (fw+gateway) with 3 NICs. Here is my iptables config

```
#!/bin/sh

# Notifico l'avvio dello script
echo "\nGZZ: Script di routing via iptables in caricamento.."

# 
# this script requires iptables package to be
# installed on your machine

# Where to find iptables binary
IPT="/sbin/iptables"

# The network interface you will use
# WAN is the one connected to the internet
# LAN the one connected to your local network
WAN="eth0"
LAN1="eth1"
LAN2="eth2"

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

# If you want to allow traffic to specific port to be
# forwarded to a machine from your LAN
# here we forward traffic to an HTTP server to machine 192.168.0.2
#$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 80 -j DNAT --to 192.168.0.2:80
#$IPT -A FORWARD -i $WAN -p tcp  --dport 80 -m state --state NEW -j ACCEPT
# For a whole range of port, use:
#$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 1200:1300 -j DNAT --to 192.168.0.2
#$IPT -A FORWARD -i $WAN -p tcp  --dport 1200:1300 -m state --state NEW -j ACCEPT

[B]$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 4662 -j DNAT --to 192.168.1.178
$IPT -A FORWARD -i $WAN -p tcp --dport 4662 -m state --state NEW -j ACCEPT

$IPT -t nat -A PREROUTING -i $WAN -p udp --dport 4672 -j DNAT --to 192.168.1.178
$IPT -A FORWARD -i $WAN -p udp --dport 4672 -m state --state NEW -j ACCEPT[/B]

# Do not allow new or invalid connections to reach your internal network
$IPT -A FORWARD -i $WAN -m state --state NEW,INVALID -j DROP

# Accept any connections from the local machine
$IPT -A INPUT -i lo -j ACCEPT
# plus from your local network
$IPT -A INPUT -i $LAN1 -j ACCEPT
$IPT -A INPUT -i $LAN2 -j ACCEPT

# Here we define a new chain which is going to handle
# packets we don't want to respond to
# limit the amount of logs to 10/min
$IPT -N Firewall
$IPT -A Firewall -m limit --limit 10/minute -j LOG --log-prefix "Firewall: "
$IPT -A Firewall -j DROP

# log those packets and inform the sender that the packet was rejected
$IPT -N Rejectwall
$IPT -A Rejectwall -m limit --limit 10/minute -j LOG --log-prefix "Rejectwall: "
$IPT -A Rejectwall -j REJECT
# use the following instead if you want to simulate that the host is not reachable
# for fun though
#$IPT -A Rejectwall -j REJECT  --reject-with icmp-host-unreachable

# here we create a chain to deal with unlegitimate packets
# and limit the number of alerts to 10/min
# packets will be drop without informing the sender
$IPT -N Badflags
$IPT -A Badflags -m limit --limit 10/minute -j LOG --log-prefix "Badflags: "
$IPT -A Badflags -j DROP

# A list of well known combination of Bad TCP flags
# we redirect those to the Badflags chain
# which is going to handle them (log and drop)
$IPT -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,URG URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j Badflags

# Accept certain icmp message, drop the others
# and log them through the Firewall chain
# 0 => echo reply
$IPT -A INPUT -p icmp --icmp-type 0 -j ACCEPT
# 3 => Destination Unreachable
$IPT -A INPUT -p icmp --icmp-type 3 -j ACCEPT
# 11 => Time Exceeded
$IPT -A INPUT -p icmp --icmp-type 11 -j ACCEPT
# 8 => Echo
# avoid ping flood
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
$IPT -A INPUT -p icmp -j Firewall

# Accept ssh connections from the Internet
#$IPT -A INPUT -i $WAN -p tcp --dport 22 -j ACCEPT
# or only accept from a certain ip
#$IPT -A INPUT -i $WAN -s 125.124.123.122 -p tcp --dport 22 -j ACCEPT
# Accetto SSH solo dalle interfacce LAN
$IPT -A INPUT -i $LAN1 -p tcp --dport 22 -j ACCEPT
$IPT -A INPUT -i $LAN2 -p tcp --dport 22 -j ACCEPT

[B]$IPT -A INPUT -i $WAN -p tcp --dport 4662 -j ACCEPT
$IPT -A INPUT -i $WAN -p udp --dport 4672 -j ACCEPT[/B]



# Accept related and established connections
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop netbios from the outside, no log, just drop
$IPT -A INPUT -p udp --sport 137 --dport 137 -j DROP

# Finally, anything which was not allowed yet
# is going to go through our Rejectwall rule
$IPT -A INPUT -j Rejectwall

echo "\nGZZ: iptables pronto all'azione!"
```

eMule running on 192.168.1.178  is reporting that TCP port 4662 is OK but UDP 4672 isn't!! what's wrong with my script?

Many thanks!

---

### Post by dexter2 on 2007-06-21
i use shorewall to manage iptables rules. It is easy to learn and once you understend it, it is very easy to manage rools.

---

### Post by turinglabs on 2007-06-21
Hello again-

You are missing the 'etablished,related' accept rule for the forward chain, although I'm not sure that's your problem. The ruleset is confusing because you are using a 'default accept' policy, when you should be using a 'default deny' policy.  Block everything, then explicitly allow what you want to let through. It's more secure, and generally a lot simpler.

I agree that some of the firewall packages like shorewall make iptables easier to manage, since they get rid of the steep learning curve. There is even a decent GUI you can try, see fwbuilder.org. I haven't checked that site in a while, but just today I saw that they now have an iptables importer, that will import your existing ruleset as a starting point.

---


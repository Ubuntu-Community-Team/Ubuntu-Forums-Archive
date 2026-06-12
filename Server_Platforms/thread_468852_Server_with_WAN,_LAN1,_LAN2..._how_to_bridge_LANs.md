---
title: "Server with WAN, LAN1, LAN2... how to bridge LANs?"
date: 2007-06-09
forum: Server Platforms
---

### Post by gianluigi.zanettini on 2007-06-09
Hi guys,
thanks to [a wonderfull guide]("http://www.debuntu.org/iptables-how-to-share-your-internet-connection"), I was able to put my 3-NICed-server on-line.

Everythings works! WAN is the Internet-connected interface: my server forwards LAN1 (192.168.1.0) and LAN2 (192.168.3.0) through WAN and both networks can reach Internet.

Here it is the IPTABLE script I use:

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

#GZZ: Forewarding eMule..
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 4662 -j DNAT --to 192.168.1.178
$IPT -A FORWARD -i $WAN -p tcp --dport 4662 -m state --state NEW -j ACCEPT
$IPT -t nat -A PREROUTING -i $WAN -p udp --dport 4672 -j DNAT --to 192.168.1.178
$IPT -A FORWARD -i $WAN -p udp --dport 4672 -m state --state NEW -j ACCEPT

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

#GZZ: Accetto SSH solo dalle interfacce LAN
$IPT -A INPUT -i $LAN1 -p tcp --dport 22 -j ACCEPT
$IPT -A INPUT -i $LAN2 -p tcp --dport 22 -j ACCEPT

#GZZ: Apro le porte di eMule
$IPT -A INPUT -i $WAN -p tcp --dport 4662 -j ACCEPT
$IPT -A INPUT -i $WAN -p udp --dport 4672 -j ACCEPT

# Accept related and established connections
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop netbios from the outside, no log, just drop
$IPT -A INPUT -p udp --sport 137 --dport 137 -j DROP

# Finally, anything which was not allowed yet
# is going to go through our Rejectwall rule
$IPT -A INPUT -j Rejectwall

echo "\nGZZ: iptables pronto all'azione!"
```

Now I also need to bridge LAN1 and LAN2 together: eg 192.168.**1**.12 can reach 192.168.**3**.15

How can I do that, preserving the Internet-sharing for both networks?

Many thanks!

---

### Post by turinglabs on 2007-06-09
> **gianluigi.zanettini said:**
> 
Now I also need to bridge LAN1 and LAN2 together: eg 192.168.**1**.12 can reach 192.168.**3**.15

How can I do that, preserving the Internet-sharing for both networks?


Packets destined from one LAN to the other will traverse the firewall's FORWARD chain, which you already have set with a default ACCEPT policy, meaning without a specific drop or reject, all packets across this chain will be allowed. From the script, the only FORWARD drop rules I see are those for packets that come in over the WAN interface (eth0). Now, because each LAN is directly connected to your firewall through an interface on the firewall itself (eth1, eth2), you should already be able to route packets from one LAN to the other with IP forwarding enabled. 

Finally, because your NAT rules are specific to the WAN interface, you don't have to worry about NAT interfering with LAN-to-LAN communication.

So no additional rules are needed.

---

### Post by gianluigi.zanettini on 2007-06-10
Many, many thanks for your kind answer!

I've no access to that box right now: I'll give it a try during the weel, I'll let you know if it works as expected!

Thanks again!

---

### Post by gianluigi.zanettini on 2007-06-11
Ok, I'm back with updates.

Unfortunately, machines on the two different networks are unreachable.

"Cross-network" traffic isn't possibile unless you have a router between them, wich has to be confiured to do so: maybe I need to explicity configure IPTABLES to forward traffic?

I'm sorry if I'm asking a stupid question: I'm a pretty skilled Win admin, but I' totally newbie with Linux!

---

### Post by turinglabs on 2007-06-11
I may be misunderstanding your network layout, but in the scenario you describe, you do have a router - the firewall itself, and you do have IP fowarding enabled, at least in the script. 

Packets from LAN1 destined for LAN2 will hit the firewall on eth1, and be routed out the eth2 interface, across the FORWARD chain (or vice-versa), *if* IP forwarding is enabled and *if* the FORWARD chain allows it. If the LAN's were not directly connected to the firewall through eth1 or eth2, then yes, you would need either an internal router or static routes on the firewall to get this to work. Here, the necessary routes get added at boot-time when the interfaces come up (do a netstat -rn and check).  

A couple of suggestions:

You might start a ping from one LAN to the other and tail your /var/log/messages file, or start a tcpdump on eth1 or eth2 and watch for packets and replies. Something like 'tcpdump -n -i eth2 src host 192.168.1.12' or 'tcpdump -n -i eth2 host 192.168.1.12' (the latter matches src or dst).

Flush your iptables rules and chains (like in the head of your script), and manually re-enable forwarding with 'sysctl -w net.ipv4.ip_forward=1'. Then test connectivity from one LAN to the other. You want to rule out a firewall issue, and this is the easiest way to just make the firewall a bare router. If it works, then re-enable the firewall rules and try again.

If you're still stuck, post the following, and we can dig further:

ifconfig -a
netstat -rn
iptables -L -nvx
iptables -t nat -L -nvx
sysctl net.ipv4.ip_forward

---

### Post by gianluigi.zanettini on 2007-06-12
turinglabs, many thanks for your time. The networks are reachable indeed : I had problem due to a non-iptables related issue.

Many thanks again for your help! if you come to Italy, please don't forget to stop in Ferrara for a glass of wine!

p.s. if you have time, could you please let me know how should I modify the script if one day I wish to isulate traffic from $LAN1 and $LAN2 (but have them both reach the internet via $WAN)?

---

### Post by turinglabs on 2007-06-12
> **gianluigi.zanettini said:**
> turinglabs, many thanks for your time. The networks are reachable indeed : I had problem due to a non-iptables related issue.

Many thanks again for your help! if you come to Italy, please don't forget to stop in Ferrara for a glass of wine!

p.s. if you have time, could you please let me know how should I modify the script if one day I wish to isulate traffic from $LAN1 and $LAN2 (but have them both reach the internet via $WAN)?

Will do, thanks! With your setup (default allow), you would just add explicit rules that block traffic from one LAN to the other, and vice-versa (replace the /24 with your netmask if needed):

$IPT -A FORWARD -s 192.168.1.0/24 -d 192.168.3.0/24 -j DROP
$IPT -A FORWARD -s 192.168.3.0/24 -d 192.168.1.0/24 -j DROP

This will still allow traffic from the LANs outbound via the WAN interface.

---

### Post by gianluigi.zanettini on 2007-06-12
You definitely rock, man!! Many thanks again!!

---


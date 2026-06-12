---
title: "are there too many return targets in this iptables script?"
date: 2009-03-04
forum: Security
---

### Post by CoffeeBreath on 2009-03-04
After the packets traversing this firewall traverse the bad_packets chain and traverse the bad_tcp_packets chain, are the two RETURN targets in those chains really necessary? Won't the packets continue to fall through the other chains and match or fail to match the conditions of the other chains?

To me it appears that a packet will go through bad_packets , jump to bad_tcp_packets and then return to the bad_packets chain which will return the packet to the INPUT chain.

Am I correct? Is there some way to improve this script?

```
# Set Policies

$IPT -P INPUT DROP
$IPT -P OUTPUT DROP
$IPT -P FORWARD DROP

###############################################################################
#
# User-Specified Chains
#
# Create user chains to reduce the number of rules each packet
# must traverse.

echo "Create and populate custom rule chains ..."

# Create a chain to filter INVALID packets

$IPT -N bad_packets

# Create another chain to filter bad tcp packets

$IPT -N bad_tcp_packets

# Create separate chains for icmp, tcp (incoming and outgoing),
# and incoming udp packets.

$IPT -N icmp_packets

# Used for UDP packets inbound from the Internet
$IPT -N udp_inbound

# Used to block outbound UDP services from internal network
# Default to allow all
$IPT -N udp_outbound

# Used to allow inbound services if desired
# Default fail except for established sessions
$IPT -N tcp_inbound

# Used to block outbound services from internal network
# Default to allow all
$IPT -N tcp_outbound

###############################################################################
#
# Populate User Chains
#

# bad_packets chain
#

# Drop INVALID packets immediately
$IPT -A bad_packets -p ALL -m state --state INVALID -j LOG \
    --log-prefix "Invalid packet: "

$IPT -A bad_packets -p ALL -m state --state INVALID -j DROP

# Then check the tcp packets for additional problems
$IPT -A bad_packets -p tcp -j bad_tcp_packets

# All good, so return
$IPT -A bad_packets -p ALL -j RETURN

# bad_tcp_packets chain
#
# All tcp packets will traverse this chain.
# Every new connection attempt should begin with
# a syn packet.  If it doesn't, it is likely a
# port scan.  This drops packets in state
# NEW that are not flagged as syn packets.


$IPT -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -j LOG \
    --log-prefix "New not syn: "
$IPT -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -j DROP

$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL NONE -j LOG \
    --log-prefix "Stealth scan: "
$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL NONE -j DROP

$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL ALL -j LOG \
    --log-prefix "Stealth scan: "
$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL ALL -j DROP

$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL FIN,URG,PSH -j LOG \
    --log-prefix "Stealth scan: "
$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP

$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j LOG \
    --log-prefix "Stealth scan: "
$IPT -A bad_tcp_packets -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP

$IPT -A bad_tcp_packets -p tcp --tcp-flags SYN,RST SYN,RST -j LOG \
    --log-prefix "Stealth scan: "
$IPT -A bad_tcp_packets -p tcp --tcp-flags SYN,RST SYN,RST -j DROP

$IPT -A bad_tcp_packets -p tcp --tcp-flags SYN,FIN SYN,FIN -j LOG \
    --log-prefix "Stealth scan: "
$IPT -A bad_tcp_packets -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP

# All good, so return
$IPT -A bad_tcp_packets -p tcp -j RETURN

$IPT -A icmp_packets --fragment -p ICMP -j LOG \
    --log-prefix "ICMP Fragment: "
$IPT -A icmp_packets --fragment -p ICMP -j DROP

$IPT -A icmp_packets -p ICMP -s 0/0 --icmp-type 8 -j DROP

# Time Exceeded
$IPT -A icmp_packets -p ICMP -s 0/0 --icmp-type 11 -j ACCEPT

# Not matched, so return so it will be logged
$IPT -A icmp_packets -p ICMP -j RETURN

$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 137 -j DROP
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 138 -j DROP

$IPT -A udp_inbound -p UDP -s 0/0 --source-port 67 --destination-port 68 \
     -j ACCEPT


# Not matched, so return for logging
$IPT -A udp_inbound -p UDP -j RETURN

# No match, so ACCEPT
$IPT -A udp_outbound -p UDP -s 0/0 -j ACCEPT

# Not matched, so return so it will be logged
$IPT -A tcp_inbound -p TCP -j RETURN


# No match, so ACCEPT
$IPT -A tcp_outbound -p TCP -s 0/0 -j ACCEPT

###############################################################################
#
# INPUT Chain
#

echo "Process INPUT chain ..."

# Allow all on localhost interface
$IPT -A INPUT -p ALL -i $LO_IFACE -j ACCEPT

# Drop bad packets
$IPT -A INPUT -p ALL -j bad_packets


$IPT -A INPUT -p ALL -d 224.0.0.1 -j DROP
# The rule to accept the packets.
# $IPT -A INPUT -p ALL -d 224.0.0.1 -j ACCEPT


# Inbound Internet Packet Rules

# Accept Established Connections
$IPT -A INPUT -p ALL -i $INET_IFACE -m state --state ESTABLISHED,RELATED \
     -j ACCEPT

# Route the rest to the appropriate user chain
$IPT -A INPUT -p TCP -i $INET_IFACE -j tcp_inbound
$IPT -A INPUT -p UDP -i $INET_IFACE -j udp_inbound
$IPT -A INPUT -p ICMP -i $INET_IFACE -j icmp_packets

# Drop without logging broadcasts that get this far.
# Cuts down on log clutter.
# Comment this line if testing new rules that impact
# broadcast protocols.
$IPT -A INPUT -m pkttype --pkt-type broadcast -j DROP

# Log packets that still don't match
$IPT -A INPUT -m limit --limit 3/minute --limit-burst 3 -j LOG \
    --log-prefix "INPUT packet died: "

###############################################################################
#
# FORWARD Chain
#

echo "Process FORWARD chain ..."

# Used if forwarding for a private network


###############################################################################
#
# OUTPUT Chain
#

echo "Process OUTPUT chain ..."

# Generally trust the firewall on output

# However, invalid icmp packets need to be dropped
# to prevent a possible exploit.
$IPT -A OUTPUT -m state -p icmp --state INVALID -j DROP

# Localhost
$IPT -A OUTPUT -p ALL -s $LO_IP -j ACCEPT
$IPT -A OUTPUT -p ALL -o $LO_IFACE -j ACCEPT

# To internet
$IPT -A OUTPUT -p ALL -o $INET_IFACE -j ACCEPT

# Log packets that still don't match
$IPT -A OUTPUT -m limit --limit 3/minute --limit-burst 3 -j LOG \
    --log-prefix "OUTPUT packet died: "
```

---

### Post by markharding557 on 2009-03-04
why not use a gui like guarddog or firestarter i found either of these configures the firewall fine

---

### Post by bodhi.zazen on 2009-03-04
It is difficult to read your script as it is probably more complex then it needs to be.

You can simplify all this by simply eliminating the user tables.

You are logging a lot of traffic, are you sure you wish to fill your logs with this information ? Just checking because if you do not intend to watch you logs you can probably further simplify your script.

Personally, the only user maintained table I use is a blacklist. This makes it easier to either add or delete an ip address as I wish.

Early in your script you should flush all tables and rules, including you user maintained tables otherwise your -A just keeps making the table longer and longer.

Once you get iptables set up, you really do not need a script at all.

```
sudo iptables-save > /etc/iptables.rules
```

And

```
sudo iptables-restore < /etc/iptables-rules
```

It also appears you posted a fragment of your script as I do not see your variables defined. while this makes it easy to write a script, it makes it hard to follow as well.

Probably easier to review your rules by posting or running :

```
sudo iptables -L -v
```

---

### Post by lensman3 on 2009-03-04
>>are there too many return targets in this iptables script?

RETURN's are not needed.  BUT, I like them because if you do a "iptables -L -nv" the returns show how many packets traversed that chain and you can see if it is working.

>>After the packets traversing this firewall traverse the bad_packets chain and traverse the bad_tcp_packets chain, are the two RETURN targets in those chains really necessary? 

No. Remember that if a packet  is found to be bad that it is dropped and iptables waits for the next packet.

>> Won't the packets continue to fall through the other chains and match or fail to match the conditions of the other chains?

Yes.  Everything keeps processing until it is dropped.   Packets that are not dropped are processed using the default polices.

>>To me it appears that a packet will go through bad_packets , jump to >>bad_tcp_packets and then return to the bad_packets chain which will >>return the packet to the INPUT chain.

Your default policy is DROP.  So eventually a "good" packet will have to be accepted.  Most packets get processed by the "RELATED,ESTABLISHED" line.  "NEW" packets going out get processed by the "NEW" statement.  

>>Am I correct? Is there some way to improve this script?
I would block more incoming/outgoing ports. Currently you do 137,139.  I drop all below 1024 (those are privileged ports).  Change the 224.0.0.1 to "224.0.0.0/3", that way everything on the broadcast network is rejected.  I drop ports ED_PORTS_UDP="69,111,135,445,515,593,444,2049,7100,31337,27444,31335,10498".  A lot of those ports are used by virus, printers and so on.  I also block ports 6000:6063 which are used by X-windows.  Block everything going out that you don't want your neighbors looking at.  (It is considered poor form to print something on your neighbors printer)!

I also block incoming and sometimes the outgoing ports to most of Asia, Eastern Europe, and South America IP addresses.  I also drop ip address ranges 214.0.0.0/8 and 215.0.0.0/8, the US Military.  You should also block 10.0.0.0/8, 169.254.0.0/16, 172.16.0.0/12, 127.0.0.0 and all above 240.0.0.0/5.  These addresses are not routable by the Internet and anybody using these are probably up to no good.  I also block 0.0.0.0, but you have to make arrangements for this one because DHCP address can come over this one.  Careful how you block 127.0.0.0.  Don't block it on the "lo" interface, just on a real eth0.

Remember that you can use the following for an iptables command:
"iptables -A "???" -p ! icmp <whatever>" 
In this case iptables with process the TCP/UDP protocols and skip processing the ICMP protocol.

One thing you can do is in that long chain where you is put the LOG and DROP parts of the chain into their own chains. Then in one test chain, test each for each of the conditions and if they are met, then jump to the LOG and DROP.  That way a good packet is only tested once instead of twice in the chain.  Bad packets are tested 3 times, but bad packets are not the rule.

I hope this helps.  My firewall iptables chain has 281 separate IPTABLES command lines.  But I block a lot of sites and when I start doing torrents I open up selected ports to the "bad" IP addresses. I have yet to see my firewall PC use more than 5% of it CPU cycles processing packets.

---

### Post by CoffeeBreath on 2009-03-05
> **bodhi.zazen said:**
> It is difficult to read your script as it is probably more complex then it needs to be.

You can simplify all this by simply eliminating the user tables.

You are logging a lot of traffic, are you sure you wish to fill your logs with this information ? Just checking because if you do not intend to watch you logs you can probably further simplify your script.

Personally, the only user maintained table I use is a blacklist. This makes it easier to either add or delete an ip address as I wish.

Early in your script you should flush all tables and rules, including you user maintained tables otherwise your -A just keeps making the table longer and longer.

Once you get iptables set up, you really do not need a script at all.

```
sudo iptables-save > /etc/iptables.rules
```

And

```
sudo iptables-restore < /etc/iptables-rules
```

It also appears you posted a fragment of your script as I do not see your variables defined. while this makes it easy to write a script, it makes it hard to follow as well.

Probably easier to review your rules by posting or running :

```
sudo iptables -L -v
```
 

Bohdi,
  Thanks for the tips. I didn't post all of the script for brevity. I also be watching the logs for the ask learning how to sift through info with tools like sed, awk , and using regular expressions. I'll also be using a box as router after this introductory project.

---

### Post by CoffeeBreath on 2009-03-06
> **lensman3 said:**
> >>are there too many return targets in this iptables script?

RETURN's are not needed.  BUT, I like them because if you do a "iptables -L -nv" the returns show how many packets traversed that chain and you can see if it is working.

>>After the packets traversing this firewall traverse the bad_packets chain and traverse the bad_tcp_packets chain, are the two RETURN targets in those chains really necessary? 

No. Remember that if a packet  is found to be bad that it is dropped and iptables waits for the next packet.

>> Won't the packets continue to fall through the other chains and match or fail to match the conditions of the other chains?

Yes.  Everything keeps processing until it is dropped.   Packets that are not dropped are processed using the default polices.

>>To me it appears that a packet will go through bad_packets , jump to >>bad_tcp_packets and then return to the bad_packets chain which will >>return the packet to the INPUT chain.

Your default policy is DROP.  So eventually a "good" packet will have to be accepted.  Most packets get processed by the "RELATED,ESTABLISHED" line.  "NEW" packets going out get processed by the "NEW" statement.  

>>Am I correct? Is there some way to improve this script?
I would block more incoming/outgoing ports. Currently you do 137,139.  I drop all below 1024 (those are privileged ports).  Change the 224.0.0.1 to "224.0.0.0/3", that way everything on the broadcast network is rejected.  I drop ports ED_PORTS_UDP="69,111,135,445,515,593,444,2049,7100,31337,27444,31335,10498".  A lot of those ports are used by virus, printers and so on.  I also block ports 6000:6063 which are used by X-windows.  Block everything going out that you don't want your neighbors looking at.  (It is considered poor form to print something on your neighbors printer)!

I also block incoming and sometimes the outgoing ports to most of Asia, Eastern Europe, and South America IP addresses.  I also drop ip address ranges 214.0.0.0/8 and 215.0.0.0/8, the US Military.  You should also block 10.0.0.0/8, 169.254.0.0/16, 172.16.0.0/12, 127.0.0.0 and all above 240.0.0.0/5.  These addresses are not routable by the Internet and anybody using these are probably up to no good.  I also block 0.0.0.0, but you have to make arrangements for this one because DHCP address can come over this one.  Careful how you block 127.0.0.0.  Don't block it on the "lo" interface, just on a real eth0.

Remember that you can use the following for an iptables command:
"iptables -A "???" -p ! icmp <whatever>" 
In this case iptables with process the TCP/UDP protocols and skip processing the ICMP protocol.

One thing you can do is in that long chain where you is put the LOG and DROP parts of the chain into their own chains. Then in one test chain, test each for each of the conditions and if they are met, then jump to the LOG and DROP.  That way a good packet is only tested once instead of twice in the chain.  Bad packets are tested 3 times, but bad packets are not the rule.

I hope this helps.  My firewall iptables chain has 281 separate IPTABLES command lines.  But I block a lot of sites and when I start doing torrents I open up selected ports to the "bad" IP addresses. I have yet to see my firewall PC use more than 5% of it CPU cycles processing packets.

Thanks for your tips lensman. I'll be testing scripts with your suggestions this weekend.

---


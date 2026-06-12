---
title: "iptables-forwarding"
date: 2007-08-16
forum: Server Platforms
---

### Post by davidhayes on 2007-08-16
Hi, 
This is driving me slowly insane. I have a linux box set up as a firewall router and I'm having trouble forwarding a particular port to one of my local machines.
All my internet research suggests that this should do the trick
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 23483 -j DNAT --to 192.168.1.7:23483
$IPT -A FORWARD -s 192.168.1.7 -p tcp --dport 23483 -j ACCEPT
However I am still seeing these packets logged as dropped. Any ideas??

Full script for context
------------
#!/bin/sh
#

# The location of the IPtables binary file on your system.
IPT="/sbin/iptables"

INT="eth1"
LOC="eth0"

# The following rules will clear out any existing firewall rules,
# and any chains that might have been created.
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X

# These will setup our policies.
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT

# The following line below enables IP forwarding and thus
# by extension, NAT. Turn this on if you're going to be
# doing NAT or IP Masquerading.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Source NAT everything heading out the $INT (external)
$IPT -t nat -A POSTROUTING -o $INT -j MASQUERADE

# This rule protects your fowarding rule.
$IPT -A FORWARD -i $INT -m state --state NEW,INVALID -j DROP

$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 23483 -j DNAT --to 192.168.1.7:23483
$IPT -A FORWARD -s 192.168.1.7 -p tcp --dport 23483 -j ACCEPT

# Now, our firewall chain. We use the limit commands to
# cap the rate at which it alerts to 15 log messages per minute.
$IPT -N firewall
$IPT -A firewall -m limit --limit 15/minute -j LOG --log-prefix Firewall:
$IPT -A firewall -j DROP

# Now, our dropwall chain, for the final catchall filter.
$IPT -N dropwall
$IPT -A dropwall -m limit --limit 15/minute -j LOG --log-prefix Dropwall:
$IPT -A dropwall -j DROP

# Our "hey, them's some bad tcp flags!" chain.
$IPT -N badflags
$IPT -A badflags -m limit --limit 15/minute -j LOG --log-prefix Badflags:
$IPT -A badflags -j DROP

# And our silent logging chain.
$IPT -N silent
$IPT -A silent -j DROP

# This rule will accept connections from local machines. If you have
# a home network, enter in the IP's of the machines on the
# network below.
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A INPUT -i $LOC -d 0/0 -p all -j ACCEPT
#$IPT -A INPUT -s 10.1.1.51 -d 0/0 -p all -j ACCEPT
#$IPT -A INPUT -s 10.1.1.52 -d 0/0 -p all -j ACCEPT

# Drop those nasty packets! These are all TCP flag
# combinations that should never, ever occur in the
# wild. All of these are illegal combinations that
# are used to attack a box in various ways, so we
# just drop them and log them here.
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j badflags

# Drop icmp, but only after letting certain types through.
$IPT -A INPUT -p icmp --icmp-type 0 -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 3 -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 11 -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
$IPT -A INPUT -p icmp -j firewall

# If you would like to open up port 22 (SSH Access) to various IP's
# simply edit the IP's below and uncomment the line. If youw wish to
# enable SSH access from anywhere, uncomment the second line only.
#$IPT -A INPUT -i $INT -s 10.1.1.1 -d 0/0 -p tcp --dport 22 -j ACCEPT
$IPT -A INPUT -i $INT -s 0/0 -d 0/0 -p tcp --dport 22 -j ACCEPT

# If you are running a Web Server, uncomment the next line to open
# up port 80 on your machine.
#$IPT -A INPUT -i $INT -s 0/0 -d 0/0 -p tcp --dport 80 -j ACCEPT

# Lets do some basic state-matching. This allows us
# to accept related and established connections, so
# client-side things like ftp work properly, for example.
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Uncomment to drop port 137 netbios packets silently.
# We don't like that netbios stuff, and it's way too
# spammy with windows machines on the network.
#$IPT -A INPUT -p udp --sport 137 --dport 137 -j silent

# Our final trap. Everything on INPUT goes to the dropwall
# so we don't get silent drops.
$IPT -A INPUT -j dropwall

---

### Post by HermanAB on 2007-08-16
Hmm, change the -A to -I to insert those rules in the beginning, instead of adding them on to the end.  If the packet gets dropped earlier in the chain, it won't get to your new rule at the end...

Cheers,

Herman

---

### Post by davidhayes on 2007-08-17
Still not having any luck, tried moving those rules to the top of the chain and they still aren't matching

---

### Post by davidhayes on 2007-08-17
Hmmm, if I add the following line
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 23483 -j LOG --log-prefix Azureus:

I see matches in the log which suggests my rule is matching. However I still can't connect and the port looks closed.

---

### Post by davidhayes on 2007-08-17
Ah, you were right.... I hadn't enabled UDP which was masking the issue
The following snippet works!!!
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 23483 -j LOG --log-prefix Azureus:
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 23483 -j DNAT --to 192.168.1.7
$IPT -A FORWARD -i $INT -d 192.168.1.7 -p tcp --dport 23483 -j ACCEPT

$IPT -t nat -A PREROUTING -i $INT -p udp --dport 23483 -j LOG --log-prefix Azureus:
$IPT -t nat -A PREROUTING -i $INT -p udp --dport 23483 -j DNAT --to 192.168.1.7
$IPT -A FORWARD -i $INT -d 192.168.1.7 -p udp --dport 23483 -j ACCEPT

# This rule protects your fowarding rule.
$IPT -A FORWARD -i $INT -m state --state NEW,INVALID -j DROP

---


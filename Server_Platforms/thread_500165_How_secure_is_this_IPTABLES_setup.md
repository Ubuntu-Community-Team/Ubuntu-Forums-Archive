---
title: "How secure is this IPTABLES setup?"
date: 2007-07-13
forum: Server Platforms
---

### Post by jimbo77 on 2007-07-13
here is my iptables configuration script, please tell me how secure this really is

i really want to make my config as secure as possible, so any suggestions/comments are greatly appreciated ;)
```

#!/bin/sh
#
# Created by James Sullivan
# Last updated 13/07/07
#
#


PATH=/usr/sbin:/sbin:/bin:/usr/bin

# temporarily block all traffic.
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Delete/Flush old iptables rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Set default policies
iptables -P OUTPUT ACCEPT
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Prevent external packets from using loopback addr [OPTIONAL]
iptables -A INPUT   -i wlan0 -s 127.0.0.1 -j DROP
iptables -A FORWARD -i wlan0 -s 127.0.0.1 -j DROP
iptables -A INPUT   -i wlan0 -d 127.0.0.1 -j DROP
iptables -A FORWARD -i wlan0 -d 127.0.0.1 -j DROP

# Anything coming from/going to Internet should not
# use private addresses [OPTIONAL]
iptables -A FORWARD -i wlan0 -s 172.16.0.0/12 -j DROP
iptables -A FORWARD -i wlan0 -s 10.0.0.0/8 -j DROP
iptables -A INPUT -i wlan0 -s 172.16.0.0/12 -j DROP
iptables -A INPUT -i wlan0 -s 10.0.0.0/8 -j DROP

# Block outgoing NetBios [OPTIONAL]
iptables -A FORWARD -p tcp --sport 137:139 -o eth0 -j DROP
iptables -A FORWARD -p udp --sport 137:139 -o eth0 -j DROP
iptables -A OUTPUT -p tcp --sport 137:139 -o eth0 -j DROP
iptables -A OUTPUT -p udp --sport 137:139 -o eth0 -j DROP

# Allow local loopback [NEEDED]
iptables -A INPUT -i lo -j ACCEPT

# Allow pings [OPTIONAL]
iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT


############ STATE STUFF ############
# Accept existing connections [NEEDED]
iptables -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow any new conections from internal network
# [ONLY NEEDED IF PORTS ARE NOT EXPLITLY FORWARDED BELOW]
#iptables -A INPUT -m state --state NEW -i eth0 -j ACCEPT
#####################################

# Allow inbound services [OPTIONAL - DNS NEEDED]
iptables -A INPUT -p tcp -i wlan0 --dport 44444 -j ACCEPT #SSH
iptables -A INPUT -p tcp -i wlan0 --dport 23232 -j ACCEPT #Bittorrent
iptables -A INPUT -p udp -i wlan0 --dport 23232 -j ACCEPT #Bittorrent
iptables -A INPUT -p udp -i eth0  --dport 53 -j ACCEPT #DNS cache
iptables -A INPUT -p tcp -i eth0  --dport 53 -j ACCEPT #DNS cache
iptables -A INPUT -p udp -i eth0  --dport 137:139 -j ACCEPT #SAMBA
iptables -A INPUT -p tcp -i eth0  --dport 445 -j ACCEPT #SAMBA


# Allow forwarding of essential services [NEEDED]
iptables -A FORWARD -p tcp --dport 80 -j ACCEPT #WEB
iptables -A FORWARD -p tcp --dport 443 -j ACCEPT #HTTPS

# Don't forward from the outside to the inside [OPTIONAL]
iptables -A FORWARD -i wlan0 -o eth0 -j REJECT


# Masquerade [NEEDED]
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward

```

---

### Post by murraymca on 2007-07-14
Hi, just quickly wondering why you block outgoing 137:139 but allow it incoming - wouldn't that just 'break'? (sorry if I misinterpreted)

Cheers

---

### Post by jimbo77 on 2007-07-16
thanks murraymca you are right.

What i meant to have there was a block on any netbios packets leaving on the wlan0 (internet) interface.

here is the latest version of my script:
```

#!/bin/sh
#
# Created by James Sullivan
# Last updated 16/07/07
#
#


PATH=/usr/sbin:/sbin:/bin:/usr/bin

# temporarily disable routing
echo 0 > /proc/sys/net/ipv4/ip_forward

# temporarily block all traffic
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Delete/Flush old iptables rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Set default policies
iptables -P OUTPUT ACCEPT
iptables -P INPUT DROP
iptables -P FORWARD DROP

# Prevent external packets from using loopback addresses [OPTIONAL]
iptables -A INPUT   -i wlan0 -s 127.0.0.1 -j DROP
iptables -A INPUT   -i wlan0 -d 127.0.0.1 -j DROP
iptables -A FORWARD -i wlan0 -s 127.0.0.1 -j DROP
iptables -A FORWARD -i wlan0 -d 127.0.0.1 -j DROP

# Anything coming from/going to Internet should not
# use private addresses [OPTIONAL]
iptables -A INPUT   -i wlan0 -s 172.16.0.0/12  -j DROP
iptables -A INPUT   -i wlan0 -s 10.0.0.0/8     -j DROP
iptables -A INPUT   -i wlan0 -s 192.168.0.0/24 -j DROP
iptables -A FORWARD -i wlan0 -s 172.16.0.0/12  -j DROP
iptables -A FORWARD -i wlan0 -s 10.0.0.0/8     -j DROP
iptables -A FORWARD -i wlan0 -s 192.168.0.0/24 -j DROP

# Block outgoing NetBios [OPTIONAL]
iptables -A FORWARD -p tcp --sport 137:139 -o wlan0 -j LOG --log-prefix "FORWARD DROP: "
iptables -A FORWARD -p tcp --sport 137:139 -o wlan0 -j DROP
iptables -A FORWARD -p udp --sport 137:139 -o wlan0 -j LOG --log-prefix "FORWARD DROP: "
iptables -A FORWARD -p udp --sport 137:139 -o wlan0 -j DROP
iptables -A OUTPUT  -p tcp --sport 137:139 -o wlan0 -j LOG --log-prefix "OUTPUT DROP: "
iptables -A OUTPUT  -p tcp --sport 137:139 -o wlan0 -j DROP
iptables -A OUTPUT  -p udp --sport 137:139 -o wlan0 -j LOG --log-prefix "OUTPUT DROP: "
iptables -A OUTPUT  -p udp --sport 137:139 -o wlan0 -j DROP

# Allow local loopback [NEEDED]
iptables -A INPUT -i lo -j ACCEPT

# Allow pings [OPTIONAL]
iptables -A INPUT   -p icmp --icmp-type echo-request -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT


############ STATE STUFF ############
# Accept existing connections [NEEDED]
iptables -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow any new conections from internal network
# [ONLY NEEDED IF PORTS ARE NOT EXPLITLY FORWARDED BELOW]
#iptables -A INPUT -m state --state NEW -i eth0 -j ACCEPT
#####################################

# Externally accessable inbound services [OPTIONAL]
iptables -A INPUT -p tcp --dport 44444 -m state --state NEW -j ACCEPT #SSH
iptables -A INPUT -p tcp -i wlan0 --dport 23232 -m state --state NEW -j ACCEPT #Bittorrent
iptables -A INPUT -p udp -i wlan0 --dport 23232 -m state --state NEW -j ACCEPT #Bittorrent

# Internal inbound services [OPTIONAL - DNS NEEDED]
iptables -A INPUT -p udp -i eth0 --dport 53      -m state --state NEW -j ACCEPT #DNS cache
iptables -A INPUT -p tcp -i eth0 --dport 53      -m state --state NEW -j ACCEPT #DNS cache
iptables -A INPUT -p udp -i eth0 --dport 137:139 -m state --state NEW -j ACCEPT #SAMBA
iptables -A INPUT -p tcp -i eth0 --dport 445     -m state --state NEW -j ACCEPT #SAMBA

# Allow forwarding of essential services [NEEDED]
iptables -A FORWARD -p tcp --dport 80 -j ACCEPT #WEB
iptables -A FORWARD -p tcp --dport 443 -j ACCEPT #HTTPS

# Masquerade [NEEDED]
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward


```

---

### Post by murraymca on 2007-07-16
Hi Jimbo,

I'm not an expert but that looks okay to me...just as long as you know what you are forwarding.

In the netbios section it appeared to me as though you had two rules:  one to log, one to drop...I use this chain to combine both, might make your configuration shorter+easier:

iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-level warning --log-prefix "dropped"
iptables -A LOG_DROP -j DROP

So to drop I append -j LOG_DROP but of course, this may not be what you want or generate too much traffic in your logs.

For loopback traffic (I'm a bit tired so sorry if you have already done all this) I reckon you need:  iptables -A OUTPUT -o lo -j ACCEPT (I think you currently just had input?)

In the stateful section, I have one like this for input and output:
iptables -A INPUT -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m state --state NEW,ESTABLISHED -j ACCEPT

From what I read (due to iptables being stateful), the output section will allow all outgoing traffic in response to an already established incoming connection - it won't however allow traffic initiated from the local machine :)

At the very end of my script I like to have:
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP

That way everything that doesn't match any of my previous rules gets dropped.  Here are a few things I have in my own script which I feel add to security, like I said I'm not an expert so maybe it's not right or doesn't even work these days ;)

# Drop fragmented packets
iptables -A INPUT -f -j LOG_DROP

# Drop source routed packets
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route

# Enable TCP SYN cookie protection from SYN floods
echo 1 > /proc/sys/net/ipv4/tcp_syncookies

# Enable source address spoofing protection
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter

# Log packets with impossible source addresses
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians

Hope that helps and I hope others have suggestions since like I said, I'm not an expert, so apologies if I'm steering you down the wrong track.   I'm pretty confident with what I suggested though ;)

I also use:

# Drop tcp connection requests
iptables -A INPUT -p tcp --tcp-flags ALL SYN,ACK -j LOG_DROP

but I'm not sure how helpful that would be, mine is just for desktop use without running any servers (hopefully ;) ).

Take care of yourself.

---


---
title: "does htb qdisc work in gutsy at all?"
date: 2007-12-23
forum: Server Platforms
---

### Post by GSMD on 2007-12-23
I'm trying to setup a simple QOS implementation on my home router running Ubuntu Gutsy (kernel 2.6.22). The complete script is below, I'd like to mention one of the parts that doesn't function as expected.
```

tc qdisc add dev ppp0 root handle 3:0 htb default 30
tc class add dev ppp0 parent 3:0 classid 3:1 htb rate 220kbit #for a 256k link
# the default one
tc class add dev ppp0 parent 3:1 classid 3:30 htb rate 10kbit ceil 220kbit burst 6k prio 3
# for p2p traffic
tc class add dv ppp0 parent 3:1  classid 3:50 htb rate 5kbit ceil 6kbit prio 5
# p2p client running on LAN and port 10720 is DNATed to ppp0
tc filter add dev ppp0 parent 3: protocol ip u32 match ip sport 10720   0xff flowid 3:50

```
Now, consider 2 options: 1)the last line is commented out and 2)the last line is uncommented.
1) p2p traffic gets to the default class 3:30 and shapes accordingly to ceil. No prob here.
2) p2p traffic gets to 3:50 (checked with 'tc -s -d class show dev ppp0', it really does) and consumes all the bandwidth (uploading files)! The ceil of 6 kbytes doesn't matter at all!

Shaping of incoming traffic partly works on eth0 (e.g. ceil really limits) yet listening to a streaming radio becomes impossible when p2p is active. That shouldn't be. Besides, even with no other inbound traffic, p2p is really slow, occupying some 5-10% of the available bandwidth.

Do I get something wrong?

TIA.

```

#!/bin/bash

# The scpript for shaping traffic.

## Interfaces
# rates in kilobits.

# Traffic direction
# Against LAN
# 
# LAN interface,
# shaping incoming traffic
LAN=eth0
LAN_BW=1024000 #1 Gbit
# WAN interface,
# shaping outgoing traffic
WAN=eth1
WAN_BW=102400 #100 Mbit
VPN_SERVER=192.168.1.254 # to track inet traffic going through WAN
# Inet interface, established over eth1
# shaping outgoing traffic
INET=ppp0
INET_UP=250
INET_DOWN=250
INET_IP=19.152.13.1

# Cleanup first
tc qdisc del dev $LAN  root    &> /dev/null
tc qdisc del dev $WAN  root    &> /dev/null
tc qdisc del dev $INET root    &> /dev/null
tc qdisc del dev $LAN  ingress &> /dev/null
tc qdisc del dev $WAN  ingress &> /dev/null
tc qdisc del dev $INET ingress &> /dev/null

# Just in case
sleep 2

## Root hierarchy
tc qdisc add dev $LAN  root handle 1:0 htb default 30
tc qdisc add dev $WAN  root handle 2:0 htb default 30
tc qdisc add dev $INET root handle 3:0 htb default 30
# Root classes
tc class add dev $LAN  parent 1:0 classid 1:1 htb rate "$LAN_BW"kbit
tc class add dev $WAN  parent 2:0 classid 2:1 htb rate "$WAN_BW"kbit
tc class add dev $INET parent 3:0 classid 3:1 htb rate "$INET_UP"kbit

#####################
### LAN Unlimited ###
#####################
tc class add dev $LAN  parent 1:1 classid 1:90 htb rate $((LAN_BW - INET_DOWN))kbit ceil "$LAN_BW"kbit prio 10

####################
### Internet #######
####################

# Highest priority: ICMP, SSH, VoIP
tc class add dev $LAN  parent 1:1 classid 1:10 htb rate 10kbit ceil "$INET_DOWN"kbit burst 6k prio 1
tc class add dev $INET parent 3:1 classid 3:10 htb rate 10kbit ceil "$INET_UP"kbit burst 6k prio 1

# High priority: Online Radios
tc class add dev $LAN  parent 1:1 classid 1:20 htb rate 130kbit ceil "$INET_DOWN"kbit burst 6k prio 2
tc class add dev $INET parent 3:1 classid 3:20 htb rate 10kbit ceil "$INET_UP"kbit burst 6k prio 2

# Default: Browsing, etc.
tc class add dev $LAN  parent 1:1  classid 1:30 htb rate 10kbit ceil "$INET_DOWN"kbit burst 6k prio 3
tc class add dev $INET parent 3:1 classid 3:30 htb rate 10kbit ceil "$INET_UP"kbit burst 6k prio 3

# Normal priority: Services running on the box available on the Internet
tc class add dev $INET parent 3:1 classid 3:40 htb rate 10kbit ceil $((9*INET_UP/10))kbit burst 6k prio 4

# Lowest priority:p2p and the like
tc class add dev $LAN  parent 1:1  classid 1:50 htb rate 5kbit ceil $((9*INET_DOWN/10))kbit prio 5
tc class add dev $INET parent 3:1  classid 3:50 htb rate 5kbit ceil $((9*INET_UP/10))kbit prio 5

###########
### WAN ###
###########

# Bandwidth reserved for Inet, overhead taken into account
tc class add dev $WAN parent 2:1 classid 2:10 htb rate $((INET_DOWN*2))kbit prio 1

# Streaming services
tc class add dev $WAN parent 2:1 classid 2:20 htb rate 512kbit ceil "$WAN_BW"kbit prio 2

# Bulk traffic
tc class add dev $WAN parent 2:1 classid 2:30 htb rate 256kbit ceil $((9*WAN_BW/10))kbit prio 3


#############
### Rules ###
#############

#### Inet ###
## :10

# TOS 0x10
tc filter add dev $LAN  parent 1: protocol ip u32 match ip tos 0x10 0xff  flowid 1:10
tc filter add dev $INET parent 3: protocol ip u32 match ip tos 0x10 0xff  flowid 3:10

# ICMP
tc filter add dev $LAN  parent 1: protocol ip u32 match ip protocol 1 0xff flowid 1:10
tc filter add dev $INET parent 3: protocol ip u32 match ip protocol 1 0xff flowid 3:10

#ssh
tc filter add dev $LAN  parent 1: protocol ip u32 match ip sport 22   0xff flowid 1:10
tc filter add dev $INET parent 3: protocol ip u32 match ip dport 22   0xff flowid 3:10


## :20
# streaming
tc filter add dev $LAN  parent 1: protocol ip u32 match ip sport 8000   0xff flowid 1:20
tc filter add dev $INET parent 3: protocol ip u32 match ip dport 8000   0xff flowid 3:20

## :30
# Default one, no rules required

## :40
tc filter add dev $INET parent 3: protocol ip u32 match ip sport 80  0xff flowid 3:40
tc filter add dev $INET parent 3: protocol ip u32 match ip sport 25  0xff flowid 3:40

## :50
# TORRENT
tc filter add dev $LAN  parent 1: protocol ip u32 match ip dport 10720   0xff flowid 1:50
tc filter add dev $INET parent 3: protocol ip u32 match ip sport 10720   0xff flowid 3:50

###########
### WAN ###
###########
tc filter add dev $WAN parent 2: protocol ip u32 match ip dst "$VPN_SERVER"/32 flowid 2:10

# No limits for private subnets => behind WAN
tc filter add dev $LAN parent 1: protocol ip u32 match ip src 192.168.0.0/16 flowid 1:90
tc filter add dev $LAN parent 1: protocol ip u32 match ip src 172.16.0.0/12  flowid 1:90
tc filter add dev $LAN parent 1: protocol ip u32 match ip src 10.0.0.0/8     flowid 1:90

```

---

### Post by GSMD on 2007-12-24
Updated the first post with a trivial example.

---


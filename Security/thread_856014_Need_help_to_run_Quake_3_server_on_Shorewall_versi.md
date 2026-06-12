---
title: "Need help to run Quake 3 server on Shorewall version 3.2.6"
date: 2008-07-11
forum: Security
---

### Post by Denbert on 2008-07-11
Hi there,

I'm total stuck in this.

I have NO problems, with controlling port 80, 22, 21 and other TCP ports.

But to open UDP port 27960 is very difficult for me, I've searched google, but can't find a solution, therefore I ask the experts in here.

My OS is Debian Etch 64 bit

# uname -a
Linux sauron 2.6.18-6-amd64 #1 SMP Fri Jun 6 05:24:08 UTC 2008 x86_64 GNU/Linux

My policy:

## Comments, comments, and more comments.
#SOURCE         DEST            POLICY          LOG LEVEL       LIMIT:BURST
#
loc        net         ACCEPT
net        all         DROP
loc        $FW         ACCEPT
$FW        net         ACCEPT
# THE FOLLOWING POLICY MUST BE LAST
all        all         REJECT
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

My Rules:

#############################################################################################################
#ACTION        SOURCE        DEST        PROTO    DEST    SOURCE        ORIGINAL    RATE        USER/
#                            PORT    PORT(S)        DEST        LIMIT        GROUP
#                                PORT    PORT(S) DEST            LIMIT    GROUP
#
#    Accept DNS connections from the firewall to the network
#
DNS/ACCEPT    $FW        net
#
#    Accept SSH connections from network AND internet for administration
#
SSH/ACCEPT    loc        $FW
SSH/ACCEPT    net            $FW
#
#    Allow Ping from the local network
#
Ping/ACCEPT    loc        $FW

#
# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..
#

Ping/REJECT    net        $FW

ACCEPT        $FW        loc        icmp
ACCEPT        $FW        net        icmp

#
# Quakeserver settings

ACCEPT    net    $FW   udp       27960
ACCEPT  $FW     net     udp       27960
#
# Webserver
#

ACCEPT  net    $FW     tcp      80
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

Anyone please?

---


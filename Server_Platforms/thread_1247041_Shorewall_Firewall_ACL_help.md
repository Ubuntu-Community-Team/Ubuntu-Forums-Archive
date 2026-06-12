---
title: "Shorewall Firewall ACL help"
date: 2009-08-22
forum: Server Platforms
---

### Post by jfmanamtr on 2009-08-22
I suppose a little background is in order. I run a few services on my server (DNS, DHCP, SAMBA, SSH, FTP, APACHE, FIREFLY & WEBMIN). I have been having issues with people trying to modify those services. So, I was trying to setup an ACL using UFW to define what places can use what services. I ran into a lot of troubles with that & decided to scrap that idea. I am trying to use shorewall to do the same thing ( I had heard that the configs for shorewall were easier than UFW). I am still having troubles when I turn shorewall on. On my server (where I am setting up the ACL) , I can ping local & external address & names, SSH to the server & still access the FTP. However if I try any of that from the workstation, it rejects it. So, I am on here trying to ask for some help. I am attaching all the config files out of /etc/shorewall. Any ideas or thoughts on how to setup an ACL?
~John

/etc/shorewall/interface
```

#
# Shorewall version 4 - Interfaces File
#
# For information about entries in this file, type "man shorewall-interfaces"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-interfaces.html
#
###############################################################################
#ZONE   INTERFACE       BROADCAST       OPTIONS
net     eth0            detect          dhcp,tcpflags,logmartians,nosmurfs
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```/etc/shorewall/policy
```

#
# Shorewall version 4 - Policy File
#
# For information about entries in this file, type "man shorewall-policy"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-policy.html
#
###############################################################################
#SOURCE         DEST            POLICY          LOG             LIMIT:BURST
#                                         LEVEL
$FW                  net               ACCEPT
net                   $FW              DROP            info
net                   all                 DROP            info
# The FOLLOWING POLICY MUST BE LAST
all                    all                 REJECT          info
#LAST LINE -- DO NOT REMOVE

```/etc/shorewall/rules
```

#
# Shorewall version 4 - Rules File
#
# For information on the settings in this file, type "man shorewall-rules"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-rules.html
#
############################################################################################################################
#ACTION      SOURCE             DEST    PROTO   DEST    SOURCE  ORIGINAL
#                                               PORT    PORT(S) DEST

#allow DNS requests from the local network
DNS/ACCEPT   net:192.168.1.0/24 $FW

#allow FTP requests from the local network
FTP/ACCEPT   net:192.168.1.0/24 $FW

#allow PING requests from the local network
Ping/ACCEPT  net:192.168.1.0/24  $FW

#allow DHCP requests from the local network
ACCEPT       net:192.168.1.0/24 $FW     UDP     67
ACCEPT       net:192.168.1.0/24 $FW     UDP     68

#allow ICMP from firewall to the network
ACCEPT       $FW                net             icmp
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```/etc/shorewall/zones
```

#
# Shorewall version 4 - Zones File
#
# For information about this file, type "man shorewall-zones"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-zones.html
#
###############################################################################
#ZONE   TYPE            OPTIONS         IN                      OUT
#                                       OPTIONS                 OPTIONS
fw      firewall
net     ipv4
#LAST LINE - ADD YOUR ENTRIES ABOVE THIS ONE - DO NOT REMOVE

```iptables -L -n (with the firewall running)
```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
eth0_in    all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
Reject     all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:INPUT:REJECT:'
reject     all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
eth0_fwd   all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
Reject     all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:FORWARD:REJECT:'
reject     all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
eth0_out   all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
Reject     all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:OUTPUT:REJECT:'
reject     all  --  0.0.0.0/0            0.0.0.0/0

Chain Drop (2 references)
target     prot opt source               destination
reject     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:113
dropBcast  all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 code 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11
dropInvalid  all  --  0.0.0.0/0            0.0.0.0/0
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 135,445
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:137:139
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:137 dpts:1024:65535
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 135,139,445
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:1900
dropNotSyn  tcp  --  0.0.0.0/0            0.0.0.0/0
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:53

Chain Reject (4 references)
target     prot opt source               destination
reject     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:113
dropBcast  all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 code 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11
dropInvalid  all  --  0.0.0.0/0            0.0.0.0/0
reject     udp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 135,445
reject     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:137:139
reject     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:137 dpts:1024:65535
reject     tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 135,139,445
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:1900
dropNotSyn  tcp  --  0.0.0.0/0            0.0.0.0/0
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:53

Chain all2all (0 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
Reject     all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:all2all:REJECT:'
reject     all  --  0.0.0.0/0            0.0.0.0/0

Chain dropBcast (2 references)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0           PKTTYPE = broadcast
DROP       all  --  0.0.0.0/0            0.0.0.0/0           PKTTYPE = multicast

Chain dropInvalid (2 references)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID

Chain dropNotSyn (2 references)
target     prot opt source               destination
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:!0x17/0x02

Chain dynamic (2 references)
target     prot opt source               destination

Chain eth0_fwd (1 references)
target     prot opt source               destination
dynamic    all  --  0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
smurfs     all  --  0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
tcpflags   tcp  --  0.0.0.0/0            0.0.0.0/0

Chain eth0_in (1 references)
target     prot opt source               destination
dynamic    all  --  0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
smurfs     all  --  0.0.0.0/0            0.0.0.0/0           state INVALID,NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
tcpflags   tcp  --  0.0.0.0/0            0.0.0.0/0
net2fw     all  --  0.0.0.0/0            0.0.0.0/0

Chain eth0_out (1 references)
target     prot opt source               destination
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
fw2net     all  --  0.0.0.0/0            0.0.0.0/0

Chain fw2net (1 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain logdrop (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:logdrop:DROP:'
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain logflags (5 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:logflags:DROP:'
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain logreject (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:logreject:REJECT:'
reject     all  --  0.0.0.0/0            0.0.0.0/0

Chain net2all (0 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
Drop       all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:net2all:DROP:'
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain net2fw (1 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     udp  --  192.168.1.0/24       0.0.0.0/0           udp dpt:53
ACCEPT     tcp  --  192.168.1.0/24       0.0.0.0/0           tcp dpt:53
ACCEPT     tcp  --  192.168.1.0/24       0.0.0.0/0           tcp dpt:21
ACCEPT     icmp --  192.168.1.0/24       0.0.0.0/0           icmp type 8
ACCEPT     udp  --  192.168.1.0/24       0.0.0.0/0           udp dpt:67
ACCEPT     udp  --  192.168.1.0/24       0.0.0.0/0           udp dpt:68
Drop       all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:net2fw:DROP:'
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain reject (11 references)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0           PKTTYPE = broadcast
DROP       all  --  0.0.0.0/0            0.0.0.0/0           PKTTYPE = multicast
DROP       all  --  255.255.255.255      0.0.0.0/0
DROP       all  --  224.0.0.0/4          0.0.0.0/0
DROP       2    --  0.0.0.0/0            0.0.0.0/0
REJECT     tcp  --  0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset
REJECT     udp  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
REJECT     icmp --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-unreachable
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited

Chain shorewall (0 references)
target     prot opt source               destination

Chain smurfs (2 references)
target     prot opt source               destination
LOG        all  --  192.168.1.255        0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
DROP       all  --  192.168.1.255        0.0.0.0/0
LOG        all  --  255.255.255.255      0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
DROP       all  --  255.255.255.255      0.0.0.0/0
LOG        all  --  224.0.0.0/4          0.0.0.0/0           LOG flags 0 level 6 prefix `Shorewall:smurfs:DROP:'
DROP       all  --  224.0.0.0/4          0.0.0.0/0

Chain tcpflags (2 references)
target     prot opt source               destination
logflags   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x29
logflags   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00
logflags   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06
logflags   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03
logflags   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:0 flags:0x17/0x02
```

---

### Post by jfmanamtr on 2009-08-24
OK, so no ideas on what I am doing wrong here? I have modified the config files (using information I had learned from searching) & still no luck. I am not sure what I am doing wrong. From what I have read the policy & rules files make up the firewall. I will edit the files I posted above to reflect the changes I have made. 

~John

---

### Post by Iowan on 2009-08-24
Any useful information (or assistance) on Shorewall's forum?

Hmmm... I'm still looking for their forum - may have been thinking Smoothwall. Mentioned [here]("http://lists.shorewall.net/pipermail/shorewall-users/2003-February/005389.html"), but that was awhile back.

---

### Post by jfmanamtr on 2009-08-25
I think you may be thinking of Smoothwall (firewall\router distro). All Shorewall does is configure iptables & ipchains for you. I just can't find a forum specific to Shorewall. 

~John

---


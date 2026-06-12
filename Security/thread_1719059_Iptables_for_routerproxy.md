---
title: "Iptables for router/proxy"
date: 2011-04-01
forum: Security
---

### Post by yeleek on 2011-04-01
Hi,

Rather than use pfsense, etc I decided to create my own router/proxy etc based on an atom base with 2 nics.

Proxy/routing/dns/etc all working fine, I now though want to lockdown the fw rules.

ETH1 is the WAN NIC
ETH2 is the LAN NIC

I'm guessing i want to allow anything out of ETH1, but only allow incoming to ETH1 when its established or related...  What about ETH2 though?  Any ideas pls?  Am used to configuring iptables on single nic, certainly not a router.

```

Chain INPUT (policy ACCEPT 18535 packets, 10M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
14111 2942K ACCEPT     all  --  any    eth1    10.1.1.0/24          anywhere            
19385   16M ACCEPT     all  --  eth1   any     anywhere             10.1.1.0/24         state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT 21117 packets, 11M bytes)
 pkts bytes target     prot opt in     out     source               destination 
```

Thanks

---

### Post by BkkBonanza on 2011-04-01
Here's an example of what I have on my mini-itx router.
This is put in a file **/etc/network/if-up.d/routing** were it gets run automatically.
```
#!/bin/bash

WANIF=eth0
LANIF=eth1
WANIP="`ifconfig $WANIF | awk '/inet/ {print $2}' | sed 's/addr://'`"
LANIP="`ifconfig $LANIF | awk '/inet/ {print $2}' | sed 's/addr://'`"
LAN="192.168.2.0/24"

if [ "$IFACE" != "$WANIF" ] || [ "$MODE" != start ] || [ "$WANIP" = "" ]; then
  exit 0
fi


echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians

/sbin/iptables-restore <<-EOF;

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i lo -j ACCEPT
-A INPUT -i $WANIF -s $LAN -j REJECT
-A INPUT -i $WANIF -s 169.254.0.0/16 -j DROP
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -i $LANIF -p tcp --dport 22 -j ACCEPT
-A INPUT -i $LANIF -p tcp --dport 631 -j ACCEPT
-A INPUT -i $LANIF -p udp --dport 631 -j ACCEPT
-A INPUT -i $LANIF -p udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i $WANIF -p udp --sport 67 --dport 68 -j ACCEPT
-A INPUT -i $LANIF -p tcp --dport 53 -j ACCEPT
-A INPUT -i $LANIF -p udp --dport 53 -j ACCEPT

-A OUTPUT -o $WANIF -d $LAN -j REJECT

-A FORWARD -i $WANIF -o $LANIF -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i $LANIF -o $WANIF -j ACCEPT
COMMIT

*nat 
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]

-A POSTROUTING -o $WANIF -j SNAT --to $WANIP

COMMIT
EOF


```
It filters a few things that shouldn't occur besides just allowing normal traffic. There are no port forwarding rules though that may be needed sometimes.

631 is CUPS - my router is also print server
67,68 are DHCP - allows DHCP server in LAN and client to outside LAN
53 is DNS - allowed out
22 is SSH - allowed only from LAN

---

### Post by yeleek on 2011-04-01
Thanks for that.  Very helpful

1 question with a default policy of drop for input (which should drop anything not specified shouldn't it) and already specifying established/related.  Why specify specifically these two?  

The first one would seem to be reject traffic if it comes in WANIF but uses range of LAN (192.168.x.y which shouldn't be routable on internet anyway should it?

and

The isn't the second one similar but for the automatic ip addressing thing?  Or am I reading all this wrong?


-A INPUT -i $WANIF -s $LAN -j REJECT
-A INPUT -i $WANIF -s 169.254.0.0/16 -j DROP

Thank you!

---

### Post by yeleek on 2011-04-01
Actually trying to lock it down, and having issues.  Now configured this:

```
Chain INPUT (policy DROP 16 packets, 1019 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  557 43556 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:ssh 
    3   201 ACCEPT     all  --  eth1   any     anywhere             anywhere            state RELATED,ESTABLISHED 
   21  6670 ACCEPT     all  --  eth2   any     10.1.1.0/24          anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   56  4749 ACCEPT     all  --  any    eth1    10.1.1.0/24          anywhere            
   57  7483 ACCEPT     all  --  eth1   any     anywhere             10.1.1.0/24         state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT 448 packets, 72369 bytes)
 pkts bytes target     prot opt in     out     source               destination  
```

This router/firewall/dns/etc also has squid running on 3128.  Now web browsing via proxy isn't functioning, but shouldn't my combination below allow for this?

```
3   201 ACCEPT     all  --  eth1   any     anywhere             anywhere            state RELATED,ESTABLISHED 
   21  6670 ACCEPT     all  --  eth2   any     10.1.1.0/24          anywhere            

```

Actually proxy just came back saying DNS server timeout when trying to reach [www.bbc.co.uk](www.bbc.co.uk) (which is up), but again shouldn't the two rules above cover this?
Thank you

---

### Post by BkkBonanza on 2011-04-01
> **yeleek said:**
> Thanks for that.  Very helpful

1 question with a default policy of drop for input (which should drop anything not specified shouldn't it) and already specifying established/related.  Why specify specifically these two?  

The first one would seem to be reject traffic if it comes in WANIF but uses range of LAN (192.168.x.y which shouldn't be routable on internet anyway should it?

and

The isn't the second one similar but for the automatic ip addressing thing?  Or am I reading all this wrong?


-A INPUT -i $WANIF -s $LAN -j REJECT
-A INPUT -i $WANIF -s 169.254.0.0/16 -j DROP

Thank you!

I have these two for two reasons. 1. As a safety in case spoofed IP packets manage to get to my router, but more importantly, 2. my router isn't connected directly to the internet. On the outside my router is connected to another LAN for my apartment building and with 160 odd other users in the apartment I have these to make block anything I really don't want in based on origin rather than destination.

I was getting a lot of random 169.254.x.x traffic probably from Windows machines in my building, so I just added that to cut it out. I figure it's safer to block stuff I should never see as precaution. Traffic from these locations could still get in if it was behaving as allowed traffic, or if someone was being malicious and trying to piggyback on established traffic.

---

### Post by BkkBonanza on 2011-04-01
> **yeleek said:**
> 
This router/firewall/dns/etc also has squid running on 3128.  Now web browsing via proxy isn't functioning, but shouldn't my combination below allow for this?

```
3   201 ACCEPT     all  --  eth1   any     anywhere             anywhere            state RELATED,ESTABLISHED 
   21  6670 ACCEPT     all  --  eth2   any     10.1.1.0/24          anywhere            

```

Actually proxy just came back saying DNS server timeout when trying to reach [www.bbc.co.uk](www.bbc.co.uk) (which is up), but again shouldn't the two rules above cover this?
Thank you

They seem ok to me but often you have to re-check over them carefully and it's easy to get mixed up. I have an iptables flow diagram [here]("http://postimage.org/image/350n5z37o/") that I like to use to clarify how it works.

In the end it always turns out to be user error rather than iptables error. So just double-triple check... :(

---

### Post by yeleek on 2011-04-01
Thank you for the help :)

I added lo and all seems working now.  

```
Chain INPUT (policy DROP 3996 packets, 240K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   98 17182 ACCEPT     all  --  lo     any     anywhere             anywhere            
 2291  314K ACCEPT     all  --  eth2   any     10.1.1.0/24          anywhere            
  774 59936 ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:ssh 
  994  976K ACCEPT     all  --  eth1   any     anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  434 58983 ACCEPT     all  --  any    eth1    10.1.1.0/24          anywhere            
  370 62457 ACCEPT     all  --  eth1   any     anywhere             10.1.1.0/24         state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT 6083 packets, 2899K bytes)
 pkts bytes target     prot opt in     out     source               destination  
```

I want remote access via SSH to my atom router, the above all seem reasonable in your opinion?

---

### Post by BkkBonanza on 2011-04-01
Seems reasonable. You can always fine tune it as you go. It didn't occur to me that squid uses loopback for it's workings - makes sense though.

You may want to move ssh to another high port. It won't hide you from someone who really wants to find you but it does cut down on a lot of log entries as hackers often scan port 22 and bang on it to see if they can get in. Moving the port isn't nearly as important as using a good password or better still, a key. If you know you will only access ssh from specific locations you might add a rule to drop anything not from those locations.

---

### Post by yeleek on 2011-04-01
Thanks :)

---


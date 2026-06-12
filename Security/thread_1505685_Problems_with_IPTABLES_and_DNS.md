---
title: "Problems with IPTABLES and DNS"
date: 2010-06-09
forum: Security
---

### Post by warriorforgod on 2010-06-09
I have an ubuntu box set up serving as a firewall/gateway/router for my network.  I am also running DHCP and DNS on this box for the nework.  eth0 is the card for my internal network, and eth1 is connected to the outside world.  When I use the following iptables rules the gentoo box itself can get to the outside world, however none of the internal boxes can resolve anything through DNS.   The following Items show up in the logs when I turn on these rules.  Any help to get this working is appreciated in advance.

```

Jun  9 08:35:21 thegatekeeper kernel: [315817.488161] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.190.178.129 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47392 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.488232] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.175.196.129 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47393 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.488776] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=24.252.60.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47394 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.488834] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.187.4.161 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47395 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.488909] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.186.246.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47396 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.488972] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.175.197.193 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47397 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.489774] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.188.36.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47398 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.489850] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=10.106.252.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47399 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.489921] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.179.50.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47400 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.489990] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.188.201.97 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47401 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.490061] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.188.208.33 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47402 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.490129] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.188.208.161 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47403 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.490424] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=174.69.80.9 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47404 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.490496] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=70.182.207.129 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47405 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.490747] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=98.188.209.193 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47406 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.491273] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=174.69.85.17 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47407 PROTO=2 
Jun  9 08:35:21 thegatekeeper kernel: [315817.491343] INPUT_DROP_DEFAULT IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:30:b8:ce:82:a0:08:00 SRC=174.78.68.97 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=47408 PROTO=2 
Jun  9 08:35:24 thegatekeeper kernel: [315820.171588] INPUT_DROP_DEFAULT IN=eth0 OUT= MAC=00:10:4b:1f:45:6e:00:12:17:e2:53:fc:08:00 SRC=192.168.1.127 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=45346 DF PROTO=UDP SPT=59487 DPT=53 LEN=40 
Jun  9 08:35:26 thegatekeeper kernel: [315821.762621] FORWARD_DROP_DEFAULT IN=eth0 OUT=eth1 SRC=192.168.1.126 DST=72.215.225.9 LEN=72 TOS=0x00 PREC=0x00 TTL=127 ID=58738 PROTO=UDP SPT=427 DPT=427 LEN=52 

```

Here is the firewall rules.
```

IPTABLES=/sbin/iptables
IP6TABLES=/sbin/ip6tables
MODPROBE=/sbin/modprobe
INT_NET=192.168.1.0/24

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### this policy does not handle IPv6 traffic except to drop it.
#
echo "[+] Disabling IPv6 traffic..."
$IP6TABLES -P INPUT DROP
$IP6TABLES -P OUTPUT DROP
$IP6TABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "INPUT_DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j LOG --log-prefix "INPUT_SPOOFED PKT "
$IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

### make sure that loopback traffic is accepted
$IPTABLES -A INPUT -s 127.0.0.1 -p tcp -j ACCEPT
$IPTABLES -A INPUT -s 127.0.0.1 -p udp -j ACCEPT
$IPTABLES -A INPUT -i lo -j ACCEPT

### default INPUT LOG rule
$IPTABLES -A INPUT ! -i lo -j LOG --log-prefix "INPUT_DROP_DEFAULT " --log-ip-options --log-tcp-options

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

### state tracking rules
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "OUTPUT_DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 53 -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

### default OUTPUT LOG rule
$IPTABLES -A OUTPUT ! -o lo -j LOG --log-prefix "OUTPUT_DROP_DEFAULT " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A OUTPUT -o lo -j ACCEPT

###### FORWARD chain ######
#
echo "[+] Setting up FORWARD chain..."

### state tracking rules
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "FORWARD_DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A FORWARD ! -i eth0 -s $INT_NET -j LOG --log-prefix "FORWARD_SPOOFED PKT "
$IPTABLES -A FORWARD ! -i eth0 -s $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 53 -j ACCEPT
$IPTABLES -A FORWARD -p udp --dport 53 -j ACCEPT
$IPTABLES -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT

### default LOG rule
$IPTABLES -A FORWARD ! -i lo -j LOG --log-prefix "FORWARD_DROP_DEFAULT " --log-ip-options --log-tcp-options

###### NAT rules ######
#
echo "[+] Setting up NAT rules..."
#$IPTABLES -t nat -A PREROUTING -p tcp --dport 80 -i eth0 -j DNAT --to 192.168.10.3:80
$IPTABLES -t nat -A PREROUTING -p tcp --dport 53 -i eth0 -j DNAT --to 192.168.1.1:53
$IPTABLES -t nat -A PREROUTING -p udp --dport 53 -i eth0 -j DNAT --to 192.168.1.1:53
$IPTABLES -t nat -A PREROUTING -p tcp --dport 1982 -i eth0 -j DNAT --to 192.168.1.127:22
$IPTABLES -t nat -A POSTROUTING -s $INT_NET -o eth0 -j MASQUERADE

###### forwarding ######
#
echo "[+] Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

exit

```

---

### Post by The Cog on 2010-06-09
At first glance, I can't see anything wrong with that. Perhaps try this command and watch what happens as your clients try a DNS lookup it prints the iptables counters (nat and filter) every 2 secs, highlighting changes:

watch -d iptables-save -c

---

### Post by bodhi.zazen on 2010-06-09
My guess is your input is eth1 

$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPT

change (or add) -i eth0 to -i eth1

Use iptables -L -v -n to see where packets are dropped.

---

### Post by WinstonChurchill on 2010-06-09
You're missing one thing.

You allow BIND's outgoing DNS queries:```
$IPTABLES -A OUTPUT -p tcp --dport 53 -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -j ACCEPT
```You allow answers to BIND's DNS queries:```
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```And you allow your LAN boxes query BIND:```
$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPT
```... but you don't allow BIND to answer your LAN boxes DNS queries - add this:```
$IPTABLES -A OUTPUT -i eth0 -p udp --sport 53 --j ACCEPT
$IPTABLES -A OUTPUT -i eth0 -p tcp --sport 53 --j ACCEPT
```The reason you need the "--sport" rule is that the DNS queries from your LAN boxes don't come from port 53 - they come from an ephemeral port (1024:65535 in Windows, usually 32768:61000 in Linux), and iptables is dropping the answers because they aren't going to port 53. The ESTABLISHED,RELATED rule in the OUTPUT chain doesn't help, because conntrack doesn't consider the connection ESTABLISHED unless it has seen traffic in both directions - in the OUTPUT chain, that rule basically says "You're forbidden to speak to anybody you haven't already initiated a conversation with"... but you can't initiate a conversation because you can't speak to them because you haven't already initiated a conversation because you can't speak to them..... you get the idea. Also, FYI, you don't really need to allow TCP on port 53 at all - I have a  setup very similar to yours, and all it ever uses is UDP; TCP is only  ever used for zone transfers (although technically it can be used for  queries...)

Also, with your current setup the IPv6 loopback address doesn't work, which isn't likely a very big deal, but it could cause you issues in the future, and you don't gain anything from disabling it. I'd add the following:```
ip6tables --append INPUT --in-interface lo --jump ACCEPT
ip6tables --append OUTPUT --out-interface lo --jump ACCEPT
```

---

### Post by The Cog on 2010-06-10
> .. but you don't allow BIND to answer your LAN boxes DNS queries
I think this probably covers that issue:
> $IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT



These seem to work together to stop things working (thanks for the pointer, Bodhi):
```
### anti-spoofing rules
$IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j LOG --log-prefix "INPUT_SPOOFED PKT "
$IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

```
Since you say that eth0 is your local LAN, I think you need to change the anti-spoofing rules to drop packets arriving from eth1 instead.

I believe there is an inbuilt anti-spoofing mechanism in the kernel. You can see if it's enabled with the command:
```
cat /proc/sys/net/ipv4/conf/all/rp_filter
```
and I think you can set it by editing /etc/sysctl.conf.

---

### Post by bodhi.zazen on 2010-06-10
> **The Cog said:**
> I think this probably covers that issue:




These seem to work together to stop things working (thanks for the pointer, Bodhi):
```
### anti-spoofing rules
$IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j LOG --log-prefix "INPUT_SPOOFED PKT "
$IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

```Since you say that eth0 is your local LAN, I think you need to change the anti-spoofing rules to drop packets arriving from eth1 instead.

I believe there is an inbuilt anti-spoofing mechanism in the kernel. You can see if it's enabled with the command:
```
cat /proc/sys/net/ipv4/conf/all/rp_filter
```and I think you can set it by editing /etc/sysctl.conf.

I find these scripts to configure iptables to be difficult to read. It helps if the OP describes the architecture of the network, what the subnets are, and the goals of the configuration. Sure it is sort of generic, but these little details help.

In terms of kernel security , edit /etc/sysctl.conf :

> # TCP SYN Cookie Protection (prevent SYN DOS)
net.ipv4.tcp_syncookies = 1

# IP Spoof Protection
net.ipv4.conf.all.rp_filter = 1

Then

```
sudo  sysctl -p
```

See also : [http://raj-kumar-linux.blogspot.com/2010/03/kernel-tunable-security-parameters.html](http://raj-kumar-linux.blogspot.com/2010/03/kernel-tunable-security-parameters.html)

---

### Post by warriorforgod on 2010-06-10
> **bodhi.zazen said:**
> I find these scripts to configure iptables to be difficult to read. It helps if the OP describes the architecture of the network, what the subnets are, and the goals of the configuration. Sure it is sort of generic, but these little details help.


The network consists of the firewall/gateway box that is also running dhcp and dns for the network.  The subnetting is 192.168.1.0/24, and the goal is to have the firewall/gateway box serve as the entry/exit point for the network to the internet, and also provide dhcp and dns.

---

### Post by bodhi.zazen on 2010-06-10
> **warriorforgod said:**
> The network consists of the firewall/gateway box that is also running dhcp and dns for the network.  The subnetting is 192.168.1.0/24, and the goal is to have the firewall/gateway box serve as the entry/exit point for the network to the internet, and also provide dhcp and dns.

I understand all that. The question is what is on eth0 ? eth1 ? What traffic do you wish to allow ? What traffic do you wish to block ?

Without knowing your architecture and goals it is hard to read and debug your iptables script.

---

### Post by warriorforgod on 2010-06-10
eth0 is the internal interface and eth1 is the external interface.  I wish to allow an ssh connection to 1 internal server, and normal web/ssh traffic outbound.  I think if I can get the DNS issue worked out everything else will go smooth.  It seems from the logs that the default input rule is what is dropping packets.

---

### Post by WinstonChurchill on 2010-06-10
The Cog:

Yes, the "$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j  ACCEPT" rule allows the LAN queries, but his OUTPUT policy is DROP, and  he doesn't have a rule that allows his server to OUTPUT answers to the  LAN. 

His rule:```
$IPTABLES -A OUTPUT -p tcp --dport 53 -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -j ACCEPT
```attempts to do this, but it doesn't match because the destination port of the DNS replies is the port the LAN box used to initiate the query, which is an ephemeral port, not 53

His "ESTABLISHED,RELATED" rule in the OUTPUT chain does not work - ipt_conntrack doesn't consider the connection ESTABLISHED because it has only seen one UDP input packet. The "-m state ESTABLISHED,RELATED" rule should not be used in the OUTPUT chain.

I'm quite certain that if he adds the rule:```
iptables --append OUTPUT --out-interface eth0 --protocol udp --sport 53 --jump ACCEPT
```his LAN boxes will be able to perform DNS resolutions.

---

### Post by warriorforgod on 2010-06-10
What if anything would changing

> $IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPT

to 

> $IPTABLES -A INPUT -p udp -m udp --dport 53 -j ACCEPT

do?  I am wondering if this would decrease security in any way.

---

### Post by The Cog on 2010-06-11
> **WinstonChurchill said:**
> The Cog:

Yes, the "$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j  ACCEPT" rule allows the LAN queries, but his OUTPUT policy is DROP, and  he doesn't have a rule that allows his server to OUTPUT answers to the  LAN. 

Dang, I posted the wrong rule. He does have a rule
> $IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT that will permit the replies to the queries.

Let's go through it bit-by-bit:
Firstly the dns query arrives from local pc (on eth0 according to his post):
intercepted and redirected to local bind server:
> $IPTABLES -t nat -A PREROUTING -p udp --dport 53 -i eth0 -j DNAT --to 192.168.1.1:53
The redirected query is received on the input chain (I assume this PC is 192.168.1.1):
> $IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j LOG --log-prefix "INPUT_SPOOFED PKT "
$IPTABLES -A INPUT ! -i eth0 -s $INT_NET -j DROP
There it is, on the floor! With a pile of other dropped queries. But let's assume it wasn't dropped, and wee what would have happened:
> $IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPTSo the request should be accepted, and conntrack should make a note that we now have an incoming "connection (1)" from the PC to UDP:53. The DNS server will try to make its own internet query to get the answer:> $IPTABLES -A OUTPUT -p udp --dport 53 -j ACCEPTSo the outgoing dns request is permitted, and conntrack notes that we have an existing outgoing dns "connection (2)". The internet will send a dns reply:> $IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPTwill allow the reply in on the existing "connection (2)". Then the local dns server can forward the reply. This was "connection (1)" of course:> $IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPTThis connection will be un-NATted, reversing this rule before forwarding back to the client:> $IPTABLES -t nat -A PREROUTING -p udp --dport 53 -i eth0 -j DNAT --to 192.168.1.1:53
So I think the only problem is the mis-placed anti-spoofing rule, which is checking against the wrong incoming interface. Otherwise, I think dns should work.

Of course, data won't work because he has the same error in is forwarding anti-spoofing rules - he's dropping the packets before they reach the accept rules:
> ### anti-spoofing rules
$IPTABLES -A FORWARD ! -i eth0 -s $INT_NET -j LOG --log-prefix "FORWARD_SPOOFED PKT "
$IPTABLES -A FORWARD ! -i eth0 -s $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth0 -s $INT_NET --dport 43 --syn -m state --state NEW -j ACCEPT


---

### Post by WinstonChurchill on 2010-06-11
My mistake - I totally missed the NAT rules at the bottom of his script... are those even necessary? I have a server that does exactly what he's trying to do, and the only NAT rule I need is the "... -j MASQUERADE" rule.

---

### Post by The Cog on 2010-06-11
I think the NAT rule is hijacking outgoing DNS requests from the PCs so that they are forced to use his DNS server. Why, I don't know.

---

### Post by The Cog on 2010-06-11
> **warriorforgod said:**
> What if anything would changing
> $IPTABLES -A INPUT -i eth0 -p tcp -s $INT_NET --dport 53 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p udp -s $INT_NET --dport 53 -j ACCEPTto [QUOTE]$IPTABLES -A INPUT -p udp -m udp --dport 53 -j ACCEPT
do?  I am wondering if this would decrease security in any way.[/QUOTE]That would allow people on the internet to query his DNS server as well, which he probably doesn't want. It wouldn't fix the anti-spoof rule that's currently discarding all his user traffic as it enters eth0.

---


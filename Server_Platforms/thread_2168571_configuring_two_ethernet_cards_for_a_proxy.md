---
title: "configuring two ethernet cards for a proxy"
date: 2013-08-18
forum: Server Platforms
---

### Post by sophie_horner on 2013-08-18
What's the basic procedure to get two Ethernet cards to work together on Ubuntu server with squid3 running ?
Can't seem to get it working properly. 
I have one card eth1 with network 198.168.0.0/24  DHCP server for local network here.
The other eth0 with 192.168.1.0/24 connected to ISP router @ 192.168.1.1
I've done an iptable with the basic rules including the squid3 redirect rules
I've given both cards static addresses .... 
The routes seem ok....
Is there a simple way around this type of config ?
Do I have to set up a bridge connection ? If so how ? Because I tried it and it failed... 
Can anyone give me the basic procedure from scratch?? Pleeeese :(

---

### Post by SeijiSensei on 2013-08-18
You need to create different subnets for the internal and external networks.  If both interfaces are in 192.168.1.0/24, the machine won't know how to route packets.

Assign a different subnet like 192.168.2.0/24 to eth1 and its connected devices. 

Where to go from here depends on whether machines connected to eth1 need to use services other than HTTP.  If not, then you can just let Squid proxy the connections.  But if some people need to connect to other external services like HTTPS sites on port 443 or SMTP/IMAP/POP on 25/143/110, you'll need to set up the gateway to do network address translation as well.

To do so, first make sure you enabled packet forwarding by uncommenting the line "net.ipv4.ip_forward=1" in /etc/sysctl.conf and that your iptables rules allow FORWARDing. Next, you'll need these two rules:

```

# send all outbound web traffic to Squid
/sbin/iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --to-ports 3128
# masquerade all other outbound traffic 
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source ip.of.eth0

```

replacing "ip.of.eth0" with its assigned IP address.

---

### Post by sophie_horner on 2013-08-19
Thank you.
I already have two different subnets 0.0 on eth1 1.0 on eth0.
I had a general masquerading line in iptables but I'll try the one you're suggesting with snat.
I'll come back shortly to sum up the whole of my config lines to check through everything if this doesn't work....
Thanks again :)

---

### Post by SeijiSensei on 2013-08-19
Just to check, you do have 

```
http_port 3128 transparent
```

in squid.conf, and an ACL that permits connections to the proxy from 192.168.0.0/24:

```

acl mynetwork src 192.168.0.0/24
http_access allow mynetwork

```

---

### Post by sophie_horner on 2013-08-19
Yep thanks, I'll be back this evening to set everything properly and if I succeed I'll post a nice complete bash so others can use and switch the thread to SOLVED ... Fingers crossed. :)
EDIT next day :
Heyhey ! So glad to see it works even if fine tuning may be needed...
--- Feel free to read through, anyone, and comment in case corrections are needed :)
```
#! /bin/sh
#just for the sake of turning the networks off and on... not sure if it would work turning them back on only at the end of script ?
ifconfig eth0 down;
ifconfig eth1 down;
ifconfig lo down;
ifconfig lo up;
ifconfig eth0 up;
ifconfig eth1 up;
#I seemed to have some issues with the routing table so i thought I throw in a check up :
route add 127.0.0.1 dev lo;
route add -net 127.0.0.0/8 dev lo;
route add -net 192.168.0.0/24 dev eth1;
route add 192.168.1.47 dev eth0;
route add default gw 192.168.1.1;
# turn fowarding off while configuring iptables :
sysctl net/ipv4/ip_forward=0
iptables -F
iptables -X
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD ACCEPT
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
#and on again once the policies are set
sysctl net/ipv4/ip_forward=1
#redirect port 80 on lan card and masquerade on wan card :
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
#accept all packets in lo and protect against spoofing :
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A INPUT -i !lo -s 127.0.0.0/8 -j DROP
iptables -A FORWARD -i !lo -s 127.0.0.0/8 -j DROP
#accept only established input but all output on WAN card
iptables -A OUTPUT -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
#just forget the invalid packets :
iptables -A OUTPUT -o eth0 -m state --state INVALID -j DROP
iptables -A INPUT -i eth0 -m state --state INVALID -j DROP
#not sure whether to put this before or after spoofing protection ?
iptables -A INPUT -i eth1 -j ACCEPT
iptables -A OUTPUT -o eth1 -j ACCEPT
#against spoofing on LAN card input :
iptables -A INPUT -i !eth1 -s 192.168.0.0/24 -j DROP
iptables -A FORWARD -i !eth1 -s 192.168.0.0/24 -j DROP
```

---

### Post by sophie_horner on 2013-08-20
*bump*
I'm just wondering where do logged packets go when you -j LOG them with iptables ? where's the default file ?

---

### Post by Doug S on 2013-08-20
> **sophie_horner said:**
> I'm just wondering where do logged packets go when you -j LOG them with iptables ? where's the default file ?By default the log entries will be in /var/log/syslog and /var/log/kern.log

---

### Post by sophie_horner on 2013-08-21
Thank you :)

---


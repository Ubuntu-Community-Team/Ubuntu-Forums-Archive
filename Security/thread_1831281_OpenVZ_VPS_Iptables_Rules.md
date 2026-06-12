---
title: "OpenVZ VPS Iptables Rules"
date: 2011-08-23
forum: Security
---

### Post by captainKrash on 2011-08-23
Hi there,

I have taken out a low spec VPS to do some learning/dev on and have been doing some basic hardening. The vps runs Ubuntu 11.04 minimal. I would like to add some firewall rules inline with it's intended use as a webserver. 

The services that I want to allow are: 

SSH (on changed port)
HTTP
HTTPS
SMTP (outgoing only from postfix)

I am not intending to run my own DNS as I have pointed an A record from another server. After several manual attempts and much faffing about (inc server reimaging after locking myself out). I stumbled upon this script (from: [http://kipz.org/blog/?p=25](http://kipz.org/blog/?p=25)).

```

#!/bin/bash

# VPS Firewall script
# Copyright (C) 2011, James Carnegie me@kipz.org
# This program may be freely redistributed under the terms of the GNU GPL

# External interface name here
EXTIF="venet0"

# VPS main IP here
EXTIP="xxx.xxx.xxx.xxx"

# Your DNS server
NSIP="xxx.xxx.xxx.xxx"

# Flush iptables
iptables -F

# Setting default filter policy DROP all
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# Allow unlinited traffic on both lo and $EXTIF
iptables -A INPUT  -i $EXTIF -s 127.0.0.1 -j ACCEPT
iptables -A OUTPUT -o $EXTIF -d 127.0.0.1 -j ACCEPT

# Allow loop back to speak to loop back
iptables -A INPUT  -i lo -s 127.0.0.1 -j ACCEPT
iptables -A OUTPUT -o lo -d 127.0.0.1 -j ACCEPT

# Block weird some stuff
iptables -A INPUT -s $EXTIP -j DROP
iptables -A OUTPUT -d $EXTIP -j DROP

# Stop  floods
iptables -N flood
iptables -A INPUT -p tcp --syn -j flood
iptables -A flood -m limit --limit 1/s --limit-burst 3 -j RETURN
iptables -A flood -j DROP

# Drop all incoming fragments
iptables -A INPUT -f -j DROP
# Drop all incoming malformed XMAS packets
iptables -A INPUT -p tcp --tcp-flags ALL ALL -j DROP
# Drop all incoming malformed NULL packets
iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP
# Bad incoming source ip address 0.0.0.0/8
iptables -A INPUT -s 0.0.0.0/8 -j DROP
# Bad incoming source ip address 127.0.0.0/8
iptables -A INPUT -s 127.0.0.0/8 -j DROP
# Bad incoming source ip address 10.0.0.0/8
iptables -A INPUT -s 10.0.0.0/8 -j DROP
# Bad incoming source ip address 172.16.0.0/12
iptables -A INPUT -s 172.16.0.0/12 -j DROP
# Bad incoming source ip address 192.168.0.0/16
iptables -A INPUT -s 192.168.0.0/16 -j DROP
# Bad incoming source ip address 224.0.0.0/3
iptables -A INPUT -s 224.0.0.0/3 -j DROP
# Incoming HTTP/HTTPS
iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d $EXTIP --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp -s $EXTIP --sport 80 -d 0/0 --dport 1024:65535 -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d $EXTIP --dport 443 -j ACCEPT
iptables -A OUTPUT -p tcp -s $EXTIP --sport 443 -d 0/0 --dport 1024:65535 -j ACCEPT

# Incoming SMTP
#iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d $EXTIP --dport 25 -j ACCEPT
#iptables -A OUTPUT -p tcp -s $EXTIP --sport 25 -d 0/0 --dport 1024:65535 -j ACCEPT

# Incoming SSH
iptables -A INPUT -p tcp -s 0/0 --sport 513:65535 -d $EXTIP --dport 22 -j ACCEPT
iptables -A OUTPUT -p tcp -s $EXTIP --sport 22 -d 0/0 --dport 513:65535 -j ACCEPT

# Outgoing DNS
iptables -A OUTPUT -p udp -s $EXTIP --sport 1024:65535 -d $NSIP --dport 53 -j ACCEPT
iptables -A INPUT -p udp -s $NSIP --sport 53 -d $EXTIP --dport 1024:65535 -j ACCEPT
iptables -A OUTPUT -p tcp -s $EXTIP --sport 1024:65535 -d $NSIP --dport 53 -j ACCEPT
iptables -A INPUT -p tcp -s $NSIP --sport 53 -d $EXTIP --dport 1024:65535 -j ACCEPT

# Outgoing ICMP
iptables -A OUTPUT -p icmp -s $EXTIP -d 0/0 -j ACCEPT
iptables -A INPUT -p icmp -s 0/0 -d $EXTIP -j ACCEPT

# Outgoing traceroute
iptables -A OUTPUT -p udp -s $EXTIP --sport 1024:65535 -d 0/0 --dport 33434:33523 -j ACCEPT

# Outgoing SMTP
iptables -A OUTPUT -p tcp -s $EXTIP --sport 1024:65535 -d 0/0 --dport 25 -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --sport 25 -d $EXTIP --dport 1024:65535 -j ACCEPT

# Outgoing SSH
iptables -A OUTPUT -p tcp -s $EXTIP --sport 513:65535 -d 0/0 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --sport 22 -d $EXTIP --dport 513:65535 -j ACCEPT

# outgoing HTTP/HTTPS
iptables -A OUTPUT -p tcp -s $EXTIP --sport 1024:65535 -d 0/0 --dport 80 -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --sport 80 -d $EXTIP --dport 1024:65535 -j ACCEPT
iptables -A OUTPUT -p tcp -s $EXTIP  --sport 1024:65535 -d 0/0 --dport 443 -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --sport 443 -d $EXTIP --dport 1024:65535 -j ACCEPT

# Drop everything else
iptables -A INPUT -s 0/0 -j DROP
iptables -A OUTPUT -d 0/0 -j DROP

```

I changed the SSH port in all the relevant places and replaced the main IP of the vps with the correct IP and DNS server IP with first my host's DNS server IP, then the IP of my VPS and then the IP of a third party DNS service (open DNS). Each time I flushed iptables and checked the loaded rules.

The issue I am having is that with the rules loaded SMTP does not send - though with the rules off SMTP does send.

Output of netstat -t -a | grep LISTEN
```

tcp        0      0 *:52127                 *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 qs1.mydomain.c:domain *:*                     LISTEN     
tcp        0      0 localhost:domain        *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 localhost:953           *:*                     LISTEN     
tcp6       0      0 [::]:52127              [::]:*                  LISTEN     
tcp6       0      0 [::]:www                [::]:*                  LISTEN     
tcp6       0      0 [::]:domain             [::]:*                  LISTEN     
tcp6       0      0 localhost:953           [::]:*                  LISTEN

```

 The problem is obviously DNS related as mail.log reveals this:

```

Aug 23 10:32:57 qs1 postfix/smtp[3799]: 82DD318E2F87: to=<my@mydomain.co.uk>, relay=none, delay=0.11, delays=0.1/0/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=mydomain.co.uk type=MX: Host not found, try again)

```

Sorry for the long winded post, but I thought it might save questions. Aside from disabling iptables rules - what can I do to get mail sending?

Thank you

---

### Post by cepal on 2011-11-14
your problem is not related to firewall but to the postfix configuration. Read the log line carefully, it tells you exactly what's wrong.

---


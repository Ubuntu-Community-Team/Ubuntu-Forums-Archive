---
title: "lsof output: what is &quot;dhclient&quot;?"
date: 2017-10-20
forum: Security
---

### Post by graigster on 2017-10-20
can someone lok at this firewalll  reading and explain to me who this dhclient  14757      root    6u  IPv4 112852      0t0  UDP *:bootpc  is 
```

graigster@graigster-Inspiron-1545:~$ sudo lsof +M -i4
COMMAND     PID      USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae   799     avahi   12u  IPv4  19441      0t0  UDP *:mdns 
avahi-dae   799     avahi   14u  IPv4  19443      0t0  UDP *:35779 
dnsmasq     953    nobody    4u  IPv4  20247      0t0  UDP graigster-Inspiron-1545:domain 
dnsmasq     953    nobody    5u  IPv4  20248      0t0  TCP graigster-Inspiron-1545:domain (LISTEN)
dnsmasq     953    nobody   11u  IPv4 112910      0t0  UDP *:55166 
cupsd     10170      root   11u  IPv4  83360      0t0  TCP localhost:ipp (LISTEN)
cups-brow 10172      root    8u  IPv4  83378      0t0  UDP *:ipp 
firefox   14514 graigster  212u  IPv4 113804      0t0  TCP graigster-Inspiron-1545:47722->ec2-52-27-163-157.us-west-2.compute.amazonaws.com:https (ESTABLISHED)
chrome-gn 14592 graigster   59u  IPv4 108057      0t0  TCP graigster-Inspiron-1545:33022->104.25.75.19:https (CLOSE_WAIT)
chrome-gn 14592 graigster   91u  IPv4 109229      0t0  UDP localhost:39437->graigster-Inspiron-1545:domain 
chrome-gn 14592 graigster   96u  IPv4 108075      0t0  TCP graigster-Inspiron-1545:60860->ec2-54-186-218-40.us-west-2.compute.amazonaws.com:https (CLOSE_WAIT)
dhclient  14757      root    6u  IPv4 112852      0t0  UDP *:bootpc 
graigster@graigster-Inspiron-1545:~$ 

```
..please help because ive  been having a lot of trouble with my computers ,phone and tablet and I think its because our home service is being attacked

---

### Post by Irihapeti on 2017-10-20
Post moved to its own thread. 

Please start a new thread of your own - that way, the other posters and their helpers are less likely to get confused. Thanks.

---

### Post by &amp;KyT$0P# on 2017-10-21
In a nutshell, [FONT=Courier New]dhclient[/FONT] automatically obtains an IP address and network information so that your computer can connect to a network.  It is a normal component of Ubuntu.

---


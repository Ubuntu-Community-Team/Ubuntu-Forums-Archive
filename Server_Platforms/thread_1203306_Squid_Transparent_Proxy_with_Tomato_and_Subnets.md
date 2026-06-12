---
title: "Squid Transparent Proxy with Tomato and Subnets"
date: 2009-07-03
forum: Server Platforms
---

### Post by semonski on 2009-07-03
HI,

First off, I want to thank anybody for any input they can give me.  I've been fooling with this problem for days, reading lots of articles, guides, and other information, but I've not been able to crack the code on this one.  Additionally, there is no practical reason for this configuration except for me to learn how to implement various environments.

I have a network diagram below where there are two subnets that cascade together for access to the internet through one DSL modem.

I've setup a Squid Proxy server on Subnet 2 that I want ALL machines on both subnets to use for HTTP (port 80) access.

With the below IPTABLES configuration, I've been successful with getting the machines on SUBNET 1 to use the proxy and function with the Proxy Server.

However, I can not get the workstation on SUBNET 2 to function with the Proxy Server.



IPTABLES


iptables -t nat -A PREROUTING -i br0 -s ! 192.168.2.12 -p tcp --dport 80 -j DNAT --to 192.168.2.12:3128

iptables -t nat -A POSTROUTING -o br0 -s 192.168.1.0 -d 192.168.2.12 -j SNAT --to 192.168.1.1




If I add the following line 

iptables -t nat -A PREROUTING -i br0 -s 192.168.2.50 -p tcp  --dport 80 -j ACCEPT

to the IPTABLES configuration on the router, the workstation will bypass the proxy, but I would like them to use the proxy.

Any assistance would be greatly apperciated.


TIA,

Kos



[IMG]http://semonski.dyndns.org/ext_longterm/net.jpg[/IMG]

---

### Post by AlexanderDGreat on 2010-12-22
Hey man, have you found a solution to your problem? I want to redirect all http requests to my Tomato router to my Squid Proxy server, but it's not working for me!

Can anyone please help?

---

### Post by AlexanderDGreat on 2010-12-23
Hey man, here's my basic Tomato Firewall script, it works for me right now, I'm planning to improve it soon:

192.168.0.50 - Squid Proxy Server
192.168.0.0/24 - local network

```

**#!/bin/sh**

iptables -t nat -A PREROUTING -s ! 192.168.0.50 -p tcp --dport 80 -j DNAT --to 192.168.0.50:3128
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -d squid-box -j SNAT --to 192.168.0.0/24
iptables -A FORWARD -s 192.168.0.0/24 -d squid-box -p tcp --dport 3128 -j ACCEPT

#exceptions, setup STATIC IP's first

iptables -t nat -I PREROUTING -s 192.168.0.5 -j ACCEPT

```

I hope you get some idea from this.

More info on this: [http://tldp.org/HOWTO/TransparentProxy-6.html#ss6.1]("http://tldp.org/HOWTO/TransparentProxy-6.html#ss6.1")

---


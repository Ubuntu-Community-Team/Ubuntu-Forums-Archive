---
title: "VPN related question"
date: 2011-06-06
forum: Server Platforms
---

### Post by adriankoooo on 2011-06-06
Hi all,
I am going to connect to a VPN service provider. From VPN I'll get a public ip. When I simple connect to this pptp VPN, all ingoing-outgoing traffic will be forwarded to the VPN. Am I right? However what if I'd like to send traffic only on specific ports through the vpn, so for example p2p traffic, etc. I want to access that port from the VPN's public ip after that.  It is possible to configure a vpn client this way? Sorry if this is a stupid question i'm pretty new to this.

Thanks,
Adrian

---

### Post by lfacchinelli on 2011-06-06
> **adriankoooo said:**
> Hi all,
I am going to connect to a VPN service provider. From VPN I'll get a public ip. When I simple connect to this pptp VPN, all ingoing-outgoing traffic will be forwarded to the VPN. Am I right? 

50-50.
All ingoing and outgoing traffil will be forwaded if you config your network connection to do that.

> **adriankoooo said:**
> 
However what if I'd like to send traffic only on specific ports through the vpn, so for example p2p traffic, etc. I want to access that port from the VPN's public ip after that.  It is possible to configure a vpn client this way? Sorry if this is a stupid question i'm pretty new to this.
Adrian
You can do that using iptables, and routing your request to your VPN's server or 'local connection'

---

### Post by adriankoooo on 2011-06-07
Super, thanks for the answer!

Can you help me with an example to iptables? If I connect to a vpn server I think there will be an virtual interface? So, how to redirect port, for example 13000 to that virtual vpn interface and all other traffic to eth0. :-k

I think I need something like this?

When I connect to the VPN, then default routing goes through ppp1. Somehow I need to change it back to eth0? Then set ppp1's public ip to eth0? Then I can connect back to my machine via ppp1's IP and because I changed back eth0 routing after VPN connect, then the traffic goes as normal (like before connecting to the VPN). Am I thinking right?

---

### Post by adriankoooo on 2011-06-07
Using interface ppp0
Connect: ppp0 <--> /dev/pts/4
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
found interface eth0 for proxy arp
local  IP address xx.xxx.179.125
remote IP address 192.168.1.100
primary   DNS address xx.xxx.96.15
secondary DNS address xx.xxx.96.16

Ok I get a public ip xx.xxx.179.125, but I can't access my machine with this IP from the internet. Why?

adriankoooo@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask                 Flags Metric Ref    Use Iface
192.168.1.100   *                         255.255.255.255 UH    0        0        0 ppp0
10.1.0.1             192.168.1.1     255.255.255.255 UGH 0        0        0 eth0
xx.xxx.191.220   192.168.1.1     255.255.255.255 UGH 0        0        0 eth0 ///my normal public IP
192.168.1.0       *                       255.255.255.0     U      0        0        0 eth0
default               192.168.1.1     0.0.0.0                 UG    100    0        0 eth0

---

### Post by Asma Ul Husna on 2011-11-28
Hello Adrian,
There are many scams on the internet, finding real VPN services is not a easy task. So, my best advice to you, that is find real VPN service. I am giving a link bellow, where you can get the best and real VPN services. You may visit here: 
[[FONT=&quot]best [/FONT][FONT=&quot]uk[/FONT][FONT=&quot] VPN[/FONT]]("http://www.bestvpn.co.uk/best-uk-vpn/")

---


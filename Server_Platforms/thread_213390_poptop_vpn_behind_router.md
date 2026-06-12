---
title: "poptop vpn behind router"
date: 2006-07-11
forum: Server Platforms
---

### Post by vaalaskala on 2006-07-11
Hi,

I managed to get poptop pptpd working and I can connect via winXP vpn to my linux box (dapper). The problem is that I cant use the internet connection via vpn.

The goal that I'm trying to achive is to get VPN up and ready so others can connect to my linux box and get the static gateway that I have and with doing so they could connect to servers that only allowed to my public ip. so far I can only connect and use local resources but not the internet connection. I can ping the router but not connect to it.

so basically its like this from inside LAN

my XP >>vpn>> my Linux >> router >> inernet

and from outside it would look like

others XP >>throughroutervpn >> my linux >> router >> internet

my pptpd.conf

logwtmp
bcrelay eth1
localip 192.168.1.32
remoteip 192.168.1.1

and pptpd-options

name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
ms-dns 192.168.0.1
ms-dns 194.126.97.30
proxyarp
nodefaultroute
lock


any suggestions?

---


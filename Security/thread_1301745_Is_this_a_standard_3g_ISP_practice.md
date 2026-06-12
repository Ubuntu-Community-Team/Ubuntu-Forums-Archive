---
title: "Is this a standard 3g ISP practice?"
date: 2009-10-26
forum: Security
---

### Post by piankhi on 2009-10-26
My first post so go easy on this noob please ;-)

A couple of weeks ago i decided to install Kubuntu 9.10 beta after hearing a friend raving about it. I must say i was really impressed how far Ubuntu & KDE have come since the "dapper" days. I've been using it for two weeks straight on my desktop and haven't booted into windows once. I have a couple of security related issues though.


**Issue 1:**

I'm using a ZTE 3g usb modem (unlimited data plan) to access the internet by dialing my ISP using KPPP. The ISP has me behind a NAT and assigns me a private IP addresses in the 10.13.x.x range that connects to a gateway with a private address in the 192.168.x.x range. Obviously i can't get any incoming connections because of this setup i.e all incoming ports are blocked. Doing a port scan on myself from a site like [http://www.grc.com/x/ne.dll?bh0bkyd2](http://www.grc.com/x/ne.dll?bh0bkyd2) scans my public ip address - which im probably sharing with a number of other users - and reports that all ports are "stealth". So here's my question. Is there anyway to get around this restriction, so that I'm able to seed torrents normally for example?

**Issue 2:**

I finally got around to reading about and configuring iptables today (should of done it a long time ago i know) :oops:. I have my local network setup as follows:

3g usb modem attached to Kubuntu box (ppp0) >> Wireless Router (DHCP + DNS server) attached to Kubuntu box through eth0 >> Various windows laptops connected to the wireless router.

So to accommodate the setup i have, my iptables rules are as follows:

```

#!/bin/bash

#SET DEFAULT POLICY
iptables -P INPUT DROP 
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD DROP

# Log & Drop chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : ' --log-level 4
iptables -A LOG_DROP -j DROP

#ALLOW LOOPBACK ACCESS
iptables -A INPUT -i lo -j ACCEPT 
iptables -A OUTPUT -o lo -j ACCEPT

#Allow ESTABLISHED and RELATED incoming connection
iptables -A INPUT -i ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT

#Allow all incoming LAN traffic
iptables -A INPUT -i eth0 -s 192.168.0.0/24 -j ACCEPT

# Masquerade out ppp0
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Forward all Outgoing connections from the LAN 
iptables -A FORWARD -i eth0 -o ppp0 -j ACCEPT

# Forward only established and related connections to the LAN 
iptables -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 

# Drop & log all other packets
iptables -A INPUT -j LOG_DROP
iptables -A FORWARD -j LOG_DROP

```After getting iptables configured as above i started seeing various entries like the following in the syslog:

```

 [IPTABLES DROP] : IN=ppp0 OUT= MAC= SRC=10.13.140.200 DST=10.13.148.39 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=47560 DF PROTO=TCP SPT=9699 DPT=445 WINDOW=16384 RES=0x00 SYN URGP=0

```My guess here is that the windows laptops behind my wireless router are sending out netbios broadcast packets that make their way out through ppp0. Is that why I'm seeing packets such as the above? This is a stupid question but here goes: In the packet above, are the source and destination ip addresses considered on the same subnet given a netmask of 255.255.255.255 ? If not, how-come the two can communicate with each other? Are they doing it through the 192.168.x.x gateway? Finally is my iptables setup secure/correct given my network environment?

BTW when i opened dolphin and pointed it to the source IP in the packet above i got a username and password prompt. Is it standard 3G ISP practice to allow subscribers to access each others shares so easily? 


Finally (really finally this time :) ) sorry for the long post and I'd really appreciate the input of any of you security gurus out there 


THANKS!

---

### Post by scorp123 on 2009-10-27
> **piankhi said:**
> **Issue 1:**

I'm using a ZTE 3g usb modem (unlimited data plan) to access the internet by dialing my ISP using KPPP. The ISP has me behind a NAT and assigns me a private IP addresses in the 10.13.x.x range that connects to a gateway with a private address in the 192.168.x.x range. Obviously i can't get any incoming connections because of this setup i.e all incoming ports are blocked. So here's my question. Is there anyway to get around this restriction, so that I'm able to seed torrents normally for example? Nope. This is normal. As far as I can tell all providers do this in order to protect their customers. And as a "positive side effect" (for them only) it also prevents most IM and VOIP clients from functioning, e.g. you probably won't be able to use Skype while you're connected via your 3G modem.

---

### Post by niteshifter on 2009-10-28
Hi,

Regarding issue #1:

It may or may not be normal. I'll use my 3G provider (AT&T) as an example:

If I give this command to the modem / cell phone:
```
AT+CGDCONT=1,"IP","wap.cingular"
```
Then I get IP addresses like yours - 10.x.x.x and I'm invisible to outside world.
If instead I use:
```
AT+CGDCONT=1,"IP","isp.cingular"
```
Then I get an IP address like 166.x.x.x - public and accessible.

What's changing in the above is the APN (Access Point Name) parameter. Which APN to use depends upon wireless (cell) provider and the type of data plan you have. By type I mean not just bandwidth privilege - but the class of access: handheld device (WAP) or computer / laptop (ISP).

You should get with your service provider and check the details of your account - some plans offer just WAP access, some offer both.

---


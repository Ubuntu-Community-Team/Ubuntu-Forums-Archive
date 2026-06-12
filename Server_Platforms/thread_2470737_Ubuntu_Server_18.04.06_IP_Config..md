---
title: "Ubuntu Server 18.04.06 IP Config."
date: 2022-01-09
forum: Server Platforms
---

### Post by baygold on 2022-01-09
Hello, I installed ubuntu server on my computer using Vmware for OpenVpn. The server is assigned an ip address of 192.168.172.65 (example). Internet ip address of my host computer 45.87.116.58 (example).


I want 192.168.172.65 (server) address to be used for internet operations of the computer I connect to. 

But the address 45.87.116.58(host) is used. 

When I rent a server from hosting companies and install openvpn on these servers, the ip address that I connect to the server can be used on other computers after the vpn connection.

 what can't i do?

---

### Post by TheFu on 2022-01-09
Reserved IPs mean nothing and aren't used on the internet.  Only the public IP is.  I know of no way to have a private IP address used over the internet. It is a routing thing.  TCP requires correct source and destination IPs for the protocol handshake to work.

---

### Post by baygold on 2022-01-09
> **TheFu said:**
> Reserved IPs mean nothing and aren't used on the internet.  Only the public IP is.  I know of no way to have a private IP address used over the internet. It is a routing thing.  TCP requires correct source and destination IPs for the protocol handshake to work.

How do hosting companies do this?

---

### Post by TheFu on 2022-01-09
They use public IPs.

---

### Post by baygold on 2022-01-09
> **TheFu said:**
> They use public IPs.

Thank you so much TheFu. But i confused. For example, a hosting company has 1500 VPS. Does this company have 1500 different public ip's? How is this possible? Can I buy 10 public IPs for a modem and assign them to my servers?

---

### Post by TheFu on 2022-01-09
> **baygold said:**
> Thank you so much TheFu. But i confused. For example, a hosting company has 1500 VPS. Does this company have 1500 different public ip's? How is this possible? Can I buy 10 public IPs for a modem and assign them to my servers?

Hosting companies order public IPs from the regional IP control organization in blocks of whatever size they want. In some parts of the world, there aren't any left, so those places (China/India) push IPv6.   In the US, my ISP has 69.252.0.0/17 for one of their blocks. That's 32766 IP addresses.  They have multiple blocks.  The block I'm on is a /29 and the block at the ISP has for that is a /19 ... 8190 IPs in a /19.

Whether you can get public IPs at your location is something to discuss with the ISP.  I have 5 public IPs, but pay about 3x more for internet than most people for 10x slower speeds.

If you use IPv6, you might be able to what you want easier, but you'd want to disable IPv4 so that data doesn't leak and you get traced. Many internet services support IPv6 and many do not.  None of my services support IPv6. That's because I don't feel qualified to secure IPv6 stuff and have learned just enough to disable it on every device I can and to block all uses of it from ingress/exfill out my network.

---

### Post by baygold on 2022-01-09
> **TheFu said:**
> Hosting companies order public IPs from the regional IP control organization in blocks of whatever size they want. In some parts of the world, there aren't any left, so those places (China/India) push IPv6.   In the US, my ISP has 69.252.0.0/17 for one of their blocks. That's 32766 IP addresses.  They have multiple blocks.  The block I'm on is a /29 and the block at the ISP has for that is a /19 ... 8190 IPs in a /19.

Whether you can get public IPs at your location is something to discuss with the ISP.  I have 5 public IPs, but pay about 3x more for internet than most people for 10x slower speeds.

If you use IPv6, you might be able to what you want easier, but you'd want to disable IPv4 so that data doesn't leak and you get traced. Many internet services support IPv6 and many do not.  None of my services support IPv6. That's because I don't feel qualified to secure IPv6 stuff and have learned just enough to disable it on every device I can and to block all uses of it from ingress/exfill out my network.


thank you so much... Last question, can i use multiple public ips on a single modem? Do I need to replace my regular user modem?

---

### Post by TheFu on 2022-01-09
You don't get the pick the IP address for your modem. That comes from the ISP.  Whether any modem can support multiple IPs or not is a question about the modem software and the ISP configuration of that software. It is common for a single port on a normal Linux system to support 1, 10, 500, different IP addresses. The limit isn't with Linux.

---

### Post by baygold on 2022-01-10
> **TheFu said:**
> You don't get the pick the IP address for your modem. That comes from the ISP.  Whether any modem can support multiple IPs or not is a question about the modem software and the ISP configuration of that software. It is common for a single port on a normal Linux system to support 1, 10, 500, different IP addresses. The limit isn't with Linux.

TheFu... you have been very helpful thank you!

---

### Post by LHammonds on 2022-01-12
IPv4 and IPv6 are fairly different in how they work.  Most everyone is familiar with IPv4 (with private,non-routable and public IP networks) but they are nearly maxed out on available IP addresses that can be issued.

IPv6 does not have the amount limitation that IPv4 has but they are logically handled in a different manner.  IPv6 IP that is assigned to your device is actually the IP that is addressable on the Internet and the IPv6 modem just acts like a pass-thru device rather than a NAT firewall / bridge.  Even though IPv6 has been around for quite some time now, it still has issues and I prefer IPv4 over IPv6 if I have a choice but depending on where you are, IPv6 may be the only option.

LHammonds

---


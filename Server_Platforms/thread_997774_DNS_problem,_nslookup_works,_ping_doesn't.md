---
title: "DNS problem, nslookup works, ping doesn't"
date: 2008-11-30
forum: Server Platforms
---

### Post by Roaders on 2008-11-30
I apologise if this is not an ubuntu problem - it could well be a windows problem but I'm not sure.

I am setting up an ubuntu development server in my flat. I have set up a dns server on it and have added the zone weddinglist.

The main IP for the box is 192.168.0.40, I want to set weddinglist up on 192.168.0.41

On all my Pcs (vista and xp) I get the following from the command prompt:

C:\Users\Giles Roadnight>nslookup weddinglist
Server:  UnKnown
Address:  192.168.0.40

Name:    weddinglist
Address:  192.168.0.41


C:\Users\Giles Roadnight>ping 192.168.0.41

Pinging 192.168.0.41 with 32 bytes of data:
Reply from 192.168.0.41: bytes=32 time<1ms TTL=64
Reply from 192.168.0.41: bytes=32 time<1ms TTL=64
Reply from 192.168.0.41: bytes=32 time<1ms TTL=64
Reply from 192.168.0.41: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.0.41:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\Users\Giles Roadnight>ping weddinglist
Ping request could not find host weddinglist. Please check the name and try agai
n.

My ipconfig:

C:\Users\Giles Roadnight>ipconfig -all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Giles-Desktop
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No


Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Marvell Yukon 88E8001/8003/8010 PCI Gigab
it Ethernet Controller
   Physical Address. . . . . . . . . : **-**-**-**-**-**
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::f179:680f:f313:5448%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.5(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1
   DNS Servers . . . . . . . . . . . : 192.168.0.40
   NetBIOS over Tcpip. . . . . . . . : Enabled

I am pretty sure that I have the dns set up ok as the nslookup is ok but I can't ping and I can't acces webpages at weddinglist.

Any help much appreciated.

---

### Post by RealPSL on 2008-11-30
Have you tried pinging the fully qualified domain name of the host in question?

---


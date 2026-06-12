---
title: "Server removing internet?"
date: 2012-05-13
forum: Server Platforms
---

### Post by JasonMarquez on 2012-05-13
When I have my Ubuntu 10.04 (Running on IBM xSeries 346), I lose internet connection on other computers. Not sure why. It might be the router not being powerful enough. I have lots of ports open on the router for Ubuntu because it is acting as a server with Teamspeak, Minecraft, and other web services. I know this is very vague information, but anything that might lead to me fixing it would be nice.

---

### Post by Tylerjd on 2012-05-14
So you are saying whenever you connect your server to your network, it causes the other computers to loose their internet connection? That **is** odd. 

A few things come to mind though. If you manually set up the connection information for you server you might have mistyped a value, and it could be "stealing" the router's place on the network, like if both your server and router have the same IP. But then again your server would not have a connection then.

Are you running a DHCP service on your server? That could be causing it to try and hand out new IP leases to computers on the network confusing them.

---

### Post by SeijiSensei on 2012-05-15
If you gave the server a static IP address, as you should when running a server, you may have inadvertently given it an address that conflicts with the address assigned to another machine on the network.  Give the server an address in the same subnet, but outside the range of any DHCP-assigned addresses.  If your router hands out addresses in the range of, say, 192.168.0.100-150, give the server an address like 192.168.0.10.

Also as Tyler says, you need to make sure that there is only DHCP on the network.  Either use the one on your router or disable that and configure dhcpd on the Linux server.

---

### Post by darkod on 2012-05-15
> **SeijiSensei said:**
> 
Also as Tyler says, you need to make sure that there is [COLOR=Red]only DHCP[/COLOR] on the network.  Either use the one on your router or disable that and configure dhcpd on the Linux server.

Of course, Sensei meant to say only ONE dhcp server issuing addresses.

Only dhcp sounds like no static addresses are permitted.

---


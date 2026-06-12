---
title: "Squid Proxy Server"
date: 2018-03-07
forum: Server Platforms
---

### Post by carnagelan on 2018-03-07
Hi Guys,

I am familier with setting up a squid proxy server. My question is as follows. 

Client pcs are all laptops which connect wirelessly to the router. 

Currently the router isnt connected to a server at all.

I would like to setup a Ubuntu server with eth0 been the LAN and eth1 been the WAN

What device will i need to purchase so the laptops connects through this device on eth0 and the router is on eth1?
Remember the laptops are not hard wired so a normal switch wont work, 

I am going to disable the wifi on the router so they cannot connect to the router directly.

The only devices that are hard wired is the NAS drive witch will also be hard wired to a switch on eth0
I will also be setting up a OpenVPN server as they would like to VPN so they can work from home.

---

### Post by darkod on 2018-03-07
If you set up the server to route/filter the traffic between the lan and the wan, then simply disable wifi on the router and buy wifi access point. That way laptops can connect by wifi to the lan and their traffic will also be filtered by the server before it reaches the wan.

---

### Post by carnagelan on 2018-03-07
Thanks Darkhod,

Thats what i had in mind but just wanted to make sure as i have setup access point to extend the wifi range but never used it in this manner.

---


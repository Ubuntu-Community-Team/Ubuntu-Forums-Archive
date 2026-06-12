---
title: "ubuntu server install on eMMC"
date: 2019-09-03
forum: Server Platforms
---

### Post by Vasu_Muppalla on 2019-09-03
Planning to install ubuntu server on a small, fan less PC which has a 64 GB eMMC storage (no other storage possible). I plan to use it as a VPN server applicance (it will have 2 ethernet, one wired and one wireless ports).

I was wondering if, for this application, the emmc storage will have adequate performance, esp when installing and updating software. I might also install either the access manager application from openvpn.net or the web based administration interface suggested on ubuntu server documentation page.

TIA.

---

### Post by darkod on 2019-09-03
Most flash memory would be good enough. You don't need to worry too much about installing and updating.

One possible issue is if you run too much traffic through the VPN because basically it will be like gateway for all clients.

In general the eMMC should be able to handle it. But I guess you will know only when you start using it.

---

### Post by Vasu_Muppalla on 2019-09-03
> **darkod said:**
> Most flash memory would be good enough. You don't need to worry too much about installing and updating.

One possible issue is if you run too much traffic through the VPN because basically it will be like gateway for all clients.

In general the eMMC should be able to handle it. But I guess you will know only when you start using it.

It is for a private VPN server at home so there shouldn't be more than one or two sessions at a time. Also, VPN connections should not be doing disk I/O, I presume ?

---

### Post by Vasu_Muppalla on 2019-09-11
I bought a dell inspiron 11 3000 with emmc, 4 GB ram and an AMD 9420e processor with TDP 6W. No fan noise, perfect for a server appliance and has display built-in. It doesn't have RJ45 but a USB ethernet adapter fixed that. 

I suspect that with USB hub and usb ethernet adapters hanging off them, you can run a router on this thing but I haven't tried that !

With the inbuilt WLAN link and the USB RJ45 link, I turned this into a VPN appliance/server with the wifi as the WAN port on the netgear R7960's LAN (and https port forwarding). It is perfect for the job. It is running openvpn's access manager on ubuntu server 18.04.

There is another router that splits the netgear's LAN side into multiple subnets and the vpn grants access to one of the subnets.

---


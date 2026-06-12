---
title: "Please help with network config to make a web server  ?"
date: 2007-11-27
forum: Server Platforms
---

### Post by infantiablue on 2007-11-27
Hi every body,

I have 2 machine:
1 is my desktop: Window XP + XAMP installed + Wireless Network Adapter 
1 is my server: Ubuntu Server Edition 7.10 +[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10) installed + NIC
For my internet line, 
I have a router and a wireless access point with 4 ports, so I use one of 4 port to connect to the server, and my desktop still connect to through wireless signal.

The problem is that, when I turn network on for my desktop, the router seems not to forward port 80 to my server. When I turn off my desktop, and I use canyouseeme.org service to check, it could see port 80 on my server.

Please help me how to configure my network in this situation. Both of router and access point are D-Link

Thank you very much for your any help !

---

### Post by crouton on 2007-11-27
It sounds like your router/wireless AP is one device.  Change your Ubuntu server to be a static IP address, login to your router, and force port 80 to forward to the server's IP.

---

### Post by infantiablue on 2007-11-28
Hi, thank you for your support. However, I tried to set up DHCP and release static IP for all machines in my network, but the problem is still there.

---

### Post by crouton on 2007-11-29
Although this sounds to be a network problem rather than an Ubuntu problem, let's walk through this step by step.

1) Is your router/wireless AP one device or two separate devices?

2) Is your router providing DHCP and performing port forwarding?

3) When you turn on your desktop's wireless, how are you aware that port 80 is no longer forwarding to your server?

---


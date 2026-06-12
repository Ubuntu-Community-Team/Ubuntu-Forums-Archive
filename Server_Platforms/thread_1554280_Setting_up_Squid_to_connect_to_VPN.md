---
title: "Setting up Squid to connect to VPN"
date: 2010-08-16
forum: Server Platforms
---

### Post by Melpomene on 2010-08-16
Hello, 

I'm trying to set up a VPN connection such that it is possible to choose which of my programs that should use it for internet access.  ( Like a proxy ) 

So I have set up webmin and installed a Squid proxy server. My idea is that I will connect to the vpn with webmin and get a proxy that I can use on localhost that will redirect me to the Network Interface created when I connect to the VPN and the programs which I don't want to forward through the VPN I will simple leave be and they will connect to the internet directly through my usual router.

I've managed to set up webmin and the squid server. Succesfully connected to the VPN with the "PPTP VPN Client" which have created an network interface named ppp0. What I haven't managed though is to set ut what network interface my squid proxy should use to connect to the internet.
Does anyone have any idea how this is done? Or have a better alternative solution for my project to select whether a program should use the VPN or not? 

//

Melpomene

---


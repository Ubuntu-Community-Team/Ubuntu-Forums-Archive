---
title: "Multi-NIC - Multi-LAN setup?"
date: 2013-01-28
forum: Server Platforms
---

### Post by Cjack1975 on 2013-01-28
Hi,

I have 3 Pentium-4 machines, a bunch of 10/100 NICs, and a couple of b/g wifi routers laying around, and planning on organizing them into some kind of 3-tier network 

1) graphical-terminal 'everyday use' (Kubuntu, Mint-KDE, Netrunner?)
2) application-server (SSH-Xforward) (Ubu Server 12.04.1 LTS)
3) file-serve (exporting /home and /usr/remote) (also Ubuntu Server)

for segmenting the network traffic, it makes sense to use 2 separate NICs on machine 2 (one for 1-2, and one for 2-3) especially if planning to integrate more remote terminals in the (1-2) link.

What difficulties can I expect in configuring the NICs mhen installing Ubu Server on Machine 2? (it seems multiple-NIC questions are quite popular!)

Maybe there's a resource that might help me further think through my planning?

---


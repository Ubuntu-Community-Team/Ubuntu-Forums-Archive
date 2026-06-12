---
title: "Running vmware appliances on Ubuntu workstation"
date: 2007-11-23
forum: Virtualisation
---

### Post by JavaMain on 2007-11-23
Hi
OK here's my plan...
I am aiming to create an Ubuntu server bristling with 3 vmware appliances. 
One a VPN firewall, one a mail server with webmail like Port25, one a proxy like Dan's Guardian.

I have two NICs maybe I need three.

I have installed Ubuntu and VMware Player so far. But having given eth0 a local subnet IP and eth1 the public one, I don't know how to proceed further. 

Anyone any experience with this who could enlighten? 

Many TIA
Andy

---

### Post by mellowd on 2007-11-23
Why 2 cards? Are you planning on using the server as a router as well?

---

### Post by JavaMain on 2007-11-23
Thanks for the Q. mellowd

Yes I want the "server" to be isolated from the internet, but the appliances will a) route to the local subnet b) send receive and store mail available to internet webmail users and local clients and c) act as local gateway for internet access to clients.

---

### Post by mellowd on 2007-11-23
I see a slight problem with this though. You want to isolate the server from the internet at the same time that the server will be a gateway for internet access to other clients.

For better isolation I would think a router with a DMZ or some sort of firewall. that way your clients can have access and your server could also have access, but in a more protected way

---


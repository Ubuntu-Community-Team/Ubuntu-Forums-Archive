---
title: "2 nic's &amp; 2 firewalls?"
date: 2007-06-25
forum: Server Platforms
---

### Post by Aberrix on 2007-06-25
I've got a server with 2 networks cards, one is a 10/100 which handles all the ssh/ftp/web traffic and is generally the dmz. the second network card is a 10/100/1000 which I like to use as the private side and wish to run my samba over and anything else I do not wish to be in the dmz.

my problem is I use ISPConfig, but when I use the firewall it affects both nic globally.

So my question is this, I would like a tool to use to be able to setup a firewall and idependently change the two nic's. I know there is iptables but I'd like something a little easier to use from the CLI, like a command line gui (if that makes sense). even a command line gui for iptables is fine.

thanks in advance for you suggestions and advice.

---

### Post by Mr. C. on 2007-06-25
It defeats the purpose of a DMZ to have one interface in the DMZ and one on the LAN.  The whole point of a DMZ is to physically isolate the server that is WAN-facing, yet provide a firewall shielding its services in general.

I'm sorry, I don't know anything about ISPconfig, nor have an easier solution for you than iptables.  With iptables, you need to setup the proper FORWARDING chain, or at the routing-level all tcp_forwarding and setup a route.

MrC

---

### Post by Aberrix on 2007-06-26
> **Mr. C. said:**
> It defeats the purpose of a DMZ to have one interface in the DMZ and one on the LAN.  The whole point of a DMZ is to physically isolate the server that is WAN-facing, yet provide a firewall shielding its services in general.

okay, maybe my wordage was incorrect. regardless I want to have one nic on the wan and one on the lan. I'd like to simply make sure my samba shares are not accessible from the outside and any other ports/services I wish to run on the lan.

are there any 'command line gui' firewalls that anyone can recommend?

I really just want to be able to go "port 21, 80, 443 on this nic open, all else closed. port XX, XXX and XXXX open on this nic, all else closed."

---


---
title: "Server/network configuration with one fixed IP address and VPN"
date: 2008-11-02
forum: Server Platforms
---

### Post by jrdecastro on 2008-11-02
Hi there -new to setting up a full server and remote VPN and need some basic guidance.
The current networks is basically internet -> broadband and wireless router -> switch -> various dektop client machines.
The current Internet connection has a floating IP address which changes every time we reconnect. Internal subnet addresses (192.168.1.x) are static for all nodes except wireless clients which are assigned through DHCP on an address range specified at the wireless router.
I am now geting a single fixed IP address and adding a server to:
- handle file serving to the clients,
- add our own email address and mail access system, and
- create a VPN to a different remote site where we will access the network from and where we will store backups and update them periodically with something bandwith-economical like rsync.
The questions I have are about basic topology - who owns the new fixed IP and how do I ensure data gets to the right place.
Can I keep the existing topology and add the server hanging off the switch together with the clients thus:
A) Internet -> broadband and wireless router -> switch -> server and various dektop client machines (all in parallell out of the switch)
or do I need to have the server (which has two Ethernet interfaces so this is possible) become the interface between the outside world and the network thus:
B) internet -> broadband and wireless router -> server -> switch -> various dektop client machines
or even
C) internet -> server -> broadband and wireless router -> switch -> various dektop client machines (since the wireless clients should also be on the local network...)
If the answer needs to be something like B), how do I set it up and how do I tell the broadband / wireless router that the fixed IP belongs to the server, mail is handled by the server, and all traffic regarding the VPN goes into the server? How do I then get the server to distribute it all correctly to the other clients in the network, including the VPN traffic? Normally I suspect that if the new fixed IP address is a.b.c.d, that address will not make it past the wireless router which will name the server something like 192.168.1.x - how does the overall system then know to send mail to a.b.c.d and its domain name to the server and not the clients for handling? Does the wireless and broadband router need to be configured to do this (and if so, is it just port forwarding (which ports) or something more subtle?)
Similarly, if the answer needs to be something like C), is the server safe enough to expose directly to the Internet like that? (and also all the questions above about how to get it to send all incoming stuff to the right machines)
For VPN, if, say the local subnet is 192.168.1.x, should I make the local subnet at the other end a different number like 192.168.2.x, and if so, should I change the mask from 255.255.255.0 to 255.255.0.0 on both sides so they can see each other, or will the VPN trickery handle that transparently?
Look forward to hearing back - you guys are great!
James

---

### Post by Iowan on 2008-11-03
Just my opinion...
Unless you specifically need the server to have "outside" address, give the router the static address, and configure it to port forward to the new server (it should be capable). This would be like your "A" configuration, which would seem to be pretty painless.  The new server could be given a static lease (depending on router capabilities).  
So far, I haven't done VPN, so I don't know what sort of problems going through the router might cause - *probably* just another port forward.
I haven't set up a mail server, either.  Hopefully, I haven't proposed a solution 180 degrees from logical - but it should at least give your thread a bump.

---

### Post by jrdecastro on 2008-11-05
Thank you very much. If it were not for the VPN I think what you propose makes the most sense - my main unknown is how the VPN would be handled and whether it would need to go through the server with the erver as gatekeeper

---


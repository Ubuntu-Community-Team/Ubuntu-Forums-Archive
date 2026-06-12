---
title: "Linux Terminal Server"
date: 2007-09-17
forum: Server Platforms
---

### Post by freeky on 2007-09-17
I have installed LTSP on Ubuntu 5.10 server. Is it necessary for me to install DHCP servicve on Terminal Server for clients to boot from. Also my server has two NIC cards . Is it possible to Install DHCP server in such a scenario. 

Regards
Freeky

---

### Post by koenn on 2007-09-17
You need a dhcp server (or bootp, but forget i mentioned that) for LTSP to work, but it doesn't have to be on the same machine as our "Terminal Server".  DHCP is needed to give your thin clients an ip address AND tell them where to  get their boot files, so you do need it. 
see eg [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)


Having a machine with 2 NICs is no problem. If you want, you can configure the dhcpd to only listen/hand out leases on 1 interface

---

### Post by freeky on 2007-09-18
Thanks koenn. Will try it out..cheers

---

### Post by freeky on 2007-09-19
Is it a bad thing if i set up  my DHCP to assign IPs in a range dynamically..BOOTP

---

### Post by koenn on 2007-09-19
for your thin clients, it doesn't realy matter what address the have, as long as they have one (within reason, eg. on the same network as your servers, unless you want to make tyhings complicated). So you just let dhcp hand them out randomly. That's what it's made for. 

Your server(s) need static (fixed) addresses because you need to pass that address to the clients so that they know where to get their boot files. 
You can do this by setting a static address, or make a dhcp reservation so the dhcp server gives the same address to that server all the time. 
If you have only one server, and that server is also doing dhcp, you have to set the address yourself, I don't think you can let a dhcp server  give an address to itself.

---

### Post by freeky on 2007-09-20
I  have installed LTSP 4.1 on UBuntu 5.10 server.The ltspcfg shows all
   services running except XDMCP which says found:none in the status. When i
   try to configure XDMCP in LTSPCFG it says it is not installed  and when i run netstat it says running GDM .I have configured gdm.congf [xdmcp] enabled= true. My DHCP Server is starting stopping fine. ..Do i have to install XDMCP  separately and if so how. also what
   When i setup cleint for LAN boot it gives error saying PXE 2.0 and "Media Test Failure" Check Cable" Exiting PXE rom

---

### Post by koenn on 2007-09-20
I don't know about XDMCP, but in any case, you have to fix that network problem first.
> When i setup cleint for LAN boot it gives error saying PXE 2.0 and "Media Test Failure" Check Cable" Exiting PXE
Apparently the network boot fails because PXE (code on your NIC that handles the network boot) can't access the network - presumably because of a bad/missing cable

---

### Post by freeky on 2007-09-21
I tried 4 working cables and its still not happening..feel somehow its related..or amybe the NIC  is not supported by LTS..hit  a roadblock now i guess..

---

### Post by koenn on 2007-09-21
1-
Is there a hub / switch between your server and the client or do you connect directly from i NIC to the other ?

2-
Have you tried plugging in to other server NIC (it has 2, right ?)

---

### Post by freeky on 2007-09-26
NO switch in between Server and cleint..i ahve connected directly..server has tqo nics bu ti have disabled one and using one of it..

---

### Post by koenn on 2007-09-26
> **freeky said:**
> .... server has tqo nics bu ti have disabled one and using one of it..
and you're sure you're using the one that is not disabled, right ?

> **freeky said:**
> NO switch in between Server and cleint..i ahve connected directly..
you may need a crossover cable. 
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by freeky on 2007-09-26
Thanks man..i will chekc it and get back..
Cheer

---

### Post by freeky on 2007-10-10
Solved. Whnen i out in the gateway and DHCP IPs from my business network it worked fine..thanks

---

### Post by koenn on 2007-10-10
Cool.

---


---
title: "Server Networking Question?"
date: 2010-03-13
forum: Server Platforms
---

### Post by cusinndzl on 2010-03-13
I have set up a server running Ubuntu Server 9.10. I have a router with 4 ports. All of those ports are taken up. I need to buy another router/hub/switch. I was planning on using one of the ports to plug in another router/hub/switch. I have port forwarding set up on the first router. 

I was wondering if the second router will show up as another IP on the network (So if the first router is 192.168.1.1 on the LAN will the second one be 192.168.10.1)? And then if I forward port 80 to the second router and then on that router forward it again to the server. 

I am pretty much trying to set up 2 routers with a server connected to the second one and I want to have the server connected to the internet with port forwarding. 

I can give you more information if needed.

---

### Post by rcayea on 2010-03-13
I apologize for not giving you a direct answer, but I thought I would direct you to a fantastic site that might help:

[www.linuxhomenetworking.com](www.linuxhomenetworking.com)

---

### Post by trundlenut on 2010-03-15
you need to buy a switch rather than a router (or see if you can use the router as a switch) and IP addresses will be handed out by the router and it doesn't matter where a machine is actually plugged in.

I have this setup at work, with one main switch with two other switches plugged into it located elsewhere in the building, IPs come from the server attached to the main switch.  This was done to provide additional network connections in two rooms.

---

### Post by tlsarles on 2010-03-15
Yeah, your going to need a switch. You can plug a router into a router, but this will create a double NAT which is highly unadvised.

To get a better understanding of how this all works, I would highly recommend this book :

[http://www.sybex.com/WileyCDA/SybexTitle/CCNA-Cisco-Ceritifed-Network-Associate-Study-Guide-Exam-640-801-Deluxe-Edition.productCd-0782143148.html](http://www.sybex.com/WileyCDA/SybexTitle/CCNA-Cisco-Ceritifed-Network-Associate-Study-Guide-Exam-640-801-Deluxe-Edition.productCd-0782143148.html)

---

### Post by spynappels on 2010-03-15
Just a basic FYI:

A router is required to talk to computers on a different subnet. In a small network of less than 250ish computers, this is only required if you want to talk to computers on other networks, like the Internet.

Switches and hubs do broadly similar jobs, but the switch is much more sophisticated at it. 

A hub will take a piece of information it receives on one port and send it out of all the other ports. This can cause problems if you have a lot of computers on the network, all shouting on all the ports they are connected to.

A switch will have a record of the port that a certain host is connected to, and will only repeat the piece of information it receives on one port to the port that the destination computer is on. This means less packet collisions and better throughput.

So to echo in a very roundabout way what the others have said, get a switch, preferably a Gigabit switch to ensure it will do what you need it to on into the future. And get as many ports as you can afford too.

---

### Post by KB1JWQ on 2010-03-15
> **tlsarles said:**
> Yeah, your going to need a switch. You can plug a router into a router, but this will create a double NAT which is highly unadvised.

To get a better understanding of how this all works, I would highly recommend this book :

[http://www.sybex.com/WileyCDA/SybexTitle/CCNA-Cisco-Ceritifed-Network-Associate-Study-Guide-Exam-640-801-Deluxe-Edition.productCd-0782143148.html](http://www.sybex.com/WileyCDA/SybexTitle/CCNA-Cisco-Ceritifed-Network-Associate-Study-Guide-Exam-640-801-Deluxe-Edition.productCd-0782143148.html)

Eh, double NAT isn't the issue it once was.  It should be fine.

Could solve the issue entirely by getting a second router (since that seems to be what he's got his heart set on) and throwing it into AP mode.

---

### Post by brian mcgee on 2010-03-15
An unmanaged switch is the simplest approach. Just plug it into the router, and it's like having a bunch of new ports. Why make it more complicated than it needs to be?

---

### Post by Iowan on 2010-03-16
+1 switch. There's a limit to how many you can daisy-chain... but it's more than 2.

---


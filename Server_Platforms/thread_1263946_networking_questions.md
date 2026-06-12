---
title: "networking questions"
date: 2009-09-11
forum: Server Platforms
---

### Post by ajy0852 on 2009-09-11
I'm designing and building a website for a local company. They have two locations, several miles apart and they've asked me to work on their network as well. I'm happy to help them out, but I don't really have experience with setting up a network. Here's what's going on:

> We currently have a peer-to-peer network.  DSL internet connection comes in to a router, which connects to a switch connecting to Location 1's networked computers.  It also connects to a router that is connected to a T-1 line, then a router at Location 2.  That router is connected to a switch and a patch panel for computers in that building, and a converter for the fiber optic line between the buildings.  At the other end of the fiber optic line is another converter, connected to a patch panel that connects to all computers in that building.

What we would like to have, we think, is a server-client network.  Actually, two, with Linux servers in both locations, connected to each other.

It may help you to know our goal - we would like to have a network that "shows" all computers in all buildings.  At this time we have two different networks talking to each other, but each location only shows the computers in that location.  Sort of.  The computers in Location 2, regardless of which building they are in, can see each other.  But between the two locations you have to know the ip address of the computer at the other location if you want to connect to it.

I'm pretty comfortable with Linux but as I say, I'm new to the server/network side of things. Does anyone have advice for me? Thanks in advance.

---

### Post by Firestem4 on 2009-09-11
The best solution to accomplish this is to create a VLAN between both sites. Depending on their setup, you can accomplish this with Linux routers or if their current routers supports it you can reconfigure them. 

For the sake of cautionary advice be sure you know what you're doing before you attempt to modify their network.Network Engineering is a very complex task and if you don't feel up to do make them aware of it. It is my opinion that its better to not be able to do something rather than attempt it and make a big mess.

 The best thing you can do is practice this yourself with your own computers; take one over to a friends house who's willing to let you hijack their internet for a little bit and attempt to create a VLAN across the internet.

Good luck.

---

### Post by ajy0852 on 2009-09-11
> **Firestem4 said:**
> The best solution to accomplish this is to create a VLAN between both sites. Depending on their setup, you can accomplish this with Linux routers or if their current routers supports it you can reconfigure them. 

For the sake of cautionary advice be sure you know what you're doing before you attempt to modify their network.Network Engineering is a very complex task and if you don't feel up to do make them aware of it. It is my opinion that its better to not be able to do something rather than attempt it and make a big mess.

 The best thing you can do is practice this yourself with your own computers; take one over to a friends house who's willing to let you hijack their internet for a little bit. 

Good luck.

Thanks. Trust me, I'm going to be very cautious.

---

### Post by Brunellus on 2009-09-11
Thread moved to a more suitable support forum. Good luck.

---


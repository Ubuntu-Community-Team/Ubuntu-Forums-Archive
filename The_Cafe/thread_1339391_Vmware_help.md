---
title: "Vmware help"
date: 2009-11-27
forum: The Cafe
---

### Post by aktiwers on 2009-11-27
I didn't know where to post this (as Im doing it on windows machines at work :()

But I have a setup I would like to create using vmware but can't get my head around it.

I have 2 PC's.

Lets call one Laptop and the other server.
I also have 2 internet connections.

I have made a small drawing of this(sorry about its MSpaint uglyness, had nothing else at hand)
[IMG]http://img204.imageshack.us/img204/4690/net1.png[/IMG]


On the server I have created 2 virtual networkcards, bridged, and applied one physical network card to each. 

On the laptop I applied the networkcard1 to the virtual networkcard, since the other physical card is used for another internet connection.

Now I want install an app on the Virtual machine located on the Laptop(1.1.1.8 ), and that app needs to connect to a database located on the virtualmachine on the server (1.1.1.3).  Though that virtual machine also runs another application, that needs to use the 192.168.1.9 virtual card. 

It's pretty important that the laptop should not be able to connect to the server, when the servers Network card 2 is disabled.

This is not the case in my setup above. If I disconnect the networkcard2, vmware simply directs the 1.1.1.10 virtual card to use the physical 192.168.1.2 card, instead of just leaving it disconnected.

So I'm thinking somethings wrong with my setup? Is brigde not the best way to go here?
Or is it just a small setting I'm missing?

All help and inputs would be very appreciated!

---

### Post by HermanAB on 2009-11-27
Hmm, look at the routing table.  The default route is likely what is causing things to work regardless.

---

### Post by aktiwers on 2009-11-27
> **HermanAB said:**
> Hmm, look at the routing table.  The default route is likely what is causing things to work regardless.

Thanks for the reply! :)

When I on the server in "Host virtuak Network Mapping" has applied one virtual card 1 to one physical card1, and virtual card2 to physical card2, shouldn't this be enough?

I don't seam to be able to find where I can change the defualt route?
Im pretty sure you are right about the route, since it seams to route through network card 1 all the time, even though I have mapped the virtual card2 to the physical card2.

Hmm.. this is confusing me - would I be getter off going for a NAT configuration?

---

### Post by aktiwers on 2009-11-27
The default route goes through localhost (127.0.0.1)..

---

### Post by toupeiro on 2009-11-27
Your switch has to be able to support multiple VLANS based on the way I'm interpreting your diagram.  Your diagram for your laptop suggests two different network connections: 1.1.1.x network and your internet connection, but it looks like they are coming from the same interface, and you have some sort of bridge or splice into your switch which is definitely not recommended, and likely will not work at all. **EDIT:** Unless, you are implying NIC2 is giving you internet and you just don't want to share the IP, which makes more sense.

Aside from this, it looks like you're trying to have your switch manage a 192.168 network and a 1.1.1 network, which I think is the source of your problem.  I don't think the average off the shelf D-link or linksys can do this.  Business class or enterprise grade switches, sure! Unless you know for certain that your switch can support multiple VLANS or potentially trunking, Your best bet is to use two different external switches, and use both network interfaces on your laptop.  If you plan on private networking VM's, they have to be seen on the same "virtual switch" and if that virtual switch is going to span outside of the virtual machine environment to a real switch sharing other physical networks, it has to be able to support trunking and/or multiple VLANS.

---


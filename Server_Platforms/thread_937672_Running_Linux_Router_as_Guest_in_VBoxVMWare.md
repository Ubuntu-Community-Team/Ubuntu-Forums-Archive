---
title: "Running Linux Router as Guest in VBox/VMWare"
date: 2008-10-04
forum: Server Platforms
---

### Post by hehehehe on 2008-10-04
**Running Linux Router as Guest in VBox/VMWare**

First of all, this is a bit of an ambitious project of mine and I'm still soliciting ideas on how to implement it. I'm not even sure if it would actually work.

Basically, what I would like to do is run a Linux host (Ubuntu Server or whatever suits for this purpose)and run two guests OSes using VBox or VMWare. I have previously played with VBox before but no clue yet about VMWare. The first guest OS would be one of those LInux/BSD router OSes and the other guest would be XP/Win98. I still haven't decided yet which one to use as the router OS. I'm thinking of going with pfsense, clarkconnet or vyatta. I'm also planning on having multiple internet connections fed into that router OS. Initially, let's just say I want to connect my two would-be-ISPs to this router OS.

Here's what I can picture in my head right now:

How many interfaces do I need for this btw?

eth0 > connected to switch for LAN, assigned to host

eth1 > connected to ISP1, assigned to guest router OS
eth2 > connected to ISP2, assigned to guest router OS
eth3 > connected to switch for LAN, assigned to router OS guest

eth4 > connected to switch for LAN, assigned to Windows guest

I wanted it in a way that the host and the windows guest will use eth3 as their gateway for internet.

I'm more troubled regarding setting up the interfaces for the guests OSes as I haven't done "bridging" and stuffs before. I've used NAT with my VBox setup before.

I was hoping maybe somebody have done it before and he can advice me regarding this - the hardware requirements and especially with setting up the interfaces. TIA


p.s. Sorry if this thread should belong to different forum category it's hard to classify what I want to achieve really.

---

### Post by windependence on 2008-10-04
You should consider running VMware ESXi which is now free. Test it on your hardware first though. 

The beauty of this is within your host box, you can create virtual switches and virtual nics so you don't need so many physical nics.

You could actually do this entirely with two physical nics in the box, one for traffic IN and one for traffic OUT. I personally have done it even with only ONE nic, but I would not recommend that for production as you would have to route traffic out and in over the same interface.

The ideal way to do it would be to use two physical nics for incoming traffic and two physical nics for outgoing traffic. Then, you can bind each pair of nics together for redundancy and greater bandwidth. Inside the VNware host, you would have a virtual switch that is not connected to any external interface. Your pfsense box would be connected to another internal virtual switch and that switch would be connected to the incoming nic. the pfsense box would also be connected to a second internal virtual switch that wouold be attached to the outgoing physical nic(s). I am at work right now, but later I will post you a diagram on how to do this and it can all be done visually in the VMware GUI on a remote box so you will be able to see what you are doing and it will make sense.

One of the best features about VMware IMHO is the networking and virtual hardware configurations you can do. You can literally build a data center in a box.

Like I said, when I get off work I will put up a diagram and if you need more help just let me know. I spent all last week in VMware boot camp.

-Tim

---

### Post by hehehehe on 2008-10-05
Thank you for replying to my thread and I look forward to your explanation. Well, as I was expecting the idea I had wasn't exactly right.

Just some quick questions:

The NIC bondings are done in the host, right? How do I do that in Ubuntu? I haven't actually done like that or close to that before. Or perhaps, I could skip this part since the application for this project doesn't really have that much bandwidth requirement. I am planning of using this on an internet cafe (a computer rental shop) with about 20 Windows clients. I just had this idea so I can consolidate resources. It would be great if could run a high grade router and the "server" (the Windows guest running the Cafe management software) in one PC.

How do I physically connect my two ISPs to the PC and the interface for the LAN?

Once again, I'm very grateful somebody has a clue about this coz I honestly don't. :)

---


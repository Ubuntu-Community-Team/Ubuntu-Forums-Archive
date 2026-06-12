---
title: "hotspot as a server"
date: 2020-11-16
forum: Server Platforms
---

### Post by steven-dalong on 2020-11-16
Hi, I hope that someone can understand what I'm trying to do or that I can communicate it well.

I have a laptop with Ubuntu server on it. I want to be able to access it through wifi with another device, but not through a router. I thought that maybe I could use a hotspot method. But it says that I must have an Internet connection through a source other than wifi. I don't want to access the internet through the server. I want to access the server pages itself. Is there a method to do this? 

I know it is an unusual request and so far the responses are, "Use your router." Surely there must be a way to make it happen. I hope someone here has a suggestion to make my idea work.

Thanks in advance.

---

### Post by LHammonds on 2020-11-16
I have actually done this before with an Ubuntu laptop a couple years ago.  When my ISP at home was not working well for months (there were chewed up cables at a junction box) I had to use my iPhone's hotspot but my work PC did not have wireless capability...thus I had to go over wired LAN and have it route through the laptop to utilize the iPhone's internet connection.  Keep in mind that hotspot Internet has different rates so if you have "unlimited data" it likely does not apply when using hotspot.

I do not remember the exact steps and unfortunately, I did not document what I did nor do I have that OS configured that way anymore.

I had setup the wired LAN port on my laptop as static IP to communicate to the LAN (example: 192.168.1.20).  For the wireless side, I connected to my iPhone hotspot like I would any other wireless access point.  (example IP: 10.10.10.2)

I had to configure a routing rule to route any incoming traffic from 192.168.1.x subnet and send to the 10.10.10.x subnet.

I then added DHCP server to my laptop so it could hand out IP addresses with the default route IP being the laptop (192.168.1.20).

On my hardware router that was connected to DSL, I told it to stop handing out IP addresses and instead told it to route any DHCP requests to my laptop (192.168.1.20).

Any device on my LAN that rebooted and got an IP from my laptop would then be able to access the Internet via the Ubuntu laptop as the router and out through my iPhone.

LHammonds

---

### Post by TheFu on 2020-11-16
People suggest using a router because that is 100x easier.  Devices on the same subnet are easy to access.  A used $5 router from 20+ yrs ago that you don't connect to the internet can make a little network between 2 computing devices.

You haven't explained clearly how you expect the 2 systems to communicate.  

Please act like you are explaining this to a 5 yr old - what wires are involved. 
[LIST]
[*]Where do they plug in? 
[*]What are the devices involved? 
[*]What OSes do they run?  
[*]Which protocols do you want them to use to communicate?
[/LIST]

Don't make us guess your intentions. Please.

I'm guessing you really want your "server" to be setup as an Access Point and router.  There are guides for doing that.  But without a router working as a default gateway, you'll have to manually add routes in both directions for the client to access the AP and for the AP to send packets back to any clients.  This isn't fun.  A $5 router does this easily.   Which is why everyone says to use your router.  Driving to the used parts store, spending $5 in a linksys router from 2005, and driving home, setting it up for a LAN only use, no internet, will be faster and much less painful.

Just sayin'.

Or you can find guides for how to make a computer into a wifi router. Most will probably want to replace your OS with a router-specific version, and doing the setup manually will be a pain. [https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) Don't worry that he's using a mini-PC. As long as you have a wifi chip and a LAN ethernet port, that should be sufficient.

---


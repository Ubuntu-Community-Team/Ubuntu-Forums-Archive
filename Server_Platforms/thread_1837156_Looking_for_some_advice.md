---
title: "Looking for some advice"
date: 2011-09-01
forum: Server Platforms
---

### Post by n8af on 2011-09-01
Hey guys! Part of my schooling degree plan involves learning about the greatness of linux and ubuntu as a server. I was hoping to get some hands on experience at home using Ubuntu Server as a home file/media share server to manage my information and backups (and more capabilities later on as I feel comfortable with experimenting). 
 
The advice that i'm inquiring about is setting up my network topology. Currently I have a dedicated PC (acting as a DHCP) for my network with a 5-port switch and a wireless AP connected to the switch:
Internet->Modem->into Ethernet Port on dedicated PC-> 2nd Ethernet Port on dedicated PC out to-> 5-port Switch -> WiFi AP ))) (((-> 2 Wireless PCs.
 
Currently I have windows 7 running on the dedicated PC configured for Internet connection sharing in order to share internet access with the other PCs on the network. 
 
The main question I have is, would this same configuration (network topology above) be possible using an Ubuntu server box in place of the dedicated PC?
 
Any advice on network/IP address configuration (LAN/WAN) would be greatly appreciated
 
-N8

---

### Post by rubylaser on 2011-09-01
@n8af, yes this is very easily accomplished, but it seems like a massive waste of power just for a router.  Is your wireless device truly just an access point, or does it include a router?  Personally, I would separate my router from my fileserver.

I have IPCOP running on an embedded PC Engines WRAP box (not in production any more).  It's been running for years , uses very little power. It just performs DHCP, DNS, Dynamic DNS updating, and VPN services for my network.

I have my fileserver running on separate hardware.

---

### Post by n8af on 2011-09-01
> **rubylaser said:**
> @n8af, yes this is very easily accomplished, but it seems like a massive waste of power just for a router. Is your wireless device truly just an access point, or does it include a router? Personally, I would separate my router from my fileserver.
 
I have IPCOP running on an embedded PC Engines WRAP box (not in production any more). It's been running for years , uses very little power. It just performs DHCP, DNS, Dynamic DNS updating, and VPN services for my network.
 
I have my fileserver running on separate hardware.
 
Yes my wireless device is only an AP.
 
Personally, I just don't like routers for a few reasons. The area I live seems to have numerous lightning storms and the router is the first thing to go - even with power/ethernet/coax all on surge protectors. Besides that, i'm constantly resetting the damn thing - updating firmware, or searching t-shooting forums because of DNS server failures (yes this was linked back to my current router). Over the years, I've had better performance and reliability with a switch configuration. Switches are less maintenance (as long as you have a reliable host). 
Thirdly, i'm trying to get some hands on experience setting up a server and tinkering with hosting.
 
I'm just trying to plan ahead. The hardware i need to build the server box should arrive next week.

---

### Post by rubylaser on 2011-09-01
I think you're confused :)  Your PC right now is acting like a router for your network, so you still have one.  A switch doesn't perform routing, unless you have a managed switch that supports Layer 3. 

If you've seriously had your power, ethernet, and coax hooked up to reputable brands of surge protectors, and lost numerous devices, it's a miracle your PC hasn't went too.

You ask about LAN / WAN recommendations, but it sounds like your mind is made up already (purchased hardware and decided on your LAN setup). I will tell you that it is silly to combine all of this functionality without separation of some of the services.  Virtualizing, at a minimum, the firewall would make the rest of the services on this host much more secure.  

Good luck and welcome to Ubuntu.

---

### Post by n8af on 2011-09-01
> **rubylaser said:**
> I think your confused :) Your PC right now is acting like a router for your network, so you still have one. A switch doesn't perform routing, unless you have a managed switch that supports Layer 3. 
 
If you've seriously had your power, ethernet, and coax hooked up to reputable brands of surge protectors, and lost numerous devices, it's a miracle your PC hasn't went too.
 
You ask about LAN / WAN recommendations, but it sounds like your mind is made up already (purchased hardware and decided on your LAN setup). I will tell you that it is silly to combine all of this functionality without separation of some of the services. Virtualizing, at a minimum, the firewall would make the rest of the services on this host much more secure. 
 
Good luck and welcome to Ubuntu.
 
My Bad - i meant stand-alone routers (linksys, d-link, netgear, etc - "the standard residential internet sharing box" :P). I was comparing using a switch as the star topology component rather than a stand-alone router.
 
Actually - my PC NIC did go out one of the times - had to replace the mo-board.  I'm not sure why the surge protector likes to allow enough juice through to kill the router and nothing else.  Even though I spent good $$ on several surge protectors, I swapped it out anyways - maybe a lemon.  The residence isn't that old either, so I can't blame it on old wiring or bad grounds - oh well, thats another topic.
 
I'm taking note of your recommendation about a VPN and separating the routing from the file storage - that makes a lot of sense.
 
When I mentioned LAN/WAN - that was a typo - i meant LAN/WLAN, lol

---


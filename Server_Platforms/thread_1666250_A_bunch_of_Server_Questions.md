---
title: "A bunch of Server Questions"
date: 2011-01-13
forum: Server Platforms
---

### Post by nkhosla on 2011-01-13
I am totally new to servers, so I have some questions that may seem ridiculous--please don't laugh :p


I need to create a secure (as in more secure than the WPA2 stock network w/firewall that comes with any good router) wireless network, and I need to do so (relatively) cheaply. I am very familiar with Linux (Ubuntu specifically), so naturally it is what I gravitated to initially.  However, I have never set up a server, let along a Linux one, so I have no idea where to start.

My server will initially be an old-ish laptop (1GB RAM, 1.5GHz single core intel processor), but I will upgrade one I learn what I am doing and establish that this is the right way to solve the problem.  This would be used a router for the wireless netowrk.

Some requirements are:

WPA2.  Self explanatory

user authentication using MAC addresses.  I do not want people to log in every time they use the network (I know that is a security hole, but the network will be acceseed by some in 3 minute intervals then the client will be shut down, so it is a huge inconvenience and a damper on efficiency).  I was thinking a way to have someone log in with their username to authenticate their device, and then the network would remember the MAC address.  It would tie it to that user, so whenever they went to connect, the network would remember that they were ok to go.

Tracking.  I need to know all URLs (not just IP addresses) requested by each user.  This would probably be tied to the MAC address, and through that to the user.

VPN.  I need to be able to use a vpn from outside to get into the network.  Not so much for file access, but for secure internet connections on public hotspots.

Is there anything else that I can do?  One suggestion was to use a RADIUS server.  What else could I do to reach that level of security, or at least close to it)?  [S]Is there any way to implement a RADIUS server on a Linux box (yeah, that is how lost I am)?[/S]  I found freeRADIUS, so that answered that question.

Thanks,
Nkk

---

### Post by rubylaser on 2011-01-13
WPA2 is a standard, so you're not going to get a more secure version of WPA2 without adding a RADIUS server to the mix.  I wouldn't even bother with MAC address filtering, it's basically useless to stop anything and can cause problems with valid users connecting.

Right off the bat you're going to have a hard time doing this with a laptop because you'll want to have multiple NICs, for WAN, LAN, and potentially DMZ or segmenting your wireless traffic from your LAN as well.

I would normally suggest using a firewall distro that has all the reporting and tools built-in i.e. IPCOP, Smoothwall, or Pfsense.  You could use any of these to accomplish what you're asking, except, you will need more network interfaces.

---

### Post by nkhosla on 2011-01-13
Ok, so RADIUS it is.  Is there any way I could get away with a laptop if I bought a USB ethernet adapter such as [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4776334&CatId=589](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4776334&CatId=589) ?  I see no reason it should not work, but I clearly have no idea about servers, so I want to make sure.  I know I am being cheap here, but I was hoping to learn and make sure this is the right solution before I bought an expensive server. 

How many NIDs do I need?  In my mind the setup goes ISP > RADIUS > Router > connected clients, so I see I need eth0 (RADIUS to ISP) and eth1 ((RADIUS to router).  Am I mistaken?

-Nkk

---

### Post by rubylaser on 2011-01-14
You could go with a USB NIC, although you'll be bandwidth limited, so make sure you use that for the WAN side.  I wouldn't suggest buying an expensive server in any case for this.  A Soekris box or a PC Engines ALIX embedded platform is perfect for a router, VPN, monitoring solution, and they both have mini-PCI slots to add a wireless card as well.

I would run a firewall distro as I said before with one of these devices.  They use hardly any power, are fanless, and best of all, they just work.

---

### Post by nkhosla on 2011-01-14
Soekris boxes look good.  However, I just got wind that a department in the college I study/work at may be getting new computers, and it is one of the departments that essentially gives away its old computers.  I am going to see if I can get one of those, and if not then I can get the soekris box.

Thanks
Nkk

EDIT:  Would there be a min requirement?  I looked at all the distributions, and they are all very light, but is a 133mHz processor/64MB RAM too little?  Will it ever get overloaded if, for example, a couple of peopple were on the wireless network and a few other people were trying to VPN in?  Sorry, I know that is a dumb question, but I am totally lost and am really do not want to waste money.

---


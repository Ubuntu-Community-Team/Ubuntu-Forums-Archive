---
title: "Mac Address Wireless Access Point"
date: 2008-11-05
forum: Server Platforms
---

### Post by RobbieVeer on 2008-11-05
Hey this is my first post and i'm kind of a newbie so please keep it simple :P

I have a ubuntu 8.04 server running with dhcp3-server and it works great but now I'd like my server to block unknown wireless access points in my network.
Is there a way for my server to recognize a wap?
I heard that vendors give wap's a mac address from a certain range, is that correct?
I know mac addresses are kind of easy to spoof but our admin thinks people won't take the effort to spoof an access point

---

### Post by RobbieVeer on 2008-11-06
anyone?:)

---

### Post by lisati on 2008-11-06
Some routers come with this kind of capability built in for the wireless side of things by a "whitelist" of MAC addresses that are allowed to access my home network, e.g. the Netgear WGR614 I have sitting in a drawer, The router I replaced it with can be set to block wireless devices by default, until I "tell" it to search for wireless devices to allow in either by pushing a button on its front panel, or by an option in its configuration pages.

---

### Post by RobbieVeer on 2008-11-06
Well thats not exactly what i want..
I wonder if a router or dhcp server can see whether a device is a access point or not

---

### Post by MJN on 2008-11-06
A 'Wireless Access Point' is just a generic term used to describe a device that provides network access to wireless clients. Hence, whilst it may usually take the form a specific device from a specialist vendor it could equally just be a PC with a wireless card in it.
 
Hence, there is nothing unique to a 'Wireless Access Point' that could be used to describe it, and certainly nothing specific about its MAC address.
 
It might be worth you taking a couple of steps back and deciding exactly what the risks are that you need securing against. I suspect it is access from unauthorised clients in which case that's where you should be concentrating your efforts (usually through encryption and the inherent privacy/authentication that this brings).
 
Mathew

---

### Post by RobbieVeer on 2008-11-06
Well we suspect that some employee's pluged in a ap for more mobility on there laptops. These might not be secure.. 
So we only want to hand out ip-addresses to the ap's that we know of..

---

### Post by MJN on 2008-11-06
You should be treating those AP's just as you are clients. After all, you don't know what the clients are doing either (they could be allowing others access through an 'Internet Sharing' / ad-hoc networking mechanism).
 
Mathew

---


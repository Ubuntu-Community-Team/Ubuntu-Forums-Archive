---
title: "Ubuntu Server 16.04 not serving website"
date: 2016-07-11
forum: Server Platforms
---

### Post by cybercyb on 2016-07-11
I am unsure as to if this is the right place for this topic. 

I have an Ubuntu Server installed on VMWare Player 12. It is a bridged connection. I have the static IP address set up. I have a domain name pointing to the server. I can access the website via local host by typing the domain. If I try to go to the domain via phone off the local network, the website is not found. I used canyouseeme on port 80 and can be seen. I am unsure as to what to do now. If you need any more information I will add it.

Thanks!

---

### Post by TheFu on 2016-07-11
In order for the internet to get to your server running inside a VM, the entire patch to that service must be cleared.  A few checkpoints:
* Do external DNS know how to find your public IP using the domainname you've purchased?
* Does your ISP **NOT** block port 80?
* Does your phone use a public DNS or something curated by the cellular company?
* Lookups inside the LAN don't help people outside find it. Public DNS is needed.
* What are the IP addresses for 
** the Ubuntu server and
** the phone and
** the public IP on the WAN side of your router?
* Does the router allow opening and forwarding port 80/tcp to an internal IP?  Has that been configured?

Lastly, and probably most important .... do you understand all the security implications of running an internet facing service and have taken the necessary steps to lock the server down sufficiently?

---

### Post by cybercyb on 2016-07-11
GoDaddy holds my domain name. I pointed it to my servers IP. (Or should it point to my host IP)
They do not block port 80 (Xfinity). I used canyouseeme.org and showed it could see me on port 80.
It was on the Cellular company network (Straight Talk).
I am unsure on what you mean by what the IPs are for.
I have forwarded port 80/tcp to my servers IP on my router. (The only way for canyouseeme.org to see me on port 80)

---

### Post by cybercyb on 2016-07-11
Alright I got it to work. Thanks TheFu for the check list. It made me think. I had to point the domain name to the hosts static IP not the servers IP. I am unsure why that is though. You would think it is supposed to point to the server. Either way the server grabs it and points it to my website.

---

### Post by TheFu on 2016-07-12
Happy you figured this out. Please mark the thread as "SOLVED" to help others both looking for a similar solution AND so people trying to help don't bother with this thread.

BTW, I cannot explain anything without the requested data being provided. Hundreds of assumptions were made just with that list of items. Some probably aren't valid.  The WAN IP is the one that needs to be used by all clients and where the DNS needs to point.

---


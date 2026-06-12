---
title: "Setting up Ubuntu as firewall?"
date: 2009-11-10
forum: Security
---

### Post by lotster on 2009-11-10
Hi all!

I'm not entirely an Ubuntu newbie, though I only have a basic knowledge of its functioning.

What I need to know is this:

I have a customer who needs a firewall.  This firewall must be set up between the incoming internet connection (through a wireless antenna with RJ45 connector to PC) and the office network (running Windows, we are currently in the planning phase of a possible migration to Ubuntu).  Can anyone please tell me how this can be done?  I understand Firestarter might be able to do this, but I don't even know where to begin.  Is there any kind of step-by-step guide?  Or any suggestions you can give me?

---

### Post by sh4d0w808 on 2009-11-10
I recommend U to check out all infos about iptables instead of Firestarter or other GUI tools.

Furthermore, if U plan to build up this machine only for firewall purposes, do not use GUI entirely, only Command Line Interface (CLI) - and maybe use Debian instead of Ubuntu. Also do not recommend wireless connection, only wired - from security point of view.

---

### Post by __p1n__ on 2009-11-10
This is a pretty trivial application however without the requisite knowledge/experience it will appear daunting.

Given that this is a commercial application you should consider outsourcing this work to a knowledgable individual or firm and use their expertise to maximize the value to your customer.

If you must plug ahead then use the ubuntu built-in iptables facility to define your firewall.  You have two adaptors, right?  One connects to the wireless surrogate and one connects to some switch/hub or router.  These connections are represented as named interfaces (e.g. eth0.)  The connection representing the wireless surrogate should be treated as a WAN with unsolicited packets being automatically dropped.  The connection representing the internal switch should be treated as a LAN.  You will want to create bridging rules using iptables describing what and how traffic flows between the zones.

note: you can do all the above automatically with a USD 30.00 consumer appliance from cisco/linksys.

---

### Post by cdenley on 2009-11-10
If you want to build a dedicated firewall, I would suggest PFSense. The easiest solution would be a pre-built firewall appliance, though, as p1n suggested.

---

### Post by MasterNetra on 2009-11-11
> **sh4d0w808 said:**
> I recommend U to check out all infos about iptables instead of Firestarter or other GUI tools.

Furthermore, if U plan to build up this machine only for firewall purposes, do not use GUI entirely, only Command Line Interface (CLI) - and maybe use Debian instead of Ubuntu. Also do not recommend wireless connection, only wired - from security point of view.

+1

Firestarter only mods the settings for iptables which is installed in Ubuntu by default.

---

### Post by bodhi.zazen on 2009-11-11
A firewall is fairly critical to security and I would not use Ubuntu. What you want is a minimal installation with as few functions as possible. I advise you look either at a commercial firewall, routers are not *that* pricey, or go for a firewall specific distro such as IPCop (there are several to choose from).

Basically less applications / minimal install = less potential exploits fo rcrackers.

You can configure a firewall with shorewall or iptables :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

The key to configuring a firewall yourself if to test, test, test , ie learn to use nmap or similar port scanners.

---

### Post by Yoann Juet on 2009-11-14
If you have some experience with linux, I'd suggest you installing a minimal debian distro with debootstrap then using the GUI Firewall Builder ([http://www.fwbuilder.org](http://www.fwbuilder.org)) to build complex policies in IPv4 and/or IPv6.  On my opinion, such an open source solution is perfectly suited for small to medium businesses (and even more). You need advanced features just like commercial solutions ? not a real issue...

- High Availability Cluster with conntrackd and keepalived
- Protocol Enforcement with L7 Filter
- Intrusion Detection System with Snort
- Transparent Proxying with Squid
- Private Virtual Networking with OpenSwan, OpenVPN...

Commercial solutions traditionally have significant ease of use / ease of integration. With open source, you need time and skills to build a similar infrastructure. That's the dilemma sys/net admins are facing.

---

### Post by QLee on 2009-11-14
[QUOTE=bodhi.zazen]A firewall is fairly critical to security and I would not use Ubuntu. [/QUOTE]
+1

[QUOTE=bodhi.zazen]What you want is a minimal installation with as few functions as possible. I advise you look either at a commercial firewall, routers are not *that* pricey, or go for a firewall specific distro such as IPCop (there are several to choose from).[/QUOTE]

+1 again. 

I have experience with IPCop and it, in my opinion, is a good one, as mentioned, there are others.

As example: An IPCop firewall can run successfully on a very low spec system and perform very well. You could use an old piece of hardware for a dedicated firewall/router instead of retiring it.

I have run IPCop on a 486 with 16MB RAM but you'll have a better system than that and I can't guarantee one that old would perform well in a very fast network with lots of clients.

---

### Post by Cheesemill on 2009-11-14
Another good firewall distro to use is [Smoothwall]("http://www.smoothwall.org/"), I use it with several of my clients.
Once installed you can use the web front-end to administrate it.

---

### Post by hictio on 2009-11-15
Another firewall distro, really polished and amazingly easy to install is [Endian](http://www.endian.com/en/community/download/), the community, free and without official (commercial) support.
I'm currently using using two of those on separate locations, they work quite good, given that they are free, and that they run on almost any hardware you can scrap :)
The main disadvantage, at lest from the version I'm testing, is the traffic shaping, everything else works really well (web proxy, VPN Server, content filtering, SIP proxy, DHCP, DNS, NTPD, etc.)

---


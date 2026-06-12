---
title: "Ubuntu server or dedicated router/firewall distros?"
date: 2005-09-21
forum: Server Platforms
---

### Post by GOwin on 2005-09-21
I'm planning to use an old P-166 computer for a router/firewall:

I need the following services:
* DHCP
* Squid
* SSH
* Firewall
* dual-WAN / dual-gateway support
* Load balancing 
* Bandwidth control and management
* Ethernet segmentation

Objective is to deploy such a router in a building with several small offices (not related to each other)

Router will be headless and will be managed remotely (hopefully).

Would a dedicated appliance be better? Or is there a router/firewall distro out there who can do the same job?

---

### Post by dk_pa on 2005-09-21
Not sure about all that stuff.  Looked up for load balancing.

Maybe [http://leaf.sourceforge.net/](http://leaf.sourceforge.net/) would work for you.

Features
[http://sourceforge.net/docman/display_doc.php?docid=1397&group_id=13751](http://sourceforge.net/docman/display_doc.php?docid=1397&group_id=13751)

Dunno nottin' about it tho really.

I have used Coyote Linux for over a year now and really like it a lot.  I don't think it can do all that stuff you want at the current time tho.

---

### Post by venzen on 2005-09-21
I agree with the advice to visit the LEAF (Linux embedded firewall application) site mentioned above. My organisation uses the Bering uClibc firewall which can be downloaded from there. It contains most the packages you mention

* DHCP
* Squid
* SSH
* Firewall
* Load balancing
* Bandwidth control and management
* Ethernet segmentation

However packages are also available for dual-WAN / dual-gateway support and you can get more info about this from the creator of Shorewall firewall's personal network log: [http://www.shorewall.net/myfiles.htm#RFC1918](http://www.shorewall.net/myfiles.htm#RFC1918) 

The great thing about Bering is that it is built on Debian (like Ubuntu) but a cutdown version neaning that the whole linux firewall fits on 1 (or 2) floppies. This means no harddisk - low power consumption and harddrive failure is obviated.

BTW - the Bering documentation and Shorewall [setup guide](http://www.shorewall.net/shorewall_setup_guide.htm)  will suggest various pieces of DOS software for windows users - nevermind, you can easily write the downloaded Bering disk image to floppy and edit it - all in linux.

Feel free to post me privately for advice.

---

### Post by LordHunter317 on 2005-09-21
I'm going to through in my hat for a COTS, hardware solution. preferably something like a Cisco or Juniper box.

Doing the last several items in Linux is very difficult: the traffic management stuff is reasonably full featured, but all the interfaces I've used are poor and difficult.   True bandwidth mangement, where traffic is throttled on a per-port level, isn't really possible at all.

Also, without a ton of RAM, Squid alone would probably be that much for the box, if your network is busy at all.  Squid requires some pretty considerable and serious resources for a busy network.

---

### Post by GOwin on 2005-09-21
Re bandwith management
Actually, my needs are simple. (Or at least, I think it's simple). Is it not possible to limit a particular subnet, say those in 192.168.10.* to 256kbps?

Or a particular IP address is limited to say 15kbps.

Or blocking certain ports (especially P2P/torrent)

Err .. obviously, I'm not technically familiar with these stuff.

---

### Post by LordHunter317 on 2005-09-21
[QUOTE=GOwin]Actually, my needs are simple. (Or at least, I think it's simple). Is it not possible to limit a particular subnet, say those in 192.168.10.* to 256kbps?[/quote]Yes, though it's a real headache compared to OBSD.  And depending on which ways you need the shaping, difficult.

Which may be a better fit, but I'm not sure how well doing load-balancing over WAN routes works there anymore, if at all.

---

### Post by GOwin on 2005-09-21
what if we drop the dual-WAN requirement and load-balancing, and keep the rest? what would you suggest then?

---

### Post by pietro_spina on 2005-09-22
[QUOTE=GOwin]what if we drop the dual-WAN requirement and load-balancing, and keep the rest? what would you suggest then?[/QUOTE]

You might want to give one the flavors of ClarkConnect some thought. Some developers are regularly in the forums and will probably give you good advice(even to the point of sending you off to a diferent sollution if that is what you need.) I can't tell you anything about their service for a fee, but I've been runing a home edition for about a year now and it has been pretty smooth sailing. (smoothwall seems to be pretty popular also)


info page
[http://www.clarkconnect.com/info/](http://www.clarkconnect.com/info/)

forums for the home edition
[http://www.clarkconnect.org/forums/ubbthreads.php](http://www.clarkconnect.org/forums/ubbthreads.php)

-p

---

### Post by cactus on 2005-09-24
Dont forget ipcop. It is a nice 'slap on and go' solution.

---


---
title: "create a linux server from a network print server (Belkin, etc)"
date: 2009-08-28
forum: Server Platforms
---

### Post by Nathan_M on 2009-08-28
Hi,
I've had a great idea that I could create a cheap linux server by installing Linux onto a manufactured print server. This would allow me to have a headless server with WiFi support, and usually a single USB socket to use with whatever device I like, and most importantly, it'll be dirt cheap! It should go without saying that I'm not planning on using it for anything hefty due to the lack of processing power... maybe just a file server I can leave on permanently, and something to tinker with for fun. Many devices use Linux and ext2/3 anyway, so I expect this will be possible.

Anyone got any thoughts/recommended devices? I'm looking at the kinds of things I can get cheaply on eBay.

---

### Post by volkswagner on 2009-08-28
Well I can't comment on a print server.  I can't imagine they would have enough resources.  I also don't know off hand of any units which have been opened up.  You may also want to add a router type device to your research.

You may be interested in the Buffalo Linkstation NAS devices of "yesteryear".  I have messed with one version, the HD-HLAN v2 MIPS (LS1).  I purchased the LS1 with 160gig  hard drive = model "HD-160LAN" for under fifty bucks as a refurb, and the HD-HLAN (HG) which is a gigabit model.  I have not messed with the HG which I also purchased as a refurb. on Buy.com for less than a hundred bucks with a 400gig disk.

There is a great amount of flexability once the firmware is flashed with opensource.  You can even run a Debian server (I have done this, but ran out of time on that project).  I did run into a snag while trying to enable NFS share, I think there is a Kernel mismatch or it is not fully supported.  

Most units have two USB ports for adding  printers or extra disks.  Not sure if it would support a USB hub.

You will need a windows PC to do the flash.  I am not sure if the flash utility would run under Wine. 

The support site can be a little confusing at first to locate all the needed info.  Let me know if you get one and need any help.  

Good luck and happy hacking.

Here is the [bible for hacking the linkstation]("http://buffalo.nas-central.org/index.php/Main_Page")


Here is a [120gig version of the HD-LAN]("http://cgi.ebay.com/BUFFALO-TECHNOLOGY-HD-H120LAN-LinkStation-NAS-Drive_W0QQitemZ190330854061QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item2c509a5aad&_trksid=p4999.c0.m14")

EDIT:  Here are some [specs]("http://buffalo.nas-central.org/wiki/FAQ#What_are_the_differences_between_the_HD-HLAN_.28PowerPC.29.2C_HD-HLAN_.28MIPSel.29.2C_and__The_HD-HGLAN_.28PowerPC.29_LinkStations.3F").  You may want to decide what you want to do before picking a model, even version number.  Some offer more options over others.

---


---
title: "ideal server config for home system"
date: 2008-07-14
forum: Server Platforms
---

### Post by joisey04 on 2008-07-14
Hello All!

First, lease don't flame me if this was discussed a lot already. I spent all weekend searching and I'm still not sure what to do.
I'd like to set up a powerful home server for all my needs. Absolute focus is preventing data loss and easy recovery if something goes south.

I'd like to realize everything with low power consumption and was thinking of mini-ITX boards for all the servers, stuff them in 19' housings and in a small rack together with a UPS and storage. I will probably go with a large RAID 5 or 6 for the main server. I want to go away from all the different USB and dedicated NAS drives flying around right now.

I'm also not sure, if I should put every service (web, mail, file, media,..) on a dedicated server (keep i mind: mini-itx) or go with one big system (then not mini-itx anymore) and maybe virtualization. I personally like the idea of having dedicated machines since I could power them off whenever I want or replace them or service them or, or, or without effecting the other systems but maybe there are arguments for a different solution.

Main clients are 3 Mac's (OSX 10.5) and going forward also linux frontends.

This is what I'm planning:

File-Server:
Hosting all my files, like it says. RAID 5 or 6??

Mailserver:
Standard mail server; nothing special; usable from inside and outside. 
Dedicated server?
Where do I store the database? on the main file server?

Webserver:
I'd like to have a web presence as well as an intranet. Do I need two servers for security reasons?? Where do I store the database? (MySQL,..)

Mediaserver:
Server to provide and stream media over the network. Storage location of the media?? dedicated server (MPD, Jinzora)???

PVR Server:
Server with a couple of PVR cards to stream TV to different frontends; due to the hardware requirements this is probably a dedicated server

Backup:
What is a good solution for backup? Another server with drives? Tapes are so expensive. Keep in mind it is a home project. Any ideas here?

All the other stuff:
Where do I put Remote access, VPN, SSH, DNS, DHCP,...? On the mail file server?

I'd appreciate any advice as on how I can realize this best. I'm new to Linux but not to networking (MS & mac) or computers in general.

Thanks!!
J

---

### Post by windependence on 2008-07-14
You'll never be able to do this (with stability) on an ITX box.

However, you are not far off when you say virtualization. I would go with one 4u server with server class hardware, at least a dual processor machine, and run VMs for all the servers. You will take the least power that way and spend the least amount of money on hardware.

RAID 5 - REAL RAID as in hardware RAID is fine.

mailserver - dedicated VM - zimbra

webserver - dedicated VM - apache

mediaserver - ?? Your guess, I have not done this.

PVR server - same thing, no clue here

backkup - dedicated VM backing up to drive not in the RAID array - Amanda or Bacula.

all the other stuff - dedicated VM just for all the gateway stuff.

Would recommend you take a look at FreeBSD for the guests.

Just MHO.

-Tim

---

### Post by joisey04 on 2008-07-14
Thanks for the reply!

Let's say worst case: My mainboard dies and I can't find the same one again. How high is the probability not getting this working again without a complete reinstall? Or will there be Mainboards (if I use a common one) which I just can replace.

Could anyone please point me to a resource where I can find a proven, common, reliable HW setup? (which MB, Mem, Controller, CPU....)


So I'd use the VM's to run all the different machines but I store everything on my big storage on the file server VM, right?


> **windependence said:**
> Would recommend you take a look at FreeBSD for the guests.
what do you mean by guest?

Thanks!
J

---

### Post by Krupski on 2008-07-14
> **joisey04 said:**
> Thanks for the reply!

Let's say worst case: My mainboard dies and I can't find the same one again. How high is the probability not getting this working again without a complete reinstall? Or will there be Mainboards (if I use a common one) which I just can replace.

Could anyone please point me to a resource where I can find a proven, common, reliable HW setup? (which MB, Mem, Controller, CPU....)

I've had very good luck with Intel brand motherboards. They are rock stable, and they are built very well. Of course, they run Ubuntu 64 bit Server flawlessly.

I've put together several NAS (Network Attached Storage) boxes using Intel DG33BU mainboards ([LINK]("http://www.intel.com/products/desktop/motherboards/DG33BU/DG33BU-overview.htm")) installed in Antec 2U size rackmount cases ([LINK]("http://www.antec.com/us/productDetails.php?ProdID=94229")).

The Intel boards are standard Micro-ATX size so you are not locked to proprietary hardware. The DG33BU and others like it support up to 8 GB of DDR-2 memory and Core 2 Duo or Core 2 Quad CPU's with up to a 1333 MHz. FSB.

One thing you will find about the Intel brand boards is that they have absolutely nothing in the BIOS for overclocking or overvolting the system. The boards are meant to be STABLE, not OVERCLOCKED. Personally, I find this to be a big plus.

In my NAS boxes, I find that the SATA-300 drives are the bottleneck. When copying files to or from the box over the network, it runs around 50 MB/Second and CPU usage is only a few percent (even with the CPU speed throttled down with the "conservative" governor).

Striped drives will accept data at around 85 MB/Second... but even then CPU usage is barely above "snooze"... :)

I get the best performance with the most memory... so I have the full 8 GB of DDR-2 memory installed (4 pieces of 2 GB memory sticks).

NOTE that the boxes I build are file servers only... so they have only a power cord and a network cable. A 2U box is too small (not tall enough) for a "real" computer (i.e. with a video card and other hardware installed). For that you would probably be better off with a 3U box or a standard ATX case.

Try out Intel motherboards. I guarantee you will not be disappointed.

Oh yeah... one more thing. Intel motherboards strictly follow STANDARDS which means they require 1.8 volt DDR-2 memory. Some brands of memory have fantastic looking specs, but they have to be run at 2.0 or 2.2 volts to get those specs (i.e. they are overclocked and overvolted). Intel requires the JEDEC standard which means 1.8 volts and standard clocking. CRUCIAL brand memory is available in 1.8 volt DDR-2.

Here's a ([LINK]("http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=85E6002FA5CA7304")) to a 4 GB kit (2 pieces of 2GB) that works in Intel motherboards (they're the ones I use).

Good luck!

-- Roger

---

### Post by Krupski on 2008-07-14
> **windependence said:**
> RAID 5 - REAL RAID as in hardware RAID is fine.

There's no such thing as "hardware RAID".

Even something like a Promise RAID card is just a multiport disk controller with RAID software in it's BIOS.

An ideal RAID setup (in my opinion) is installing the OS on a small SOLID STATE drive (like a compact flash card) and using multiple hard drives in a RAID configuration solely for data storage (i.e. no Ubuntu on the hard drives - just on the CF card).

This way, you are always booting from the compact flash card which will never "crash" like a hard drive can. And if a drive in the RAID array fails, you will still be able to boot up the OS and fix the array.

Also, it's easy to make a byte for byte "snapshot" of the CF card to save and use as a "last known good" in case you mess something up.

Just yesterday I was playing around with BWBASIC on my Ubuntu server box and I mistakenly created a file in the root called "?????". Woe was me when I tried to delete "?????" (as root of course)!

It wiped my whole root clean and killed the box. So, I just shut it off, used Winimage to re-write a known good image back to the CF card, popped the CF card back into the server box and bingo! It came back up and ran fine.

Having Linux on a separate, small "drive" (the CF card) turned a major disaster into a 5 minute inconvenience.

-- Roger

---


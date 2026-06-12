---
title: "IBM RaidManager Cannot Find IBM badged Adaptec 2410SA"
date: 2009-01-11
forum: Server Platforms
---

### Post by digitldrug on 2009-01-11
Hi All,

If anyone can help with this one it would be greatly appreciated.

I have an IBM re-branded Adaptec Serial ATA RAID 2410SA
OS: 8.10 server 32bit with Xfce.  I'm 2 weeks into linux/Ubuntu (but I'm going all in with desktop and server) so please bare with my nube-ness.

1) I physically installed the card and ran lspci -v to ensure that the driver was loaded.  The output was the following:

 RAID bus controller: Adaptec AAC-RAID (rev 01)
	Subsystem: Adaptec Device 0290
	Flags: bus master, 66MHz, slow devsel, latency 32, IRQ 17
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	[virtual] Expansion ROM at 40000000 [disabled] [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: aacraid
	Kernel modules: aacraid

So far so good.

2)
I then followed the directions in [[COLOR="Red"]this thread[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=597256&highlight=ibm+serverraid")to install IBM's server manager.  It should be noted that I installed v7, not v9, as that is the version IBM associated with my card.

Ideally I would have liked to just install Adaptec's version but they require an adaptec serial, which my card lacks.

I ran the IBM version of the manager but it lists 0 detected adapters.

Any ideas?  I'm wondering if the problem is that I'm running the driver that comes with Ubuntu, and not the IBM one (they don't offer a Debain variant) . . . but I'm at a loss.

Alternately, if anyone can provide a copy of  "	Adaptec Storage Manager under Linux and VMware v4.30-16038" found [[COLOR="Red"]here[/COLOR]]("http://www.adaptec.com/en-US/downloads/storage_manager/sm?productId=AAR-2410SA&dn=Adaptec+Serial+ATA+RAID+2410SA#downloads") (again it requires the registration of an adaptec card) that would probably work too.

Thanks,
Jordan

PS: Anyone know why I can't seem to add a post to the thread that describes how to install IBM RaidMan [[COLOR="Red"]linked[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=597256&highlight=ibm+serverraid") above?  I thought it would be the best place to ask but I was told that I do not have permission.  Thanks again!

---

### Post by digitldrug on 2009-01-14
Bump

I have the CD downloaded from IBM's site.  The cd is bootable and it is able to see the card so this appears to be specific to the installation on Ubunut.

Alternately does anyone know if I can use a newer version of RAIDManager with this card?  IBM supplies ver 7, but other cards have ver9 in the dl list.
Anything to get this thing to be detected.


Thanks!

---

### Post by digitldrug on 2009-01-14
OK Update

Obtained the latest version of RaidMan - raidman_9.00-1_i386
Installed, runs, but still reports "No controllers were found in this system"  :(

Can anyone help?

---

### Post by digitldrug on 2009-01-15
Once upon a time vacuum tubes randomly died, and a bug in the system was caused by . . . well . . . an actual bug.  In those days (looong before my time) if your program failed to run as expected you had to debug both hardware and software . . . . apparently we are not yet past that point.

The problem was the hardware.
Port 2 and 3 would cause the unit to fail detection if used.  Plug 1 and 4 work fine . . . so now I get to figure out if there is an incompatibility with the drives Western Digital (WD7500AAKS) 750GB drives or the card is bad.  I'll update the thread in case others are attempting the same setup and run into the same situation.

---

### Post by alastair on 2009-01-15
I'm interested in this sort of stuff. Please update if you can.

Good luck.

Alastair

---

### Post by digitldrug on 2009-01-16
It may take a while for the whole RMA process to complete but I will be sure to update once I have a new card and try again.

---

### Post by digitldrug on 2009-03-05
Wow I suck, totally forgot to post an update.

The RMA'd card works fine after a Bios upgrade . . . well it wasn't quite that easy . . . 

1) The IBM bios upgrade does not occur within the management utility (unlike adaptec's update procedure).
To update you need to download the latest driver disk and boot from it.  The driver disks will load the bios update utility first and report if an update is required. YOU MUST UPDATE or most larger hard drives will not be supported.

[http://www-947.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=SERV-RAID&brandind=5000008](http://www-947.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=SERV-RAID&brandind=5000008)

I believe this card is the SATA (ServeRAID-7t).  Download the ServeRAID Support CD (v7.12 as of this writing.) Boot from it.


2) management software:
Download the ServerRaid software CD (v9 as of this post) from the url above.

Then follow the directions here to install.
[http://ubuntuforums.org/showthread.php?t=597256&highlight=ibm+serverraid](http://ubuntuforums.org/showthread.php?t=597256&highlight=ibm+serverraid)

3) Configuring your Array.
For whatever reason I could not build or create an array because the previous (DOA) card initialized the array before completely failing, and left the drives in an unsafe state.  The solution was to boot into linux and use gparted to completely wipe the drives and start from scratch.  I'm sure there was a more graceful way to do this, but I couldn't figure out how.

Good luck all, I hope I've assisted someone struggling with this in the future.

---

### Post by digitldrug on 2009-03-05
oh and the driver that ships with ubuntu is fine, but if for anyreason you feel like upgrading, try here:
[http://linux.adaptec.com/2008/12/09/updating-the-aacraid-driver-in-ubuntu/](http://linux.adaptec.com/2008/12/09/updating-the-aacraid-driver-in-ubuntu/)

I haven't tried this but figured I'd post it for all that may be interested.

---


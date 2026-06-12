---
title: "Hardware Compatibility"
date: 2007-03-21
forum: Server Platforms
---

### Post by Linuturk on 2007-03-21
We are currently rearranging our network. This will include wiping a Windows 2000 Server and installing Ubuntu Edgy 6.10 Server to run a Cacti server.

I'd like to know about anyone who has a **Dell PowerEdge 650** with similar specs:

System Type:	PowerEdge 650
Ship Date:	9/20/2003
Dell IBU:	Americas
Quantity	Parts #	Part Description
1	4N454	KEYBOARD, 104, UNITED STATES, NMB, LOW COST, MIDNIGHT GRAY
1	4N433	MOUSE, PERSONAL SYSTEM 2, 6P, 2BTN, LOGITECH, SAW34
2	9U174	DUAL IN-LINE MEMORY MODULE, 512, 266M, 64X72, 8K, 184, 1U
2	4W941	ASSEMBLY, CABLE, AUXILIARY, POWER, HDD
1	8W522	KIT, CABLE, INTERFACE, IDE (INTEGRATED DRIVE ELECTRONICS), REDUNDANT ARRAY OF INTEGRATED/ INEXPENSIVE DRIVES/DISKS
1	N0804	HARD DRIVE, 80GB, I, 7.2K, 80G/P, SEAGATE-ALPINE
1	N0804	HARD DRIVE, 80GB, I, 7.2K, 80G/P, SEAGATE-ALPINE
1	C0132	OVERPACK KIT, MICROSOFT WINDOWS SERVER 2003 STANDARD EDITION, ENGLAND/ENGLISH, WORLD WIDE
1	J1679	CARD (CIRCUIT), NETWORK, ETHERNET, PRO1000, DUAL
1	0X096	KIT, CABLE, INTERFACE, POWER, DORADO/ATHENS/TUALATIN/ALMODOR, PE650
1	H1483	PROCESSOR, 80532, 2.4G, 512K, 533, SOCKET N, DECISION ONE
1	6878T	CORD, POWER, 125V, 10FT, SJT, UNSHIELDED
1	F0076	KIT, DOCUMENTATION ON COMPACT DISK, DOCUMENT OBJECT MODEL, V3.5, WORLD WIDE
1	9K646	CARD (CIRCUIT), CONTROLLER, IDE (INTEGRATED DRIVE ELECTRONICS), LSI LOGIC, ATA100/4CH

[B]Have you had any hardware problems?
Is it hard to setup the RAID? (I need BIG help on this) I've never setup a RAID on linux before.[/B]

---

### Post by wonk-o-matic on 2007-03-21
Google on /etc/raidtab and mkraid.  If there are already filesystems on the disks, check out the -f option.

---


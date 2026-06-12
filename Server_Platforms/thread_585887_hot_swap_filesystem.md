---
title: "hot swap filesystem?"
date: 2007-10-21
forum: Server Platforms
---

### Post by XeroxGUI on 2007-10-21
Okay, here goes:

I have a server and a dream. 

The server has 2 SCSI drives set up in BIOS raid 1, both 40 GB in size (completely identical), both with independant controllers. 

The dream: if the filesystem(/ /swap /proc) drive goes bad when the RAID 1 has been perfect, can I yank the bad drive(unmounting if at all possible) without takin' her down? B/C I know from $rm -rf / ing a VM Ubuntu that most of the stuff stays in memory, and was wondering if some open-source software lets me hotplug the filesystem when both RAID drives are the same.

(Call me stupid, but if there is no such thing, I have some inventing to do, now dont't I!)

Does anyone know of such a thing??:lolflag:

---

### Post by HermanAB on 2007-10-21
To that, you need hot swap SCSI drives.  Kinda expensive though.

Cheers,

H.

---

### Post by XeroxGUI on 2007-10-22
wow, ok I have the hardware just need the soft.. or should I just yank this sucker now to test it...

---

### Post by HermanAB on 2007-10-22
No... Ordinary SCSI is NOT hot swappable.  You will crash your computer and may damage the drives if you just go and yank them if it is the El'Cheapo type.

---

### Post by XeroxGUI on 2007-10-30
The SCSI it uses has a "SATA-like" connector, e. g. it is flat, not just rows of pins. I tested 'er out by just pulling one out, waiting, testing the filesystem, then after re-inserting and remounting I did the same with the other and it worked fine. 

Please note that the BIOS of the server was the catch: set to RAID 1 with hotspare.

------------------------------------------------------------------------------------------
EDIT:
Hee hee, I just put the drives both to automount in /etc/fstab, so now the machine treats hot-swapping just as good as windoze 2k3. 

Just one step closer to Linux being the no questions asked preferred Server, EVEN TO WINDOZE CLIENTS!!

---

### Post by HermanAB on 2007-10-30
Uhmm, unless you have a lot of money, it is not a good idea to hot-swap equipment that was not designed to do that...

---

### Post by jbardin on 2007-11-01
if the drive is scsi, with sata connectors, that means it's a Serial Attached SCSI (SAS). SAS drives are hot swappable. Actually, anything with an SATA connector is hot swappable at the harware level, but not always at at the firmware or driver level. 

The sata specification is designed to accommodate the power spike, and the ground contacts always connect first when plugging in.

---


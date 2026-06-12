---
title: "Trouble Installing Ubuntu Server 9.10"
date: 2010-01-19
forum: Server Platforms
---

### Post by peridian on 2010-01-19
Hi,
 
I've done some hunting around, and apparently my only option is to go and spend money on additional hardware... which I refuse to believe.
 
I have 9.10 iso on disk. Boot up on server (actually an old PC I want to use for server), runs through install process, no problems.
 
Until it says it cannot find the install disk that it has just been installing from....
 
Apparently this has to do with my IDE connected DVD drive. At some stage during the install, it puts some drivers on there that then mean the software cannot see the drive (which is plain daft).
 
There are suggestions on workarounds I've read, one or two I cannot follow, but I found Unetbootin very straight forward.
 
Only to discover that my motherboard does not support boot from USB... which I was surprised at.
 
I cannot believe that it is this problematic to install the software.
 
Is there a tool like nLite for Linux that would allow me to integrate the correct drivers into the install before I burn it to disk?
 
Regards,
Rob.

---

### Post by sanderj on 2010-01-19
Which workarounds have you seen, and what you tried?

BTW: about your old hardware: what's the CPU and the memory?

---

### Post by peridian on 2010-01-20
The rig is this:
 
AMD FX-62 (i.e. it is a 64-bit processor, for which I am using the 64-bit Ubuntu Server)
Foxconn C51XEM2AA (NVidia chipset)
4Gb DDR2 800Mhz (Corsair Dominator)
512Mb HD4350 (Asus EAH Silent)
2x 500Gb RAID1 (Hitachi Deskstar)
Optiarc NEC IDE DVD-RAM
 
All of the workarounds involved boot from USB, which I was finally thwarted by as it was not an option.
 
Is there a way that I could partition the disk itself, put the installer on one partition and install it to another?
 
Rob.

---

### Post by sanderj on 2010-01-20
You should not have problems (or special drivers) for an IDE CD/DVD drive.

Other workarounds:

- try Ubuntu 8.04 LTS and see if that boots & installs OK, or
- turn off ACPI, DMA etc in the Ubuntu boot (F6), or
- take out the harddisk, put it in another machine, install Ubuntu (without proprietary video drivers), put back the hardisk in the original machine

---

### Post by BT1 on 2010-01-20
Sometimes disks can be corrupt and it doesn't use a driver for an install because its on the corrupted part. Try burning one more disk (this is why I use CD-RWs when doing CD installs) and set the burn speed to 1x to ensure it writes well. Also make sure the MD5 matches the .iso before you burn it.

I had an issue with an Ubuntu Desktop disk doing this until I did the above tips and it worked.

I just... doubt its the install not supporting IDE.

Hope it turns out well!

---

### Post by sanderj on 2010-01-20
> **BT1 said:**
> Sometimes disks can be corrupt and it doesn't use a driver for an install because its on the corrupted part. Try burning one more disk (this is why I use CD-RWs when doing CD installs) and set the burn speed to 1x to ensure it writes well. Also make sure the MD5 matches the .iso before you burn it.


Good point!

---

### Post by wojox on 2010-01-20
I also use the [mini cd]("https://help.ubuntu.com/community/Installation/MinimalCD") it's all you'll ever need.

---

### Post by gobbledigook on 2010-01-20
you could check that the jumpers are set on the odd to be slave and hdd to be master?

---

### Post by peridian on 2010-01-20
Hi,
 
Somebody else had suggested the ACPI thing, but I had thought it was in my BIOS, so I didn't think I had that as an option.
 
I tried doing an install with acpi=off ticked, but no difference.
 
The error I get is:
 
[!!] Install the base system
 
Please insert the dsic labeled: 'Ubuntu-Server 9.10 _Karmic_Koala_ = Release amd64 (20091027.2)' in the drive '/cdrom/' and press enter.
 
Media change
 
 
 
Doing disk swapping seems over the top to me, and if I cannot get this version to work, I'm not inclined to use an older one.
 
On the IDE channel, the DVD drive is the master on Channel 0, the HDD is in a RAID on the SATA Channel 0 Master.
 
With regard to checking the disk, where would I get a program to check the MD5 file?
 
Regards,
Rob.

---


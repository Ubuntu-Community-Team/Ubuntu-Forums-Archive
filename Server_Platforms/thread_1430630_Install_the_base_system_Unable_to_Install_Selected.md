---
title: "Install the base system: Unable to Install Selected Kernel Package"
date: 2010-03-15
forum: Server Platforms
---

### Post by L0neRanger on 2010-03-15
I've been trying to install Ubuntu Server on an old server since a  couple of days and have been unsuccessful.

I've google'd a bit but found no solid solution yet to this problem.  Everything goes fine and I'm able to partition my SCSI drives and  everything. After the installation starts unpacking and copying files  this happens.
[IMG]http://harshay.com/doc/install.jpg[/IMG]
I have to mention that I'm installing from a USB drive with the  following added at the end of the normal install options:

```
--install cdrom-detect/try-usb=true
```Version I'm trying to install: Ubuntu 9.10 i386 Server
CPU: AMD Athlon XP 2000+
RAM: DDR 2*256MB
MOBO: ECS K7VTA3 VIA KT266A socket A DDR

I've tried solving this on my own but no luck so far.

---

### Post by cdenley on 2010-03-15
What does virtual console 4 say? (ctrl+alt+f4)

---

### Post by L0neRanger on 2010-03-15
> **cdenley said:**
> What does virtual console 4 say? (ctrl+alt+f4)
The last two lines say something like this:

```
*timestamp* in-target: Setting up linux-headers-generic-pae (2.6.31.14.27) ...
*timestamp* base-installer: error: exiting on error base-installer/kernel/failed-install
```

---

### Post by L0neRanger on 2010-03-16
Installed Ubuntu Server 8.04 LTS without an issue.

Must be some problem with the 9.10.

Issue Solved.

---

### Post by atisss on 2010-10-30
The same problem here with Ubuntu Server 10.10 i386.

```
Oct 29 23:43:00 in-target: (Reading database ...
Oct 29 23:43:00 in-target: 9216 files and directories currently installed.)
Oct 29 23:43:00 in-target: Unpacking linux-headers-2.6.35-22 (from .../linux-headers-2.6.35-22_2.6.35-22.33_all.deb) ...
Oct 29 23:43:12 in-target: Selecting previously deselected package linux-headers-2.6.35-22-generic-pae.
Oct 29 23:43:12 in-target: Unpacking linux-headers-2.6.35-22-generic-pae (from .../linux-headers-2.6.35-22-generic-pae_2.6.35-22.33_i386.deb) ...
Oct 29 23:43:19 in-target: Selecting previously deselected package linux-headers-generic-pae.
Oct 29 23:43:19 in-target: Unpacking linux-headers-generic-pae (from .../linux-headers-generic-pae_2.6.35.22.23_i386.deb) ...
Oct 29 23:43:19 in-target: Setting up linux-headers-2.6.35-22 (2.6.35-22.33) ...
Oct 29 23:43:19 in-target: Setting up linux-headers-2.6.35-22-generic-pae (2.6.35-22.33) ...
Oct 29 23:43:19 in-target: Setting up linux-headers-generic-pae (2.6.35.22.23) ...
Oct 29 23:43:19 base-installer: error: exiting on error base-installer/kernel/failed-install

```

---

### Post by L0neRanger on 2010-10-30
I was able to install Ubuntu Server 10.04 LTS without an issue on the same server without an issue recently.

Are you using the 10.10 daily build? Try installing 10.04 LTS first and see if that works.

---

### Post by atisss on 2010-10-31
No, I downloaded Server CD Image for 10.10 from ubuntu.com

I followed Your advice and tried 10.04.1 (also from ubuntu.com), and got the following error:

```
Failed to determine codename for release
```

The machine I'm playing with has currently set up Ubuntu Server 8.04 and I decided to change some partitioning, because I got my secondary HDD back from warranty, so I wanted to avoid mess with resizing my RAID devices, and set up clean install with degraded RAID on one HDD.

CPU:  AMD Sempron(tm) 2600+
MB: SiS chipset
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0d.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

Partitioning (I did disconnect sda when trying install as it has my current Ubuntu 8.04, and swapped cables so that secondary HDD becomes primary)

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8508b462

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  fd  Linux raid autodetect
/dev/sda2              17       60561   486327712+  fd  Linux raid autodetect
/dev/sda3           60562       60683      979965   82  Linux swap / Solaris
/dev/sda4           60684      121601   489323835   83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1e6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1959    15735636   fd  Linux raid autodetect
/dev/sdb2            1960        2221     2104515   82  Linux swap / Solaris
/dev/sdb3            2222      100128   786437977+  fd  Linux raid autodetect
/dev/sdb4          100129      182401   660857872+  83  Linux

```

Root filesystem was chosen MD device on physical volume /dev/sdb1

---


---
title: "Samba FileServer &amp; use of RAID"
date: 2007-07-08
forum: Server Platforms
---

### Post by 2shanfernando on 2007-07-08
Howdy,

I've setup Feisty as a fileserver (+lots more! damn I love linux!!!) on an old s478 system i had lying around. I've stuck two PCI sata cards in there which have (at the moment) 6x500Gb SATA HDs (SATA-I) attached (total of 8 ports). 

Previously I had a windows 2k3 box with the same HDs, some in RAID-0, this is with the onboard controller for those boards (P5WDH/P5WD2 etc etc) which is just using the ICHR7 controller + the PCI (and PCI-X) cards there. Now however I've got the HDs hooked up as seperate 500Gb drives mounted under various shares in /media/ to 'fake' as if they are from the same drive (using SAMBA to share the /media/Storage/ folder).

I was wondering whether its advisable (forgetting RAID-0 risks) to use RAID on linux and whether SoftRAID or LinuxRAID or FakeRAID is the way to go. I'm a bit confused after reading about employing RAID under linux. I'm not *too* fussed if it takes CPU cycles. This box has a 3Ghz processor and 2Gb of DDR RAM.

This is *not* to boot off or run Ubuntu on (most tutes had this setup), its already happilly chugging away, I just want to have a bigger HD available to throw stuff onto instead of having to split and mount into seperate folders.

My lspci output:

```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to CSA Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:01.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:02.0 RAID bus controller: Silicon Image, Inc. Adaptec AAR-1210SA SATA HostRAID Controller (rev 02)
03:03.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
03:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

Anything else just ask.
Thanks,

---

### Post by kidders on 2007-07-09
Hi there,

> **2shanfernando said:**
> I was wondering whether its advisable (forgetting RAID-0 risks) to use RAID on linux and whether SoftRAID or LinuxRAID or FakeRAID is the way to go.

I'm not sure what the distinction between SoftRAID and LinuxRAID is, but (forgetting RAID-0 risks!), Linux has been running RAID systems for a *very* long time, so there's no reason not to try it. For a simple, cheap solution, I would suggest an array implemented in software. For a variety of reasons, I would very strongly discourage FakeRAID, personally.

Arrays designed for plain old data storage are a doddle to set up, but if your only reason for having one is to shorten your /etc/fstab, I would not suggest doing it ... mostly (but not entirely) for reasons I've ... ehhh ... forgotten!

---

### Post by doogy2004 on 2007-07-09
A software raid is easy to set up during the installation of ubuntu when using the server or alternate disk.  I've been looking for a good tutorial to manage the software raid and doing the following.

Determine the health of the RAID (good disks/bad disks)
Add/remove disks
Recover from a damaged disk
etc.

Finding this with a nice user interface such as a Text User Interface or a GUI would be GREAT.

---

### Post by doogy2004 on 2007-07-09
> **doogy2004 said:**
> A software raid is easy to set up during the installation of ubuntu when using the server or alternate disk.  I've been looking for a good tutorial to manage the software raid and doing the following.

Determine the health of the RAID (good disks/bad disks)
Add/remove disks
Recover from a damaged disk
etc.

Finding this with a nice user interface such as a Text User Interface or a GUI would be GREAT.

DONE, shortly after posting I found EVMS.  This has BOTH a TUI and a GUI.  Check it out [http://evms.sourceforge.net/](http://evms.sourceforge.net/)

---

### Post by 2shanfernando on 2007-07-10
> **doogy2004 said:**
> DONE, shortly after posting I found EVMS.  This has BOTH a TUI and a GUI.  Check it out [http://evms.sourceforge.net/](http://evms.sourceforge.net/)

Kewl! I'll have to try this out. Thanks Doogy2004:-)

---


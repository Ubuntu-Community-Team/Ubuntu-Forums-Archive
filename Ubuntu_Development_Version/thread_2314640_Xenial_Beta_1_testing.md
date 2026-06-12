---
title: "Xenial Beta 1 testing"
date: 2016-02-22
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2016-02-22
For the participating flavors Beta 1 is planned for Thursday the 25th:

[https://lists.ubuntu.com/archives/ubuntu-release/2016-February/003618.html](https://lists.ubuntu.com/archives/ubuntu-release/2016-February/003618.html)

> Dailies disabled and milestone builds in progress for :

Lubuntu
Ubuntu Gnome
Ubuntu Kylin
Ubuntu Mate
Ubuntu Server Cloud
Ubuntu Studio
Xubuntu

So the proposed images are (or soon will be) available here:

[http://iso.qa.ubuntu.com/qatracker/milestones/357/builds](http://iso.qa.ubuntu.com/qatracker/milestones/357/builds)

Depending on the nature of the bugs discovered images may be rebuilt a number of times prior to Thursday. We should also test release upgrades from both Trusty and Wily :)

---

### Post by sudodus on 2016-02-23
There is a [new bug](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1547793) causing Ubiquity to crash in laptops with batteries. There is already a lot of activities around this bug. Several bug reports are linked to it and Martin Pitt is assigned to solve it.

There is a [new bug](http://launchpad.net/bugs/1548477) causing 'man' to fall back to using the primitive 'more'. This bug report needs confirmation 'affects me too', and it is not clear yet, where the bug is located.

---

### Post by sudodus on 2016-02-23
Testing Lubuntu Xenial beta1 desktop i386:

[http://iso.qa.ubuntu.com/qatracker/milestones/357/builds/113130/testcases/1300/results/](http://iso.qa.ubuntu.com/qatracker/milestones/357/builds/113130/testcases/1300/results/)

Installing Lubuntu in a laptop with the battery unplugged worked, but the way to set locale and keyboard is changed (and the keyboard setting did not 'survive'). I suspect that this new behaviour/bug affects other flavours of Ubuntu too.

Should the keyboard settings problem be reported as a new bug?

Please try to install a non-English language and look for this new behaviour/bug :-)

---

### Post by sammiev on 2016-02-23
I tried Xenial Xubuntu 64 on the 21st and the installer in broken.

Hope it works for the 25th.

---

### Post by PaulW2U on 2016-02-23
> **sudodus said:**
> There is a [new bug](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1547793) causing Ubiquity to crash in laptops with batteries. There is already a lot of activities around this bug. Several bug reports are linked to it and Martin Pitt is assigned to solve it.
A fix was released earlier today and images are being rebuilt. I've just tested Xubuntu on two laptops but Ubiquity still fails to start unless the battery is removed.
> **sammiev said:**
> I tried Xenial Xubuntu 64 on the 21st and the installer in broken.
Was that on a laptop sammiev? I successfully installed Xubuntu last night (22nd) by removing the laptop battery.

---

### Post by MikeMecanic on 2016-02-23
Try L (20160222) alongside Win10 (x64) and didn&#8217;t get the Keyboard bug (engUS):  K remains the best installer.

EDIT: Oups!  USC seems to be gone in all flavours, plus SDC is not on-board K and X.  Startup Disk Creator works everywhere now.


```
sudo apt-get install software-center
```

---

### Post by sammiev on 2016-02-23
> **PaulW2U said:**
> 
Was that on a laptop sammiev? I successfully installed Xubuntu last night (22nd) by removing the laptop battery.

Yes it was on a laptop. I will try it again in a few days as I installed KDE 16.04 after that happen.

---

### Post by MikeMecanic on 2016-02-23
> **sammiev said:**
> I tried Xenial Xubuntu 64 on the 21st and the installer in broken.

Hope it works for the 25th.

Just made a perfect fresh install: auto-resize.

---

### Post by MikeMecanic on 2016-02-23
Its not the first time I'm getting that error at the end?

From: 

```
$ journalctl
```
 
 
 [HTML]Feb 23 15:57:40 g kernel: [drm:intel_opregion_init [i915]] *ERROR* No ACPI video bus found

 Feb 23 15:57:40 g kernel: [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
 Feb 23 15:57:40 g kernel: [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
 Feb 23 15:57:40 g kernel: usb 1-1: new high-speed USB device number 2 using ehci-pci
 Feb 23 15:57:40 g kernel: usb 2-1: new high-speed USB device number 2 using ehci-pci
 Feb 23 15:57:40 g kernel: [drm] GMBUS [i915 gmbus dpc] timed out, falling back to bit banging on pin 4
 Feb 23 15:57:40 g kernel: ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 Feb 23 15:57:40 g kernel: ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

 Feb 23 15:57:40 g kernel: ata1.00: ATA-8: ST3750528AS, HP40, max UDMA/100
 Feb 23 15:57:40 g kernel: ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
 Feb 23 15:57:40 g kernel: ata1.00: configured for UDMA/100
 Feb 23 15:57:40 g kernel: scsi 0:0:0:0: Direct-Access     ATA      ST3750528AS      HP40 PQ: 0 ANSI: 5
 Feb 23 15:57:40 g kernel: sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
 Feb 23 15:57:40 g kernel: sd 0:0:0:0: Attached scsi generic sg0 type 0
 Feb 23 15:57:40 g kernel: sd 0:0:0:0: [sda] Write Protect is off
 Feb 23 15:57:40 g kernel: sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
 Feb 23 15:57:40 g kernel: sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 Feb 23 15:57:40 g kernel: ata3.00: ATAPI: hp       CDDVDW TS-T633P, H1B0, max UDMA/100
 Feb 23 15:57:40 g kernel: usb 1-1: New USB device found, idVendor=8087, idProduct=0024
 Feb 23 15:57:40 g kernel: usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
 Feb 23 15:57:40 g kernel: hub 1-1:1.0: USB hub found
 Feb 23 15:57:40 g kernel: hub 1-1:1.0: 6 ports detected
 Feb 23 15:57:40 g kernel: ata3.00: configured for UDMA/100
 Feb 23 15:57:40 g kernel: scsi 2:0:0:0: CD-ROM            hp       CDDVDW TS-T633P  H1B0 PQ: 0 ANSI: 5
 Feb 23 15:57:40 g kernel: usb 2-1: New USB device found, idVendor=8087, idProduct=0024
 Feb 23 15:57:40 g kernel: usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
 Feb 23 15:57:40 g kernel: hub 2-1:1.0: USB hub found
 Feb 23 15:57:40 g kernel: hub 2-1:1.0: 8 ports detected
 Feb 23 15:57:40 g kernel:  sda: sda1 sda2 sda3 < sda5 sda6 >
 Feb 23 15:57:40 g kernel: sr 2:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
 Feb 23 15:57:40 g kernel: cdrom: Uniform CD-ROM driver Revision: 3.20
 Feb 23 15:57:40 g kernel: sr 2:0:0:0: Attached scsi CD-ROM sr0
 Feb 23 15:57:40 g kernel: sr 2:0:0:0: Attached scsi generic sg1 type 5
 Feb 23 15:57:40 g kernel: sd 0:0:0:0: [sda] Attached SCSI disk
 Feb 23 15:57:40 g kernel: fbcon: inteldrmfb (fb0) is primary device
 Feb 23 15:57:40 g kernel: Console: switching to colour frame buffer device 240x67
 Feb 23 15:57:40 g kernel: i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
 Feb 23 15:57:40 g kernel: usb 1-1.3: new full-speed USB device number 3 using ehci-pci
 Feb 23 15:57:40 g kernel: usb 2-1.2: new high-speed USB device number 3 using ehci-pci
 Feb 23 15:57:40 g kernel: usb 1-1.3: New USB device found, idVendor=0408, idProduct=3008
 Feb 23 15:57:40 g kernel: usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=4
 Feb 23 15:57:40 g kernel: usb 1-1.3: Product: OpticalTouchScreen
 Feb 23 15:57:40 g kernel: usb 1-1.3: Manufacturer: Quanta
 Feb 23 15:57:40 g kernel: usb 1-1.3: SerialNumber: 0000
 Feb 23 15:57:40 g kernel: hidraw: raw HID events driver (C) Jiri Kosina
 Feb 23 15:57:40 g kernel: usbcore: registered new interface driver usbhid
 Feb 23 15:57:40 g kernel: usbhid: USB HID core driver
 Feb 23 15:57:40 g kernel: tsc: Refined TSC clocksource calibration: 3092.972 MHz
 Feb 23 15:57:40 g kernel: clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2c955856658, max_idle_ns: 440795256416 ns
 Feb 23 15:57:40 g kernel: usb 2-1.2: New USB device found, idVendor=046d, idProduct=0826
 Feb 23 15:57:40 g kernel: usb 2-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=1
 Feb 23 15:57:40 g kernel: usb 2-1.2: Product: HD Webcam C525
 Feb 23 15:57:40 g kernel: usb 2-1.2: SerialNumber: 43032BD0
 Feb 23 15:57:40 g kernel: usb 2-1.5: new full-speed USB device number 4 using ehci-pci
 Feb 23 15:57:40 g kernel: EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
 Feb 23 15:57:40 g kernel: usb 2-1.5: New USB device found, idVendor=03f0, idProduct=d407
 Feb 23 15:57:40 g kernel: usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
 Feb 23 15:57:40 g kernel: usb 2-1.5: Product: HP Link-5 Micro Receiver
 Feb 23 15:57:40 g kernel: usb 2-1.5: Manufacturer: HP
 Feb 23 15:57:40 g kernel: input: HP HP Link-5 Micro Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/0003:03F0:D407.0002/input/
 input3
 Feb 23 15:57:40 g kernel: hid-generic 0003:03F0:D407.0002: input,hidraw0: USB HID v1.11 Keyboard [HP HP Link-5 Micro Receiver] on usb-0000:00:1d.0-1
 .5/input0
 Feb 23 15:57:40 g kernel: input: HP HP Link-5 Micro Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/0003:03F0:D407.0003/input/
 input4
 Feb 23 15:57:40 g kernel: usb 2-1.6: new high-speed USB device number 5 using ehci-pci
 Feb 23 15:57:40 g kernel: hid-generic 0003:03F0:D407.0003: input,hiddev0,hidraw1: USB HID v1.11 Mouse [HP HP Link-5 Micro Receiver] on usb-0000:00:1
 d.0-1.5/input1
 Feb 23 15:57:40 g kernel: usb 2-1.6: New USB device found, idVendor=13fe, idProduct=4200
 Feb 23 15:57:40 g kernel: usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber
...
[/HTML]

---

### Post by Irihapeti on 2016-02-23
Xubuntu Beta 1 installed uneventfully on my desktop PC. No such luck with the EeePC 900 netbook - the Ubiquity battery bug is still active here. At least, I know not just to write it off to shortage of memory.

---

### Post by PaulW2U on 2016-02-24
> **Irihapeti said:**
> Xubuntu Beta 1 installed uneventfully on my desktop PC. No such luck with the EeePC 900 netbook - the Ubiquity battery bug is still active here. At least, I know not just to write it off to shortage of memory.
Eavesdropping on various IRC channels throughout the day it seems that the problem has now been solved and fixes are working their way through the release process. I think there were several bugs that seemed to confuse both bug reporters and developers.

Expect at least one respin for each of the Beta 1 participating flavours before release tomorrow.

---

### Post by sudodus on 2016-02-24
> **PaulW2U said:**
> Eavesdropping on various IRC channels throughout the day it seems that the problem has now been solved and fixes are working their way through the release process. I think there were several bugs that seemed to confuse both bug reporters and developers.

Expect at least one respin for each of the Beta 1 participating flavours before release tomorrow.

Yes, you are right about the great confusion. I know people have been working hard, I think particularly Martin Pitt. I had hoped that the versions released today would have solved the ubiquity bug(s). Anyway, I'm eagerly waiting for the next batch of xenial beta 1 iso files :-P

---

### Post by PaulW2U on 2016-02-24
> **sudodus said:**
> I had hoped that the versions released today would have solved the ubiquity bug(s). Anyway, I'm eagerly waiting for the next batch of xenial beta 1 iso files :-P
Updated ISOs for Xubuntu are now available. Confirmed battery bug(s) fixed. Other flavours will be ready shortly if they aren't already.

---

### Post by Irihapeti on 2016-02-24
Currently installing Xubuntu on the EeePC. A bit slow - to be expected with only 1 GB of RAM - but it's working so far!

---

### Post by sammiev on 2016-02-24
> **PaulW2U said:**
> Updated ISOs for Xubuntu are now available. Confirmed battery bug(s) fixed. Other flavours will be ready shortly if they aren't already.

Thanks Paul,

I will give it a go this evening. :)

---

### Post by Irihapeti on 2016-02-24
Successfully installed on EeePC. Yay!

BTW, I don't recommend doing it this way for netbooks of this kind - too slow. Mini ISO would be less painful.


Have to go out shortly, so won't be able to test on the desktop PC for several hours.

---

### Post by sudodus on 2016-02-24
Lubuntu i386 works too :-)

But I have a problem with Lubuntu amd64. Ubiquity starts, but it ***fails to create swap*** (in a used disk). There is evidence in the [bug report](https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/990744) that a clean drive should work - and a hint how to improve creating the swap (see comment #15). Do you remember it *irihapeti*?

...

Yes, a clean drive worked (I wiped the SSD) - It seems the amd64 version is more picky than the i386 version.

---

### Post by sammiev on 2016-02-24
Xubuntu 64 installed on a laptop with no issues along side of Ubuntu-Gnome 64.

---

### Post by Irihapeti on 2016-02-24
> **sudodus said:**
> Lubuntu i386 works too :-)

But I have a problem with Lubuntu amd64. Ubiquity starts, but it ***fails to create swap*** (in a used disk). There is evidence in the [bug report](https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/990744) that a clean drive should work - and a hint how to improve creating the swap (see comment #15). Do you remember it *irihapeti*?

...

Yes, a clean drive worked (I wiped the SSD) - It seems the amd64 version is more picky than the i386 version.

I saw the report - I'm subscribed to it. But I'm not using 64 bit versions, so I can't offer any useful input on this one. It appeared to use the existing swap OK with the 32 bit install.

---

### Post by kansasnoob on 2016-02-24
> **sudodus said:**
> Lubuntu i386 works too :-)

But I have a problem with Lubuntu amd64. Ubiquity starts, but it ***fails to create swap*** (in a used disk). There is evidence in the [bug report](https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/990744) that a clean drive should work - and a hint how to improve creating the swap (see comment #15). Do you remember it *irihapeti*?

...

Yes, a clean drive worked (I wiped the SSD) - It seems the amd64 version is more picky than the i386 version.

That's one of those old bugs that jumps up and bites me every once in a while. Then if I reboot the live image and try again it works OK.

---

### Post by kansasnoob on 2016-02-24
These two bugs have driven me buggy:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1549067](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1549067)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1359689](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1359689)

---

### Post by sudodus on 2016-02-24
Bug #1359689 affects me too. It prevents prompting for the cryptsetup passphrase (for encrypted disk). I think it is related to some other bug reports with plymouth - there is only a blue screen in Lubuntu, no dots, no texts, that help users understand what happens. But standard Ubuntu is not affected, so I think it is something specific for Ubuntu Gnome and Lubuntu.

I have not touched the release-upgrade test cases so I don't know anything about your other bug.

---

### Post by MikeMecanic on 2016-02-26
Ubuntu is not in the Testing tracker list and *source.list.save* still showing Alpha release:


# deb cdrom:[Ubuntu16.04 LTS _Xenial Xerus_ - Alpha amd64 (20160226)]/ xenial main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted #Added by software-properties


There’s only good news here,


Just made a fresh install and got only 2 bugs that didn't compromise the installation


1-  As in Kylin (20160222), there was no clock during installation (time was okay after rebooting)
2-  Was not ask to remove media at the end (directly in the boot sequence, no incidence)


There is a third bug (post-installation) related to Gnome Software that seems to be empty: I’m not able to load Google Chrome and my main browser Opera37.x. Software does not recognize the.deb files that I have on separate pendrive.  


So, loading Ubuntu Software Center is the only solution.  Same apply for Network Tools that is not there.   For the other apps, I’m using the terminal.  


If K is the best installer, Ubuntu is the fastest one (takes about 5-6 minutes).


Enabling Proposed before running Software Updater: 165Mb patch only + Kernel 4.5 rc5
```


ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.4.0-7-generic                  4.4.0-7.22                                 amd64       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.4.0-8-generic                  4.4.0-8.23                                 amd64       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii [COLOR=#ff3333]**linux-image**[/COLOR]-4.5.0-040500rc5-generic          4.5.0-040500rc5.201602201730               amd64       Linuxkernel image for version 4.5.0 on 64 bit x86 SMP
ii [COLOR=#ff3333]**linux-image**[/COLOR]-extra-4.4.0-7-generic            4.4.0-7.22                                 amd64       Linux kernel extra modulesfor version 4.4.0 on 64 bit x86 SMP
ii [COLOR=#ff3333]**linux-image**[/COLOR]-extra-4.4.0-8-generic            4.4.0-8.23                                 amd64       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii [COLOR=#ff3333]**linux-image**[/COLOR]-generic                          4.4.0.8.9                                  amd64       Generic Linux kernel image

```

At 5 weeks from the freeze release, my overall appreciation is that there are more bugs fixed then anything else.

---


---
title: "Portable installed system that boots in UEFI as well as in BIOS mode"
date: 2014-03-27
forum: Tutorials
---

### Post by sudodus on 2014-03-27
[SIZE=4]Edit: **Stable portable systems**[/SIZE]

If you want a stable portable system, that boots in UEFI mode as well as  BIOS/CSM mode, and in 64-bit as well as 32-bit computers, you can try

[One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682"). 

If you want a pendrive with a live **and** an installed system, that works in UEFI and BIOS mode, you can try

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506") and

[Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

I have developed a system from Ubuntu Xenial amd64 (I call it gamma because it is beyond beta), and I was able to simplify the method to make a stable installed system for UEFI and BIOS mode. See this link

[Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13468260#post13468260)

with a description how to make it 'from scratch' plus a link to where I have uploaded compressed image files plus a small script to fix the GPT after cloning.

[Two updated 'text-mini' compressed image files are uploaded 2016-05-27](http://ubuntuforums.org/showthread.php?t=2213631&page=8&p=13494760#post13494760)

There is a new stable alternative with Lubuntu 18.04.1 LTS. It provides live, persistent live and installed systems for one single USB pendrive (size at least 16 GB).

See more details at [post #187](https://ubuntuforums.org/showthread.php?t=2213631&p=13836574#post13836574) and the following link to an Ubuntu help page,

[help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1)

[HR][/HR]
Get and overview at the following Ubuntu help wiki page: [**help.ubuntu.com/community/Installation/UEFI-and-BIOS**](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[HR][/HR]
[size=3]There is a torrent file that you can use to build your own custom operating system[/size]

The dd_text_16.04-UEFI-n-BIOS compressed image file was made up to date, and a torrent file was uploaded in January 2017. It can be used, if you want to start with a light-weight system and install your own selection of program packages - desktop packages, server packages and application packages.

[dd_text_16.04-UEFI-n-BIOS_2017-01-15_intel-4-pendrive-7.8GB.img.xz.torrent](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS?action=AttachFile&do=view&target=dd_text_16.04-UEFI-n-BIOS_2017-01-15_intel-4-pendrive-7.8GB.img.xz.torrent)

Use ***mkusb*** to install from the downloaded compressed image file to a USB pendrive, a memory card, or maybe an external SSD or HDD.

See details at this link: [Installation/UEFI-and-BIOS/torrent](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/torrent)

[HR][/HR]
[size=3]Detailed description of the original installed system[/size]

I wanted an installed system as a good alternative to a persistent live system that boots new computers with and without UEFI. So I made one, which is described in this link

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

But I have tested it in only two computers, my Toshiba laptop, where I made it, and in my son's HP Elitebook laptop, so I don't know how portable it is.

The method is described in detail, and there is a compressed image of an Ubuntu 12.04.4 system available at

[http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

I think the ***method*** is at least as important to test as the compressed image, if and how it works in other computers.

So now, that we have finished testing beta 2, maybe there is time for you to try the method and make an UEFI-and-BIOS pendrive with your favourite flavour of Ubuntu Trusty beta 2.

***Not stable enough to survive certain updates***

 I  expected that this 'Portable installed system that boots in UEFI as  well as in BIOS mode' could be installed into a USB pendrive as a good   alternative to a persistent live system, possible to update and upgrade   without limits. But unfortunately a current update involving a new   kernel and updating grub will make it fail to boot. So this system is not stable enough to survive certain updates. It is good only as an illustration of a method to make a bootable drive in UEFI as well as BIOS mode.

***Links***

It might be a good idea to try various systems and methods before deciding what to install. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") 

The following links contain general information 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by ventrical on 2014-03-27
I was just experimenting with a ready-made saucy pendrive install and it works just fine on UEFI and non-UEFI.

```


ventrical@ventrical-MS-7798:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
06:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2014-03-27
OK .. I think I am not  on the same topic here. I just merely <enabled> UEFI in BIOS and booted to an already existing install from a pendrive. I tried some of your code  from the link and it does not report that I am in UEFI mode.

---

### Post by sudodus on 2014-03-28
> **ventrical said:**
> OK .. I think I am not  on the same topic here. I just merely <enabled> UEFI in BIOS and booted to an already existing install from a pendrive. I tried some of your code  from the link and it does not report that I am in UEFI mode.

An Ubuntu desktop 64-bit install DVD or USB drive can boot into both  systems (UEFI - grub, BIOS - syslinux), and with my method an  installed system is tweaked to boot via grub in both UEFI and BIOS by  activating different paths to booting.

In my Toshiba, it is not possible to boot a system made for BIOS, when I enable UEFI. And it is not possible to boot a system made for UEFI, when I disable UEFI by selecting 'CSM', which means enabling old style BIOS mode.

> 
UEFI   Compatibility Support Module (CSM) provides compatibility support for traditional legacy BIOS.  This allows allows the booting an operating system that requires a traditional option ROM support, such as BIOS Int 10h video calls.


I think that the UEFI systems are not standardized, but vary a lot, which can make the experience different between computers.

-o-

The system, that you can expand from

[http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu-UEFI-n-BIOS-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu-UEFI-n-BIOS-7.8GB.img.xz)

boots clearly differently for me when I set the computer in UEFI mode and BIOS (CSM) mode. The grub menu is rendered differently, so it is easy for me to identify. But the same installed Ubuntu system is running after grub.

---

### Post by sudodus on 2014-04-14
This UEFI-n-BIOS booter was developed in my Toshiba

[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

and today I tested it in a Dell  Latitude E5430 non-vPro with the following specs according to lshw
```

computer
    description: Laptop
    product: Latitude E5430 non-vPro (Latitude E5430 non-vPro)
    vendor: Winbond Electronics
    version: 01
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=laptop sku=Latitude E5430 non-vPro uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0MYF02
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A11
          date: 05/20/2013
          size: 64KiB
          capacity: 13MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect socketedrom edd int13flop
py1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer a
cpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-3120M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 53
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-3120M CPU @ 2.50GHz
          slot: SOCKET 0
          size: 1200MHz
:
          capacity: 2500MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx f16c lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
...
     *-memory
          description: System Memory
          physical id: 46
          slot: System board or motherboard
          size: 2GiB
...

```

Pressing F12 at boot, I arrived at a boot menu, with one entry to boot from the USB pendrive in BIOS (legacy) mode and another entry to boot the pendrive in UEFI mode (along with all the other entries including booting Windows).

And the computer could run this portable installed system in UEFI as well as in BIOS mode.

*Edit*: But it does not run in UEFI secure mode, not even in the Toshiba, where it was developed.

---

### Post by oldfred on 2014-04-14
I have seen users with many different options.

A few have no UEFI/BIOS options, it tries UEFI and if no efi partition tries BIOS.
Some have settings that are UEFI or BIOS, but you can set either or both. 
Some have to have UEFI/BIOS setting to exact mode they want to use to boot and have to turn on/off UEFI and/or turn on/off BIOS.

I think all have to turn off secure boot to get any other options as BIOS is not secure boot.

For those that can boot either way the one time boot key if available should show both options.

With a new Dell and Haswell processor, the suggestion was to turn on BIOS mode but boot in UEFI mode to fix some bug in the Haswell/Intel chip & software. Do not know how that would be related, thought UEFI & BIOS were totally separate?

---

### Post by sudodus on 2015-04-01
***Not stable enough to survive certain updates***

 I  expected that this 'Portable installed system that boots in UEFI as well as in BIOS mode' could be installed into a USB pendrive as a good  alternative to a persistent live system, possible to update and upgrade  without limits. But unfortunately a current update involving a new  kernel and updating grub will make it fail to boot. So this system is not stable enough to survive certain updates. It is good only as an illustration of a method to make a bootable drive in UEFI as well as BIOS mode.

***A stable portable system***

If you want a stable portable system, that boots in UEFI mode as well as BIOS/CSM mode, and in 64-bit as well as 32-bit computers, you can try [One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682") 


***Links***

It might be a good idea to try various systems and methods before deciding what to install. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") 

The following links contain general information 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by sudodus on 2015-04-11
[SIZE=4]A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode[/SIZE]


***1. Current system, seems very stable so far***

The current system contains a live system and an installed system, and both work in UEFI and BIOS mode. The compressed image file

**dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz**

at

[http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

is created like this (only a crude description so far)


***A. Create an MSDOS partition table***

Use gparted to get a partition table with the following partitions (or similar if you wish, for example also a casper-rw partition),

listed by fdisk -lu

```
Disk /dev/sdd: 15.7 GB, 15693664256 bytes
64 heads, 32 sectors/track, 14966 cylinders, total 30651688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063103

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048     2623487     1310720    b  W95 FAT32
/dev/sdd2         2625534    19400703     8387585    5  Extended
/dev/sdd5         2625536    18350145     7862305   83  Linux
/dev/sdd6        18352128    19400703      524288   82  Linux swap / Solaris

```
listed by parted -l

```
Model: SanDisk Extreme (scsi)
Disk /dev/sdd: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1343MB  1342MB  primary   fat32           boot
 2      1344MB  9933MB  8589MB  extended
 5      1344MB  9395MB  8051MB  logical   ext4
 6      9396MB  9933MB  537MB   logical   linux-swap(v1)

```
listed by lsblk

```
NAME        FSTYPE  LABEL               MOUNTPOINT
sdd                                               
&#9500;&#9472;sdd1      vfat    usb-live            /media/usb-live
&#9500;&#9472;sdd2
&#9500;&#9472;sdd5      ext4    usb-installed       /media/usb-installed
&#9492;&#9472;sdd6      swap

```

***B. Use the Startup Disk Creator alias usb-creator-gtk***

Install Ubuntu from the file

** ubuntu-14.04.2-desktop-amd64.iso**

into partition 1 of a pendrive with at least 16 GB.


***C. Boot from the pendrive in UEFI mode and install Ubuntu***

Install Ubuntu into partition 5 of the same pendrive. Install the
bootloader into partition 5 (not into the head of the drive).

Tweak the boot configuration files

```
.../usb-live/syslinux/txt.cfg
.../usb-live/boot/grub/grub.cfg
.../usb-installed/boot/grub/grub.cfg

```
according to the files that you find after installing with mkusb from

** dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz**

to a pendrive.


***D. The pendrive uses the boot system of the Ubuntu installer ***

Notice that this system is not like an ordinary installed system. It has an MSDOS partition table (not a GPT). It uses the boot system of the Ubuntu installer instead of what is normally created by installing in UEFI mode.

This method seems stable when used in a USB pendrive. It is tested in two different laptops, a Toshiba Satellite and an HP Elitebook. The previous installed UEFI and BIOS pendrive system did not survive such adventures.

It is also tested in an eSATA SSD drive, where it also works when installed according to the description above. But it might not work to flash the pendrive image directly to the SSD drive.

[HR][/HR]

***2. Tweak the system***

***A. Decrease wear for a pendrive***

Add the mount option noatime in /etc/fstab

```
# / was on /dev/sdb3 during installation
UUID=4c518694-d97c-4910-bb7b-eeb6a6b73874  /  ext4  noatime,errors=remount-ro 0  1

```
Do not copy this line. Add 'noatime' to your own line.

It is also possible to remove the swap partition and the swap entry in /etc/fstab in order to avoid wear due to swapping.


***B. Move swap and grow root partition***

Move the swap partition and grow the root partition to use the whole drive. See this link

[http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf](http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf)


***C. Login and password for the system to download***

The system that is installed from the compressed image file

[http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz)

has the following user and password

[B]user:     guru
password: changeme

[/B][HR][/HR][B]
*Edit 1: *[/B]It is straight-forward to install from the compressed image file with [***mkusb*** or ***mkusb-nox***]("https://help.ubuntu.com/community/mkusb")[B].
[I]
Edit 2:[/I][/B] It should be mentioned that ***the shift key or any other key should be held down  while booting into BIOS mode***, otherwise we do not get the menu with the  the installed 'ubuntu' entry.

***Edit 3:*** See also [Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

---

### Post by ventrical on 2015-04-13
> **sudodus said:**
> [SIZE=4]A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode[/SIZE]


***1. Current system, seems very stable so far***

The current system contains a live system and an installed system, and both work in UEFI and BIOS mode. The compressed image file

**dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz**

at

[http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)


So is the file,

[B]ubuntu-14.04.2-desktop-amd64.iso

[/B]compressed within the img.xz file? I don't understand this. Why can't we just download the .iso file?

> 

is created like this (only a crude description so far)


***A. Create an MSDOS partition table***

Use gparted to get a partition table with the following partitions (or similar if you wish, for example also a casper-rw partition),

listed by fdisk -lu

```
Disk /dev/sdd: 15.7 GB, 15693664256 bytes
64 heads, 32 sectors/track, 14966 cylinders, total 30651688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063103

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048     2623487     1310720    b  W95 FAT32
/dev/sdd2         2625534    19400703     8387585    5  Extended
/dev/sdd5         2625536    18350145     7862305   83  Linux
/dev/sdd6        18352128    19400703      524288   82  Linux swap / Solaris

```
listed by parted -l

```
Model: SanDisk Extreme (scsi)
Disk /dev/sdd: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1343MB  1342MB  primary   fat32           boot
 2      1344MB  9933MB  8589MB  extended
 5      1344MB  9395MB  8051MB  logical   ext4
 6      9396MB  9933MB  537MB   logical   linux-swap(v1)

```
listed by lsblk

```
NAME        FSTYPE  LABEL               MOUNTPOINT
sdd                                               
&#9500;&#9472;sdd1      vfat    usb-live            /media/usb-live
&#9500;&#9472;sdd2
&#9500;&#9472;sdd5      ext4    usb-installed       /media/usb-installed
&#9492;&#9472;sdd6      swap

```


So you would need us to create all of this on the usb using gparted before proceeding?

 
> 
***B. Use the Startup Disk Creator alias usb-creator-gtk***

Install Ubuntu from the file

** ubuntu-14.04.2-desktop-amd64.iso**

into partition 1 of a pendrive with at least 16 GB.


***C. Boot from the pendrive in UEFI mode and install Ubuntu***

Install Ubuntu into partition 5 of the same pendrive. Install the
bootloader into partition 5 (not into the head of the drive).

Tweak the boot configuration files

```
.../usb-live/syslinux/txt.cfg
.../usb-live/boot/grub/grub.cfg
.../usb-installed/boot/grub/grub.cfg

```
according to the files that you find after installing with mkusb from

** dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz**

to a pendrive.


***D. The pendrive uses the boot system of the Ubuntu installer ***

Notice that this system is not like an ordinary installed system. It has an MSDOS partition table (not a GPT). It uses the boot system of the Ubuntu installer instead of what is normally created by installing in UEFI mode.

This method seems stable when used in a USB pendrive. It is tested in two different laptops, a Toshiba Satellite and an HP Elitebook. The previous installed UEFI and BIOS pendrive system did not survive such adventures.

It is also tested in an eSATA SSD drive, where it also works when installed according to the description above. But it might not work to flash the pendrive image directly to the SSD drive.

[HR][/HR]
***2. Tweak the system***

***A. Decrease wear for a pendrive***

Add the mount option noatime in /etc/fstab

```
# / was on /dev/sdb3 during installation
UUID=4c518694-d97c-4910-bb7b-eeb6a6b73874  /  ext4  noatime,errors=remount-ro 0  1

```
Do not copy this line. Add 'noatime' to your own line.

It is also possible to remove the swap partition and the swap entry in /etc/fstab in order to avoid wear due to swapping.


***B. Move swap and grow root partition***

Move the swap partition and grow the root partition to use the whole drive. See this link

[http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf](http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf)


***C. Login and password for the system to download***

The system that is installed from the compressed image file

[http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz)

has the following user and password

[B]user:     guru
password: changeme[/B]

It must just be me but don't understand why the 'compressed image file'  is used when we only need the .iso file.  I am confused that I have to use compressed image file and it is not detailed out on how to extract:

ubuntu-14.04.2-desktop-amd64.iso

 from the image file. So I am immediately deterred from trying this process because of my lack of understanding of the *instructions* you are suggesting to attempt this experiment.

Regards..

---

### Post by sudodus on 2015-04-14
> **ventrical said:**
> So is the file,

[B]ubuntu-14.04.2-desktop-amd64.iso

[/B]compressed within the img.xz file? I don't understand this. Why can't we just download the .iso file?

So you would need us to create all of this on the usb using gparted before proceeding?

It does not do all I want it to do directly from the iso file.
> 
It must just be me but don't understand why the 'compressed image file'  is used when we only need the .iso file.  I am confused that I have to use compressed image file and it is not detailed out on how to extract:

ubuntu-14.04.2-desktop-amd64.iso

 from the image file. So I am immediately deterred from trying this process because of my lack of understanding of the *instructions* you are suggesting to attempt this experiment.

Regards..

Sorry, I have not explained well enough. Either you create it or you use the compressed image file :-)

A. Create it to learn what I have been doing.

B. Install from the compressed image file, if you want to get it quickly and just test if/how it works for you. *Edit*: In this case, simply install with mkusb.

---

### Post by ventrical on 2015-04-14
Ok... clear to me now. My only problem is that I am trying to conserve bandwidth until my next billing cycle. I am near or over my limit atm. Sorry .. but that is politics in Canada... one moment .. I will check status..

I'll download from alternate source, time permitting.

Thanks for your patience.

Regards..

---

### Post by sudodus on 2015-04-14
Well it is big, because there are two systems, one live and one installed. Another version might be specialized and contain only the boot part of the live system, so it would be smaller (around 1 GB instead of 1.8 GB). I hope you can download this one without a penalty fee from your ISP :-)

---

### Post by ventrical on 2015-04-14
> **sudodus said:**
> Well it is big, because there are two systems, one live and one installed. Another version might be specialized and contain only the boot part of the live system, so it would be smaller (around 1 GB instead of 1.8 GB). I hope you can download this one without a penalty fee from your ISP :-)

I am always over my limit as it is :)

Here goes dl now :)

Regards..

---

### Post by ventrical on 2015-04-14
I used mkusb to install the compressed image file.

How do I boot into usb-installed partition 5?

It just automatically booted into .iso with 'Try Ubuntu' and "Install Ubutnu' options.

Regards..

---

### Post by sudodus on 2015-04-15
I think you booted in BIOS mode. If you check carefully, you will see an option (a line in the menu) to boot into the installed system. I added that line to the syslinux boot menu.

In a similar way, there is an option to boot into the installed system in the UEFI grub menu, that belongs to the boot system of the iso file.

*Edit*: Maybe I should make those lines easier to find, for example with stars.

---

### Post by ventrical on 2015-04-15
> **sudodus said:**
> I think you booted in BIOS mode. If you check carefully, you will see an option (a line in the menu) to boot into the installed system. I added that line to the syslinux boot menu.

In a similar way, there is an option to boot into the installed system in the UEFI grub menu, that belongs to the boot system of the iso file.

*Edit*: Maybe I should make those lines easier to find, for example with stars.

Ahhh... ok.... I'll have a look at that then. 


Regards..

---

### Post by ventrical on 2015-04-16
> **sudodus said:**
> I think you booted in BIOS mode. If you check carefully, you will see an option (a line in the menu) to boot into the installed system. I added that line to the syslinux boot menu.

In a similar way, there is an option to boot into the installed system in the UEFI grub menu, that belongs to the boot system of the iso file.

*Edit*: Maybe I should make those lines easier to find, for example with stars.

When booting in BIOS mode it will go right to the purple boot screen. There are no other options unless you hit another key to be able to choose alternate install menu. In UEFI mode there are all the options in Grub. It works very well with perisistive drive.

*note* You have left the default server for Sweden and so the first update fails. It has to be changed to United States or Main Server.

 Nice work , well done.

Regards..

---

### Post by sudodus on 2015-04-16
I'm glad you managed to run it in UEFI mode.

- What about BIOS mode and the syslinux menu (with Try Ubuntu, Install Ubuntu etc)? Did you manage to boot also the installed system that way? It works for me, so it should work, unless there is some portability issue.

I'll try to remember the issue with the default server in future versions. I can update from the US server. Funny that you could not update from the Swedish server. Maybe you hit a bad time slot, when that server was upgrading itself or some other temporary problem.

- What would you prefer for a portable system in a USB pendrive?

- A persistent live system or an installed system (or a combination with both)?

- This pendrive system contains standard Ubuntu. Would it be better with a lighter desktop environment, for example Lubuntu or Xubuntu to compensate for the slow data transfer rate of USB and the flash memory in pendrives.

---

### Post by ventrical on 2015-04-16
I have had great success installing ubuntu to USB flash drives which work almost as fast as an hdd. The trick I use is to remove any  hdd that is currently installed in the system. Then, I just install whatever flavor to the USB as the ubuntu iso recognizes a 16GB USB stick as a target harddrive. Lubuntu has been fastest. This method is far superior to creating a persistive usb_drive and I still have installs of Lucid Linux on 8 and 16 GB USB flash disks respectively.  I understand that a lot of experimenters do not agree with my method and they will suggest leaving the hdd in while install  to a usb flash_disk. However .. the method I discovered  works just fine for me.

  I have not tried this method in UEFI mode as of yet.

Regards..

---

### Post by ventrical on 2015-04-16
> **sudodus said:**
> I'm glad you managed to run it in UEFI mode.

- What about BIOS mode and the syslinux menu (with Try Ubuntu, Install Ubuntu etc)? Did you manage to boot also the installed system that way? It works for me, so it should work, unless there is some portability issue.



  I do not get a menu in BIOS mode on my latest  motherboard .. however I should try it on another machine. Currently it goes right to purple screen  with 'man in circle logo' at bottom and then I am given options to 'try ubuntu' , 'install ubuntu'.

Regards..

*edit*

 ok.. I see PBR listing ... works just fine .. I did not see it the first time.:)

Regards..

---

### Post by sudodus on 2015-04-17
> **ventrical said:**
> I have had great success installing ubuntu to USB flash drives which work almost as fast as an hdd. The trick I use is to remove any  hdd that is currently installed in the system. Then, I just install whatever flavor to the USB as the ubuntu iso recognizes a 16GB USB stick as a target harddrive. Lubuntu has been fastest. This method is far superior to creating a persistive usb_drive and I still have installs of Lucid Linux on 8 and 16 GB USB flash disks respectively.  I understand that a lot of experimenters do not agree with my method and they will suggest leaving the hdd in while install  to a usb flash_disk. However .. the method I discovered  works just fine for me.


I agree completely with this :-D

It is certainly possible, but more risk of failure to leave the internal  drive connected. See what I recommend at the 'FromUSBSstick' help page: [https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)

> It is straight-forward to install Ubuntu 14.04.2 LTS (64-bit), **ubuntu-14.04.2-desktop-amd64.iso** in UEFI mode to the whole drive, when no other drive is connected in the computer. 

---

### Post by sudodus on 2015-04-17
> **ventrical said:**
> I do not get a menu in BIOS mode on my latest  motherboard .. however I should try it on another machine. Currently it goes right to purple screen  with 'man in circle logo' at bottom and then I am given options to 'try ubuntu' , 'install ubuntu'.

Regards..

*edit*

 ok.. I see PBR listing ... works just fine .. I did not see it the first time.:)

Regards..

That was nice for me to read! I was getting afraid that something was not portable or stable.

Thanks for testing :-)

---

### Post by ventrical on 2015-04-17
> **sudodus said:**
> That was nice for me to read! I was getting afraid that something was not portable or stable.

Thanks for testing :-)

Your welcome. It is very stable. It should be mentioned (unless it has already been mentioned and I did not see it) that the shift key or any other key should be held down while booting into BIOS mode, otherwise we do not get the menu with the the installed 'ubuntu' PBR. This method is used when installing ubuntu  from alternate mode (as you know).

Regards..

---

### Post by dodgexander on 2015-04-28
Thanks for the brilliant guide, I have been following the steps to try and make a similar USB disk, except with mint. I wondered, when creating your own key as your instructions, what is the easiest way to create a custom boot menu as you have done? I have tried looking into each of the files as you have mentioned in your live image(which is working fine btw) but I can't understand what I need to change to customise it towards my own image.

I had my image working fine, but on startup it presented only to me my installed partition and not the live one. I guess I want an easy way to add the live image as an option.

---

### Post by sudodus on 2015-04-28
Welcome to the Ubuntu Forums :-)

1. Which compressed image file did you try? And which description did you follow - please specify with as many details as possible!

2. Do you have problems in UEFI mode or BIOS mode or both?

3. Which version of Linux Mint did you try?

First I must find out what you have tried, and then we can try to find out if the configuration of Linux Mint is similar enough for the same description to work, (as what works for Ubuntu), or if something must be changed.

---

### Post by dodgexander on 2015-04-28
Thanks!

In answer to your questions, I used the ubuntu 10gb image from the op (dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz), this works fine. My motherboard booted fine from it in UEFI mode.

As for trying my own configuration which is the same for mint, except with extra space I was able to install mint and create a live partition. When booting from this drive I could enter my installation fine, but there was no option "to try" mint in the boot menu.

The version of mint I have been using is: linuxmint-17.1-cinnamon-64bit.iso.

The problem is only in the boot menu as far as I can see, when I use the OP instructions to create the disk I can boot fine into my installation, but lack the option to "try" mint. eg the live usb option.

In the op it says you have to alter several files including the grub.cfg in live and installed partitions, yet I have no clue how I should edit mine for mint.

Thanks a lot for your help!

My aim is simply to have a USB stick I can plug in with an install and a live version of mint, but when I unplug it the machine will just boot up windows instead. Is it even possible to keep the windows bootloader on the local drive whilst keeping only grub on the usb?

I am not interested really in getting it to work on non EFI computers, I have a windows 8.1 install on EFI on the main computer I want to use this USB, but even when I install grub too USB it seems to remove the windows bootloader and then I am in a situation where I have to rebuild the windows bootloader, or have the USB stick plugged into to boot from windows 8.1 from my internal drive.

---

### Post by sudodus on 2015-04-28
That's a good and detailed description :-)

I refer back to the description how to create the system:

> [I][B]
C. Boot from the pendrive in UEFI mode and install Ubuntu[/B][/I]

Install Ubuntu into partition 5 of the same pendrive. [COLOR=#ff0000]Install the
bootloader into partition 5 (not into the head of the drive).
[/COLOR]
Tweak the boot configuration files

```
.../usb-live/syslinux/txt.cfg
.../usb-live/boot/grub/grub.cfg
.../usb-installed/boot/grub/grub.cfg

```
according to the files that you find after installing with mkusb from

** dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz**

to a pendrive.


***D. The pendrive uses the boot system of the Ubuntu installer ***

Notice that this system is not like an ordinary installed system.

You seem to boot directly to the grub menu of the installed system. Maybe you forgot to install the bootloader into partition 5 (not to the head of the drive). Doing this will give you a system that only boots into the live system. You need to add a 'menuentry' in that system's grub.cfg file (**.../usb-live/boot/grub/grub.cfg** for UEFI mode) to make the system able to boot into the installed system too.

Select ***Something else*** in the partitioning window in order to control where to install the bootloader.

---

### Post by dodgexander on 2015-04-28
Now I can't even install as the installer says it needs to unmount /CDROM which it can't as that's the running live partition.

I'm not really sure why this is happening, but before I bypassed this by using a different USB drive as the live disk.

I also get confused by when I'm running efi and not. Before I was able to run the very same USB disk having efi only enabled in bios. This time my USB disk only appears when legacy mode is also on.

I wonder if it matters how you are booted when you create the start up disk..

Also somehow I have lost my windows bootloader off my internal hd again. I didn't even do anything apart from install a live usb startup disk on the first partition of my USB disk and now my windows bootloader has gone!

So unless I can work around this Mount problem I'll have to use my second usb stick again to make a separate live disk and then use that live to install mint on my desired usb disk.

As for the grub menu entry I don't know what to change or add and I was planning to keep this second disk (which holds the working 10gb image from under op) so I could study the grub.cfg file there but it looks like I'll have to forget about that bit until I get mint installed again as it looks like I'll need that second disk!

Trust me to turn this into a nightmare! I am only following the instructions in the op :D

---

### Post by sudodus on 2015-04-29
Linux mint is a different linux distro, and the configuration files can be different. It means that you cannot expect everything to work without changing some things from what they are in the Ubuntu case. I'm sorry but I don't know what to change and how to change it.

> **dodgexander said:**
> Now I can't even install as the installer says it needs to unmount /CDROM which it can't as that's the running live partition.

I'm not really sure why this is happening, but before I bypassed this by using a different USB drive as the live disk.

I also get confused by when I'm running efi and not. Before I was able to run the very same USB disk having efi only enabled in bios. This time my USB disk only appears when legacy mode is also on.

I wonder if it matters how you are booted when you create the start up disk..

Yes, I think it matters.
> 
Also somehow I have lost my windows bootloader off my internal hd again. I didn't even do anything apart from install a live usb startup disk on the first partition of my USB disk and now my windows bootloader has gone!

If you install a system using the standard methods, the installer is likely to install the bootloader into the 'first internal disk'. You should either remove the internal disk or use 'Something else' and manually set the target for the bootloader to where you want it.

Fortunately it is possible to re-install the Windows bootloader without installing the whole Windows operating system.
> 
So unless I can work around this Mount problem I'll have to use my second usb stick again to make a separate live disk and then use that live to install mint on my desired usb disk.

As for the grub menu entry I don't know what to change or add and I was planning to keep this second disk (which holds the working 10gb image from under op) so I could study the grub.cfg file there but it looks like I'll have to forget about that bit until I get mint installed again as it looks like I'll need that second disk!

Trust me to turn this into a nightmare! I am only following the instructions in the op :D

This is what I suggest:

If you want an installed Linux Mint system, maybe the best option is to install it with the standard method offered by Mint's own installer. Keep that system separate from 'my' portable installed system, which is made with Ubuntu.

If you want 'my' portable installed system, keep using it, if your pendrive is still working with it or re-install it from the compressed image file. But do not mix it with Linux Mint on the same pendrive.

Apply the method of 'my' portable installed system to Linux Mint ***only if you enjoy*** fixing the things that need fixing because of differences between Linux Mint and Ubuntu.

---

### Post by sudodus on 2015-04-29
Search the internet for ***Windows bootloader*** and you will find many descriptions how to do it, for example

[http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/](http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/)

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

[https://neosmart.net/wiki/recovering-windows-bootloader/](https://neosmart.net/wiki/recovering-windows-bootloader/)

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

[http://www.fixedbyvonnie.com/2013/12/how-to-repair-the-efi-bootloader-in-windows-8/](http://www.fixedbyvonnie.com/2013/12/how-to-repair-the-efi-bootloader-in-windows-8/)

[And this one: "[COLOR=#b22222]***So you’ve managed to hose the bootloader on your computer? No worries, every Geek has***.[/COLOR]" https://tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/]("https://tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/")

---

### Post by dodgexander on 2015-04-29
thanks for your help, I have been using this as a learning experience, its more fun than anything trying to work out the way things work.

Anyhow I think I will do as you said and just stick to the traditional method. I already have too many problems with my computer not recognising some UEFI boot disks.

In the long term I think I will just settle for an installed system with the bootloader on the same partition as the install on my USB disk. In the mean time I will keep your disk image handy. Thanks.

---

### Post by sudodus on 2015-04-29
You are welcome and good luck :-)

---

### Post by jamosky on 2015-09-03
Hi Guys 

Great guide, could you explain to me why you have 2 partitions overlapping please ? 

Number 2 and 3 (extended and ext4) as shown below from your original post ...

```

Model: SanDisk Extreme (scsi)
Disk /dev/sdd: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1343MB  1342MB  primary   fat32           boot
 2      1344MB  9933MB  8589MB  extended
 5      1344MB  9395MB  8051MB  logical   ext4
 6      9396MB  9933MB  537MB   logical   linux-swap(v1)
```

thanks...

---

### Post by sudodus on 2015-09-03
Welcome to the Ubuntu Forums, jamosky :-)

Partition number two is an extended partition. It is a container for partitions number five and six, which are 'logical' partitions. You get an intuitive view of the partition table with ***gparted***.

You find good explanations via the internet, for example [this link](https://askubuntu.com/questions/151968/what-does-the-term-extended-partition-mean-is-it-safe-to-use-this-type-of-par)

---

### Post by jamosky on 2015-09-03
thanks, that explains why I cant select logical partitions in gparted !

---

### Post by sudodus on 2015-09-03
It *is* possible to select logical partitions in gparted. What are you trying to do?

---

### Post by jamosky on 2015-09-03
sorry....what I meant is gparted will not allow you create a logical partition outside of the extended partition...its greyed out. So I was incorrectly trying to create them outside of the extended partition, I am trying to follow your guide :)

---

### Post by sudodus on 2015-09-03
That's right, you create logical partitions inside the extended partition.

You can increase the size of the the extended partition (move the right edge in gparted), and in the new space inside it, you can create a logical partition.

---

### Post by jamosky on 2015-09-04
hi sudodus

Great work, i have the mkusb method using the compressed image working across UEFI & BIOS, really fast! I am going to try the manual method next using an Ubuntu ISO. 

My Question - once I have the USB created and working with various tweeks etc, what is the best way to make an image of that USB ? - basically to make my own .img.xz for use with mkusb.

---

### Post by sudodus on 2015-09-04
I use home-made batch files with ***dd*** and ***xz*** for that purpose. Compressing with ***gzip*** instead of xz is much faster, but the compression ratio is not as good. ***mkusb*** can expand files made with both methods.

1. Find the end of the last partition, *). If you use the whole pendrive it is not necessary, just clone the whole drive.

2. Zeroise the unused space of the partitions (this makes the compression much more efficient). You can write zeros with dd to a file until the file fills all available space. Then remove that file. (Do it in all writable partitions.)

3. Clone the drive from the very beginning to the end of the last partition, and pipe the output via xz or gzip to 'file.img.xz' or 'file.img.gz' (depending on the compression tool). I have found that cloning is faster with the option bs=4096 (default is bs=512).

[HR][/HR]
*) This works with an MSDOS partition table. If you have a GUID partition table, I'm afraid that you must clone the whole drive.

I have not tested ***Clonezilla*** for this purpose, but it is possible, that it works to make a cloned image of these special systems with Clonezilla. If it works, it will be more efficient than to use dd and xz. But dd and xz make image files, that are easier to use (they do not need Clonezilla).

---

### Post by jamosky on 2015-09-04
thanks for the quick response ! I will give that a try and let you know how i get on....:D

---

### Post by jamosky on 2015-09-07
that works great, many thanks.

I have another question for further experiments :)

 I like the persistence of your install method,  it behaves  as a 'normal' ubuntu OS, I am wondering if it is possible to load the OS or filesystem into memory using your method and maintain persistence :) For example :- 

1. use your method for install to USB
2. make changes to the the OS ...install/remove packages, change desktop environment etc.
3. set the OS to load into RAM 

is this possible ? Currently the system fails (as expected) when the USB is removed as the filesystem is no longer availible

---

### Post by sudodus on 2015-09-07
It is easy to put the OS of a persistent live system into RAM. Just add the boot option **toram**. (Add it near **persistent** in grub.cfg)

It may be more complicated to use RAM with an installed system. See this link (I have not tried it, but it seems to work for several people).

[Making Ubuntu Fast using RAM (updated and simplified)](http://ubuntuforums.org/showthread.php?t=1594694)

And of course, you need a lot of RAM to make it work well.

---

### Post by jamosky on 2015-09-08
thanks I will take a look at that.

---

### Post by msavini on 2015-11-16
hi,
i'm not an expert about boot processes at all, but i'd like to share how i created an external usb disk with ubuntu installed that boots on both UEFI and bios machines...

here are the steps i followed:

1) using gparted, i wiped the disk creating a new gpt partition table with the following partitions:
[FONT=Courier New]
size     | filesystem
---------------------
2MB     | unformatted filesystem
200MB  | fat32
98GB    | ext4
3800MB | swap
[/FONT]

2) using gparted as well, i flagged the first partition with "bios_grub" flag.
this is the final result:
[FONT=Courier New]$ sudo parted /dev/sdb print
Model: WDC WD32 00BEKT-00PVMT0 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3146kB  2097kB                     bios_grub
 2      3146kB  213MB   210MB   fat32            msftdata
 3      213MB   10.3GB  10.1GB  ext4
 4      10.3GB  14.3GB  3985MB linux-swap(v1)[/FONT]

3) i installed ubuntu 14.04.**2** on the disk in bios mode. i selected "manual partitioning" to use /dev/sdb3 as root and install grub to the whole drive (/dev/sdb).

4) after the installation, i booted the disk in bios mode, installed gparted and marked the fat32 partition (/dev/sdb2) with the "boot" flag.
[FONT=Courier New]$ sudo apt-get update && sudo apt-get install gparted && sudo gparted[/FONT]

5) finally i installed grub-efi-amd64-bin and efi on /dev/sdb2:
[FONT=Courier New]$ sudo apt-get install grub-efi-amd64-bin
$ sudo mkdir -p /mnt/esp
$ sudo mount /dev/sdb2 /mnt/esp
$ sudo grub-install --efi-directory /mnt/esp --boot-directory /boot  --target x86_64-efi --removable /dev/sdb
Installing for x86_64-efi platform.
Installation finished. No error reported.
$ sudo umount /mnt/esp
$ sudo rm -r /mnt/esp[/FONT]


here are the tests i performed:
1) before installing efi, the disk was not bootable on a UEFI machine. after installing it, it was.
2) since i installed ubuntu 14.04.**2** i tried and update the system: more than 300MB of updates where downloaded and installed (including kernel updates) and the disk is still bootable in both UEFI and bios machines.
3) i tried same procedure with linux mint 17.1, updating to 17.2: everything went as expected.
4) i tried and boot the disk inside a virtualbox machine: it correctly boots in both modes.

the only attempt that failed so far was doing the whole procedure inside virtualbox: the disk boots fine if efi is disabled but i was not able to boot it in efi mode.

what do you think about?

---

### Post by sudodus on 2015-11-16
Welcome to the Ubuntu Forums msavini :-)

I think your external usb disk with ubuntu installed that boots on both UEFI and bios machines is very interesting. It works well for you, at least when left alone and doing its own update/upgrade tasks.

A future hard test is how it survives attacks from Windows. What happens if your usb disk is connected during major updates of Windows 10? Maybe it is left alone, thanks to the --removable option of grub-install.

Good luck with your system, and please keep us updated :-)

---

### Post by msavini on 2015-11-16
fortunately, i only (sporadically) run windows inside a virtualbox vm... sorry then, i won't be able to test if my method survives a windows update...
i'll tell you if i find it to be broken by an ubuntu update, instead!

---

### Post by sudodus on 2015-11-16
I have only Windows Technical Preview (for Windows 10). I have no regular Windows 10 system.

Let us hope that someone who uses Windows 10 has time enough to test it!

---

### Post by QDR06VV9 on 2015-11-16
@sudodus
I would have taken that testing effort, But the last bit of updates that came in for Windows 10 On a Lenovo B-570
Took my Bios out meaning I no longer have the ability to get to my BIOS.
As a cheesy sort of work around I can remove the hard drive and plug a USB drive with Installer or persistent OS.
This Lenovo Laptop is known for having faulty BOIS from the Start. Just a heads up for any one with this Laptop.

---

### Post by sudodus on 2015-11-16
That's too bad runrickus. I hope that there will be a fix soon for the BIOS of that Lenovo model.

---

### Post by QDR06VV9 on 2015-11-16
> **sudodus said:**
> That's too bad runrickus. I hope that there will be a fix soon for the BIOS of that Lenovo model.

That's very kind, but That just goes with testing.(Of which I am very aware)
I find it quite funny that it was Window's That took it out though:D
But if there is a way I will find it. 
Best Regards

---

### Post by msavini on 2015-12-01
hi,
when testing my own portable installation [method]("http://ubuntuforums.org/showthread.php?t=2213631&p=13391873#post13391873"), i've always used an external usb disk.
now i'm trying to do the same on a usb stick, and i'm stuck on the first step: i simply can't create an "unformatted" partition using gparted...
i tried 2 different (cheap!) usb sticks: in one case, creating an unformatted partition results in a fat32 filesystem with a warning about an "incorrect" filesystem. in the other case the process results in an "unknown" filesystem...
is this "normal"..?

---

### Post by oldfred on 2015-12-01
I use gpt even on flash drives now.
I have not had an issue with unformatted, but you have to scroll all the way down on format choices.

My flash drives usually are MicroCenter's own brand, and now I only buy USB3. I found my USB3 was even faster by about 10% on my USB2 ports on my old computer.

---

### Post by msavini on 2015-12-01
> **oldfred said:**
> I use gpt even on flash drives now.
i tried with both msdos and gpt, but nothing changes...

> **oldfred said:**
> I have not had an issue with unformatted, but you have to scroll all the way down on format choices.
of course, i did scroll!

> **oldfred said:**
> My flash drives usually are MicroCenter's own brand, and now I only buy USB3. I found my USB3 was even faster by about 10% on my USB2 ports on my old computer.
i'll try with a usb3 stick (i should have one somewhere) and report...

---

### Post by sudodus on 2015-12-02
It should work independently of USB 2 and USB 3.

- Is the pendrive big enough?

Maybe it would work better if you wipe the first megabyte before trying to make a new partition table. It can be done with [mkusb](https://help.ubuntu.com/community/mkusb). See these links for more details

[mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

[mkusb#Wipe_menu](https://help.ubuntu.com/community/mkusb#Wipe_menu)

---

### Post by msavini on 2015-12-02
> **sudodus said:**
> It should work independently of USB 2 and USB 3.

- Is the pendrive big enough?
of course, it is... i'm just creating a 2MB partition...

> **sudodus said:**
>  Maybe it would work better if you wipe the first megabyte before trying to make a new partition table. It can be done with [mkusb]("https://help.ubuntu.com/community/mkusb"). See these links for more details

[mkusb#Wipe_the_first_megabyte_or_the_whole_device]("https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device")

[mkusb#Wipe_menu]("https://help.ubuntu.com/community/mkusb#Wipe_menu")

thanks for the hint: i tried and wipe the first MB in both the usb sticks, but nothing changes...

---

### Post by sudodus on 2015-12-02
> **msavini said:**
> hi,
when testing my own portable installation [method]("http://ubuntuforums.org/showthread.php?t=2213631&p=13391873#post13391873"), i've always used an external usb disk.
now i'm trying to do the same on a usb stick, and i'm stuck on the first step: i simply can't create an "unformatted" partition using gparted...
i tried 2 different (cheap!) usb sticks: in one case, creating an unformatted partition results in a fat32 filesystem with a warning about an "incorrect" filesystem. in the other case the process results in an "unknown" filesystem...
is this "normal"..?

> **msavini said:**
> of course, it is... i'm just creating a [COLOR="#FF0000"]**2MB**[/COLOR] partition...

thanks for the hint: i tried and wipe the first MB in both the usb sticks, but nothing changes...

Are you intending to create a partition with a bios_grub flag for grub in BIOS mode? And are you doing it in a GPT partition table? In that case you can use the following wipe menu option in ***mkusb***

**a "Advanced: create GUID partition table (skeleton for installing an OS)" **

Otherwise you should be able to do it with ***gparted***, at least after you have wiped the first megabyte and created a new partition table. See also [this link for more details](https://wiki.ubuntu.com/Win32DiskImager/iso2usb/FormatHelp)

I have been doing it many times also with USB pendrives. It should not be any problems. Are you sure that your pendrives are good? That you can write to them? If they are failing, the first symptom may be that they are read-only.

[hr][/hr]
***Edit:*** 'Unknown file system' might mean that there is no file system, in other words, that you have succeeded, but the message is tricking you :-)

---

### Post by msavini on 2015-12-02
> **sudodus said:**
> Are you intending to create a partition with a bios_grub flag for grub in BIOS mode?
And are you doing it in a GPT partition table?
Are you sure that your pendrives are good? That you can write to them?

answer is yes to all of the questions.

this is what i did with 3 different usb sticks:
1) wiped the first MB using mkusb
2) using gparted:[INDENT]- created a gpt partition table
    - created a 2MB unformatted parition
    - successfully applied changes
[/INDENT]
 
however none of the 3 sticks shows an unformatted partition:
- 2 of the usb sticks show a fat32 partition with this warning:[INDENT][I]Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for fat32 file system support:  dosfstools, mtools.[/I]
[/INDENT]
- the third shows an "unknown" filesystem partition.

using this method with an external hard disk never gave any issue.

all of the 3 usb sticks are cheap, but working fine: i can create partitions, mount them and write. no kind of problem...

---

### Post by sudodus on 2015-12-02
I see. It seems that you are affected by a bug, because my experience is that this is possible with USB sticks as well as with USB hard disk drives.

Exactly which operating system are you running? You can get it specified by the output of the following commands:

```
lsb_release -a

uname -a
```

Which version of gparted? Check via the pulldown menu ***Help -- About***

And what USB sticks are there, brand name and model?

What is the output of the following commands when the USB sticks are plugged-in? It should help you identify the USB sticks, but use also whatever information you have about them.

```
ls -l /dev/disk/by-id| grep [a-z]$|tr -s ' ' ' '  |cut -d ' ' -f 9,11|sort -k2|grep -e \^a -e \^u  |sed 's#../..#/dev#'

sudo lsblk -o NAME,MODEL,FSTYPE,LABEL,MOUNTPOINT,SIZE,NAME /dev/[^f]d?

sudo parted -ls

```

It can be difficult to find out what program package that is causing this bug. Maybe gparted itself, maybe some other package. Maybe I can try in the same operating system, with the same version of gparted and a similar USB stick (if I have some similar stick). After some more testing, and maybe help from someone else, who can add some knowledge, you can report a bug to Launchpad via the following command

```
apport-bug gparted
```

(or some other package).

---

### Post by msavini on 2015-12-03
here you are:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
$ uname -a
Linux bolide 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

> **sudodus said:**
> Which version of gparted? Check via the pulldown menu ***Help -- About***
GParted 0.18.0

> **sudodus said:**
> And what USB sticks are there, brand name and model?
2 unnamed sticks and 1 transcend.

> **sudodus said:**
> What is the output of the following commands when the USB sticks are plugged-in?

```

$ ls -l /dev/disk/by-id| grep [a-z]$|tr -s ' ' ' '  |cut -d ' ' -f 9,11|sort -k2|grep -e \^a -e \^u  |sed 's#../..#/dev#'
usb-Generic_Flash_Disk_CCBB1209032156470220217111-0:0 /dev/sdc
usb-JetFlash_Transcend_8GB_5MWVD0SETVSA0DNB-0:0 /dev/sdd
usb-058f_6387_39881A48-0:0 /dev/sde

```

```

$ sudo lsblk -o NAME,MODEL,FSTYPE,LABEL,MOUNTPOINT,SIZE,NAME /dev/sd*
sdc    Flash Disk                                62.5G sdc
&#9492;&#9472;sdc1                  ext4                     48.7M &#9492;&#9472;sdc1
sdc1                    ext4                     48.7M sdc1
sdd    Transcend 8GB                              7.6G sdd
&#9492;&#9472;sdd1                  vfat                        2M &#9492;&#9472;sdd1
sdd1                    vfat                        2M sdd1
sde                                               725M sde
&#9492;&#9472;sde1                  vfat                        2M &#9492;&#9472;sde1
sde1                    vfat                        2M sde1

```

```

$ sudo parted -ls
Model: Generic Flash Disk (scsi)
Disk /dev/sdc: 67.1GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  51.0MB  51.0MB  ext4


Model: JetFlash Transcend 8GB (scsi)
Disk /dev/sdd: 8103MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3146kB  2097kB  fat32


Model:   (scsi)
Disk /dev/sde: 760MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3146kB  2097kB  fat32

```

---

### Post by sudodus on 2015-12-03
> **msavini said:**
> here you are:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
$ uname -a
Linux bolide 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
[QUOTE=sudodus;13400870]Which version of gparted? Check via the pulldown menu ***Help -- About***
GParted 0.18.0
[/quote]
I have a corresponding system, but completely up to date with the kernel **3.13.0-71-generic** and the same version of ***gparted*** as you.
> 
> **sudodus said:**
> And what USB sticks are there, brand name and model?
2 unnamed sticks and 1 transcend.

I have a Transcend 8 GB pendrive (a slow USB 3 pendrive).
```
usb-JetFlash_Transcend_8GB_197950252-0:0 /dev/sdd
```
> 
> **sudodus said:**
> What is the output of the following commands when the USB sticks are plugged-in?

```

$ ls -l /dev/disk/by-id| grep [a-z]$|tr -s ' ' ' '  |cut -d ' ' -f 9,11|sort -k2|grep -e \^a -e \^u  |sed 's#../..#/dev#'
usb-Generic_Flash_Disk_CCBB1209032156470220217111-0:0 /dev/sdc
usb-JetFlash_Transcend_8GB_5MWVD0SETVSA0DNB-0:0 /dev/sdd
usb-058f_6387_39881A48-0:0 /dev/sde

```


I did it the easy way: installed [mkusb](https://help.ubuntu.com/community/mkusb) and used the following wipe menu option in mkusb

**a "Advanced: create GUID partition table (skeleton for installing an OS)"**

It worked for me (with my Transcend 8 GB pendrive). And I think it should work also with your Transcend pendrive. See the attached screenshots :-)

If it does not work with the 'noname' pendrives, I think you can blame the pendrive manufacturer.

-o-

In order to show properly the content of the pendrive after you have edited the partition table, you may need to check that it is unmounted, unplug and plug it in again. Try that and check what you get with ***gparted*** and with

```
sudo parted -ls
#and
sudo lsblk -o NAME,MODEL,FSTYPE,LABEL,MOUNTPOINT,SIZE,NAME /dev/sd*
```

---

### Post by sudodus on 2016-01-18
[SIZE=4]Compressed image file with Ubuntu 15.10[/SIZE]

I made a compressed image file with Ubuntu 15.10, that I thought should be rather stable (I hoped it would not be destroyed easily when updating itself or updating Windows). It can boot in UEFI mode as well as in BIOS mode (but it works only in computers with 64-bit architecture). It was made up to date (updated/dist-upgraded) 2016-01-18, a clean *installed Ubuntu system with almost no tweaks or patches except that it can boot in UEFI and BIOS mode*, and that some 'cruft' is cleaned.

Download from this link: [dd_Ubuntu_15.10-UEFI-n-BIOS-11GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_15.10-UEFI-n-BIOS-11GB.img.xz)

Check that the download was successful with ***md5sum***

```
md5sum dd_Ubuntu_15.10-UEFI-n-BIOS-11GB.img.xz
c9b8bb5f3d2d50754f3c66664f3275ae  dd_Ubuntu_15.10-UEFI-n-BIOS-11GB.img.xz

```

Log in with the following user ID and password

[B]user:     guru
password: changeme[/B]

and change the password ;-)

[SIZE=3]Details[/SIZE]

I made this system in a computer without an internal drive by installing in UEFI mode into a pendrive with an MSDOS partition table and two partitions, with FAT32 for the EFI (boot) partition, and with ext4 for the root partition. I skipped the swap partition, but it is easy enough to add, if you wish. After the installation I remade the booting (re-installed grub twice, once for UEFI and once for BIOS, and with the option **--removable**, which I think makes it less vulnerable to attacks from Windows or from the UEFI system. I also added the mount option **noatime** for the root partition in /etc/fstab in order to reduce wear.

[SIZE=3]Installing into a USB pendrive or another drive (internal or external)[/SIZE]

- in linux: use [mkusb](https://help.ubuntu.com/community/mkusb) to install from the compressed image file,

- in Windows: use [7zip](http://www.7-zip.org/) to uncompress and after that [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) to install from the [uncompressed] image file.

[SIZE=3]Alternative method; tips and tricks[/SIZE]

*Tom_S.* made a tutorial with many details: [Surface Pro 3 - USB/MicroSD Only Install](http://ubuntuforums.org/showthread.php?t=2309963). It is really worthwhile to read the tutorial and use some of the tips and tricks described there (depending of what you need).

***Edit:***

After more testing, I found some boot problems in UEFI mode. I think *you have better luck with the compressed image file described in the next post*.

---

### Post by sudodus on 2016-01-20
[SIZE=4]Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10[/SIZE]

The system in this compressed image file is very similar to a system that has been very stable for a long time now, so it is also likely to continue to work in many computers, modes and conditions.

This system contains an up to date (updated & dist-upgraded 2016-01-19) installed Ubuntu 15.10 64-bit system alongside a live Ubuntu 14.04.2 64-bit system. I added the mount option **noatime** for the root partition in /etc/fstab in order to reduce wear. The booting is made in a similar way as described in post #8: [A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)

Notice that the booting is done via syslinux in BIOS mode (attachments 1-4), and via grub 2 in UEFI mode (attachment 5).

In BIOS mode you must press a key while there is a screen with two small icons at the bottom (attachment 1) in order to get to the menu where the installed system can be selected.

The compressed file [dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz) can be downloaded from [http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

Check that the download was successful with ***md5sum***

```
md5sum dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz
e36d68f00dde93ecc4e7f283d9550077  dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz
```

Log in with the following user ID and password

[B]user:     guru
password: changeme[/B]

and change the password ;-)

[SIZE=3]Installing into a USB pendrive or another drive (internal or external)[/SIZE]

- in linux: use [mkusb](https://help.ubuntu.com/community/mkusb) to install from the compressed image file,

- in Windows: use [7zip](http://www.7-zip.org/) to uncompress and after that [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) to install from the [uncompressed] image file.

[SIZE=3]Alternative method; tips and tricks[/SIZE]
I also added the mount option noatime for the root partition in /etc/fstab in order to reduce wear.
*Tom_S.* made a tutorial with many details: [Surface Pro 3 - USB/MicroSD Only Install](http://ubuntuforums.org/showthread.php?t=2309963). This compressed image file provides a shortcut compared to the long list of tasks, but it is really worthwhile to read the tutorial and use some of the tips and tricks described there (depending of what you need).

[SIZE=3]Updating/dist-upgrading[/SIZE]

After updating/dist-upgrading the installed system to get a new version of the kernel, it should boot directly in BIOS mode. But you may need to edit a **grub.cfg** file in order to 'reach' the new kernel and boot from it.

When booted into 15.10, you can edit with the command line ```
sudo nano /media/guru/usb-live/boot/grub/grub.cfg
``` and edit the kernel version number in the menuentries.

If there are no symbolic links in the root partition you can make links that match the entries in the grub.cfg file,

```

cd /
sudo ln -s boot/vmlinuz-4.2.0-25-generic vmlinuz
sudo ln -s boot/initrd.img-4.2.0-25-generic initrd.img

```

Change the kernel number (4.2.0-25) to what applies for the new kernel.

---

### Post by ventrical on 2016-01-22
I was experimenting with win10. I had previously installed Win8 evaluation on 3TB hdd.  At first I decided to update as it offered me upgrade to Windows 10 but it had notified me that evaluation copy expired. It told me I cannot upgrade so then I adjust machine and try to upgrade to Win 10 from iso.dvd. Result was system was completely locked out, I could not get into BIOS or Boot Options. I had to disassemble complete physical KVM to be able to make machine bootable again. Now doing fresh install of Windows 10. 

There is definite evidence that Windows 8 evaluation copy in UEFI mode has tampered with the KVM and the BIOS sequence.

  I have much to write on this and will hope to compose this later.

Regards..

---

### Post by ventrical on 2016-01-22
Windows 10 installed in UEFI mode.  Xenial will not recognize operating system but does recognize Windows Boot Loader. Does not offer to resize partition or side by side  and install. Only offers to 'erase completely and install ubuntu' and encrypt/LVM modes.

 So I will have to use gparted to resize partition I suppose. 
:)

regards..

---

### Post by sudodus on 2016-01-22
- Is Windows 10 shut down completely (or hibernated or semi-hibernated alias 'fast boot')? It may work better for Xenial, if Windows is shut down completely.

1. A first task is to test a Xenial system installed into the internal drive alongside Windows 10. I guess this is the task you are talking about now, how it can be installed and if it survives.

2. Another thing is to test the Ubuntu system described in post #63. If the 'installed' 15.10 system can survive attacks from Windows, if you 'forget' to remove the pendrive when you boot into Windows, and maybe even more important, when Windows is updated at shutdown and the next boot?

The compressed file [dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz) can be downloaded from [http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

---

### Post by ventrical on 2016-01-22
> **sudodus said:**
> - Is Windows 10 shut down completely (or hibernated or semi-hibernated alias 'fast boot')? It may work better for Xenial, if Windows is shut down completely.

1. A first task is to test a Xenial system installed into the internal drive alongside Windows 10. I guess this is the task you are talking about now, how it can be installed and if it survives.

2. Another thing is to test the Ubuntu system described in post #63. If the 'installed' 15.10 system can survive attacks from Windows, if you 'forget' to remove the pendrive when you boot into Windows, and maybe even more important, when Windows is updated at shutdown and the next boot?

The compressed file [dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_14.04.2-live-n-15.10-inst-UEFI-n-BIOS-10GB.img.xz") can be downloaded from [http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

1. I am currently wiping the drive completely = s long time :)
2. It was completely shut down (even power cables removed) to get KVM back up from lock-up.

I will have to wait until 3TB hdd is wiped before I re-install Win 10.


---

  In some non related topic: I had  been consulted a few weeks back to install a machine with Windows 7 installed (that also had a LinuxMint Trusty install). It was working just perfectly. It offered  to install free genuine Windows 10 upgrade. It already had authentic Windows 7 Home Premium. The over the wire install completed and corrupted all the driver files and some sys files.  I performed a System Restore  (I can't believe I did that) and then it booted into GruB Rescue. I used Grub Rescue CD and did not work. I used Super Grub Rescue and this showed the bootloader and I was able to boot into windows from the CD but still had Grub Rescue on hard boot. I then proceeded to install ubuntu-gnome 16.04 onto the partiton where LinuxMint was. It installed without a hitch, upgraded grub and put the Windows 7  boot loader back in the GruB menu. Whew...!

regards..

---

### Post by ventrical on 2016-01-23
Re: Windows 10 Technical Review

Drive is wiped.  Will try again. Appears it is only good for 1 or 2 runs as date/time auto reset back to present invoking expiry routine.

Regards..

---

### Post by sudodus on 2016-01-23
I think you can set back the computer's clock in a UEFI/BIOS menu and try again. That works for me to keep it working for testing purposes. I need not re-install it.

Edit: In the worst case, disconnect the network: If not connected to the internet, there is no way for the computer 'to know the real date'. But remember that linux is fast to update the time and date, while I think Windows does it only once a week.

---

### Post by sudodus on 2016-04-10
[SIZE=4]Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode[/SIZE]


***1. Current system, seems very stable so far***

The current system contains an installed system, that works in UEFI and BIOS mode. The compressed image files

**Original files:**
dd_Ubuntu_16.04-gamma-UEFI-n-BIOS-12GB.img.xz
dd_Ubuntu_16.04-gamma-UEFI-n-BIOS-[COLOR="#0000FF"]4-pendrive[/COLOR]-12GB.img.xz
dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz
dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz

**Newer files with updated content:**
dd_Ubuntu_16.04.1_2017-05-07_UEFI-n-BIOS-12GB.img.xz
dd_text_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz
dd_dus-lxde_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz

at

[http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

are created according to the following description (written from memory, I may have forgotten some detail).

***Remove or replace the internal drive of the computer you intend to use***. This is because it wants to use /dev/sda for the EFI partition. Boot into the live system, but if the target is also a USB pendrive, plug it in before continuing from the grub menu.

Install this system into  a drive with ***at least 16 GB*** (pendrive, other external drive, or internal drive). If you install to a pendrive it should be [***fast***](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed).


***A. Create a partition table with [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)***

"Advanced: create GUID partition table (skeleton for installing an OS)" 

After that, use ***gparted*** to get a partition table with partitions for EFI, root and swap. See Attachment #1.


***B. Install***

Boot into Ubuntu ***live*** from an ***amd64*** iso file in UEFI mode. (It might work in BIOS mode, but I did not try that.)

Start the installer. At the partitioning window, select ***Something else*** and install into the root partition 3 and swap partition 4.


***C. Create boot-loading systems for external drives***

While running the live system in UEFI mode

```
sudo mkdir /mnt/efi
sudo mount /dev/sdx1 /mnt/efi
sudo mkdir /mnt/root
sudo mount /dev/sdx3 /mnt/root
sudo grub-install --force --removable --no-floppy --boot-directory=/mnt/root/boot  --efi-directory=/mnt/efi /dev/sdx
```

It is best if you manage to make the computer see the target drive as **/dev/sda** (that **x** is **a**).

Reboot the live system into BIOS mode, install ***grub-pc*** and install the bootloader for BIOS mode/media/multimed-2/boot-usb/OneButtonInstaller/dd_Ubuntu_16.04-gamma-UEFI-n-BIOS-4-pendrive-12GB.png

```
sudo apt-get install grub-pc
sudo mkdir /mnt/root
sudo mount /dev/sdx3 /mnt/root
sudo grub-install --force --removable --no-floppy --boot-directory=/mnt/root/boot /dev/sda
```

If some minor detail goes wrong, you may need to repeat the installation of the bootloaders (trial and error).

***X. gpt-fix***

If you clone the compressed iso files, you need to fix the GUID partition table, GPT, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table). I made a shellscript file, [***gpt-fix***](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix), that does the work for you. It works for the cases that I have tested. gpt-fix uses ***gdisk*** under the hood, and you may need to install it. Run gpt-fix in the directory, where you downloaded it (or install it into a directory in $PATH).

```
sudo apt-get install gdisk  # install if necessary

sudo bash gpt-fix /dev/sdx
```

where **x** is the drive letter. The functions ***gpt_zap*** and  ***gpt_fix*** are included in mkusb so the GPT is fixed automatically, if you use ***mkusb 10.6.6*** or a newer version to install from these compressed image files.

-o-

The method described above seems to create a stable system when used in a USB pendrive and also in an SSD connected via eSATA and USB. It is tested in three different laptops, a Toshiba Satellite and an HP Elitebook and a Lenovo X131e and in an ultra-small desktop computer, Intel NUC 6i3SYH, and it has survived such adventures in UEFI and BIOS mode. But we need more testing :-P

It might or might not work to flash the pendrive image directly from a compressed image file to an SSD or HDD drive depending on the sector sizes. The sector size according to parted, 512b/512b, is shown in the screenshot, Attachment #2.

In the HP computer it boots via eSATA, where it also works when installed according to the description above. It is possible to boot from USB via chainloading. (This HP computer does not want to boot directly from USB if there is a GPT partition table).

[HR][/HR]
 or a newer version
***2. Tweak the system***

***A. Decrease wear [COLOR="#0000FF"]for a pendrive[/COLOR]***

Add the mount option noatime in **/etc/fstab**

```
# / was on /dev/sdb3 during installation
UUID=4c518694-d97c-4910-bb7b-eeb6a6b73874  /  ext4  noatime,errors=remount-ro 0  1

```
Do not copy this line. Add 'noatime' to your own line.

It is also possible to remove the swap partition and the swap entry in /etc/fstab in order to avoid wear due to swapping.

Remove journaling

```
sudo tune2fs -O ^has_journal /dev/sdxy
```

where x is the drive letter and y is the partition number of the root partition, in my case **/dev/sda3**.

***B. Move swap and grow root partition***
 or a newer version
Move the swap partition and grow the root partition to use the whole drive. See this link

[http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf](http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf)


***C. Login and password for the system to download***

The system that is installed from the compressed image files has the following user and password

[B]user:     guru
password: changeme

[/B][HR][/HR][B]
*Edit 1: *[/B]It is straight-forward to install from the compressed image file with [***mkusb*** or ***mkusb-nox***]("https://help.ubuntu.com/community/mkusb"). Remember to check with ***md5sum***, that the download of the compressed image file was successful. After this cloning operation you should run [***gpt-fix***](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix) in order to match the gpt data to the current drive size. 

***Edit 2:*** See also [Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

***Edit 3:*** There is a more ***detailed description*** at the following Ubuntu help page: [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

***Edit 4:*** A new compressed image file is uploaded, **dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz**

This image file of the mini system with text screen was made starting from the Ubuntu Server 16.04 64-bit iso file. A minimal system was created as a starting point for any of the Ubuntu flavours including Ubuntu Server.

***Edit 5:*** A new compressed image file is uploaded, **dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz**

This image has the package 'xserver-xorg-video-intel' installed, which makes it work with some old Intel graphics chips.

***Edit 6:*** Two updated compressed image files are uploaded, [edit:] and removed in favour of new versions.

[s][dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz)
[dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz)[/s]

One of these images has the package 'xserver-xorg-video-intel' installed, which makes it work with some old Intel graphics chips.

The functions ***gpt_zap*** and  ***gpt_fix*** are included in mkusb so the GPT is fixed automatically, if you use ***mkusb 10.6.6*** or a newer version to install from these compressed image files. If you use other tools, you need ***gpt-fix*** or to fix the GPT manually with ***gdisk***.

***Edit 7:*** Three updated compressed image files are uploaded,

[dd_Ubuntu_16.04.1_2017-01-17_UEFI-n-BIOS-12GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_16.04.1_2017-01-17_UEFI-n-BIOS-12GB.img.xz)
[dd_text_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz)
[dd_dus-lxde_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_dus-lxde_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz)

---

### Post by sudodus on 2016-04-16
I discovered a bug in gnome-disks.

It is straight-forward to install from a compressed image file from [http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/) with ***mkusb*** or ***mkusb-nox***, which use ***dd*** under the hood. I tried in Lubuntu Xenial daily to ***restore disk image*** with ***gnome-disks*** but it considered the size to be 3.5 GB, when it was 12 GB, so the image was truncated, Bug #1571255

See this link: [gnome-disks truncates a huge image when restoring to a drive from xz-compressed image file](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1571255)

Please mark 'affects me too' if it does :-P

***Edit:*** This bug affects Lubuntu Xenial i386 but not amd64.

---

### Post by sander11 on 2016-04-25
Hi, I'm currently running the image from a few weeks ago with the full Ubuntu 15 install. I've updated the kernel before and manually edited the grub.cfg which allowed it to boot, but it's been a few weeks, will this method continue to work? Does the Ubuntu 16 image require the same grub.cfg editing?

---

### Post by sudodus on 2016-04-25
Welcome to the Ubuntu Forums :-)

Systems installed from the compressed image files

[B]dd_Ubuntu_16.04-gamma-UEFI-n-BIOS-12GB.img.xz
dd_Ubuntu_16.04-gamma-UEFI-n-BIOS-4-pendrive-12GB.img.xz[/B]

at

[http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

do ***not*** require the same grub.cfg editing, so they should be easier to manage. I can update/dist-upgrade them as normal installed systems.

Please post back and tell us how it works for you, if you install from one of these files and update/dist-upgrade the system :-)

---

### Post by sudodus on 2016-05-01
[SIZE=4]A new compressed image file is uploaded: 'dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz'[/SIZE]

This is an image file of a mini system with text screen (no graphic desktop environment). It was made starting from the Ubuntu Server 16.04 64-bit iso file. A minimal system was created as a starting point for any of the Ubuntu flavours including Ubuntu Server.

It is available at [http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

There is a detailed description at [UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

[hr][/hr]
user:     **guru**
password: **changeme**

[hr][/hr]
***gpt-fix***

If you clone the compressed iso files, you need to fix the GUID partition table, GPT, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table). I made a shellscript file

[http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix)

that does the work for you. It works for the cases that I have tested. gpt-fix uses ***gdisk*** under the hood, and you may need to install it. Run gpt-fix in the directory, where you downloaded it (or install it into a directory in $PATH).

```
sudo apt-get install gdisk  # install if necessary

sudo bash gpt-fix /dev/sdx
```

where **x** is the drive letter.

---

### Post by sudodus on 2016-05-15
[SIZE=4]A new compressed image file is uploaded: 'dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz'[/SIZE]

This is an image file of a mini system with text screen (no graphic desktop environment). It was made starting from the Ubuntu Server 16.04 64-bit iso file. A minimal system was created as a starting point for any of the Ubuntu flavours including Ubuntu Server. The difference to the previous version is that this image has the package

**xserver-xorg-video-intel**

installed, which makes it work with some old Intel graphics chips. 

It is available at [http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

There is a detailed description at [UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

[hr][/hr]
user:     **guru**
password: **changeme**

[hr][/hr]
***gpt-fix***

If you clone the compressed iso files, you need to fix the GUID partition table, GPT, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table). I made a shellscript file

[http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix)

that does the work for you. It works for the cases that I have tested. gpt-fix uses ***gdisk*** under the hood, and you may need to install it. Run gpt-fix in the directory, where you downloaded it (or install it into a directory in $PATH).

```
sudo apt-get install gdisk  # install if necessary

sudo bash gpt-fix /dev/sdx
```

where **x** is the drive letter.

---

### Post by ventrical on 2016-05-18
[SIZE=4]A new compressed image file is uploaded: 'dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz'[/SIZE]

It took too long too download and too long to make usb. Anyways .. after I was finished I tried to boot. got grub menu .. then it raced with verbose message and then just kept repeating error:

```

floppy error 5 while reading block 0

```

regards..

---

### Post by sudodus on 2016-05-19
Hi ventrical,

That sounds like a bad failure :-(

- Please tell me what computer you tried to boot with this system.

- Did you try in another computer with a 64-bit system)?

- Did you activate that line in fstab for floppy? In that case, what happens if you comment it out again?

- Did it fail directly when you tried the system in text mode, or did you install any desktop environment before it failed?

[hr][/hr]
***Edit:*** Maybe the following method helps to work around the 'floppy error'

***floppy-off***

This tweak helps, when blkid and fdisk -lu are very slow

[linux-disable-dev-fd0-floppy](http://unix.stackexchange.com/questions/53513/linux-disable-dev-fd0-floppy)

In Ubuntu, the floppy driver is loaded as a module. You can blacklist this module so it doesn't get loaded:

```
echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklist-floppy.conf
sudo rmmod floppy
sudo update-initramfs -u
```

Immediately and upon rebooting, the floppy driver should be banished for good.

---

### Post by ventrical on 2016-05-19
I DID NOT activate any lines. I just did a fresh boot after I created the USB. I did , however get this from 'disks'  after the usb disk was created so there is definetly something wrong with 'disks' or the iso itself. But you did not explain why it takes so long to create  the USB. hmmm .. I'll try again..

Regards..

Edit: I tired again and got the same thing as in screenshot below. Obviously there is somethin wrong with 'disks'.

---

### Post by sudodus on 2016-05-19
How did you install it?

I can only guess why it was slow

1. Maybe the network or Phill's server was busy. The compressed image file size is 343858096 bytes = 328 Mibibytes (bigger than the mini.iso but much smaller than typical iso files).

2. Maybe you installed into a slow USB pendrive. But there could be many reasons. How long did it take to write 7.8 GB?

Examples:

A slow pendrive (5 MB/s) would need 7800/5 s = 1560 s = 26 minutes
A fast [USB3] pendrive in a USB 2 port (25 MB/s) : 312 s = 5 min 12 s
A fast USB3 pendrive in a USB 3 port (78 MB/s) : 100 s = 1 min 40 s 

3. I use mkusb to install from the compressed image file to a drive (internal or external), and I know that there is a bug in Disks (32-bit gnome-disks), that makes it fail to install alias 'restore' from xz-compressed image files. See this link: [Post #71](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13471313#post13471313)

and this link: [gnome-disks truncates a huge image when restoring to a drive from xz-compressed image file](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1571255)

Please mark 'affects me too' if it does :-P

4. Since the download was slow, maybe there were errors too. Did you check the md5sum?

```
$ md5sum dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz
706fdab95c4e24f60b094e253a3ec157  dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz
```

---

### Post by ventrical on 2016-05-19
If you looked at my screenshot you would see Kingston Data Traveller 3.0

I installed it using 'disks' on xenial install. There were no special circumstances..

Used high end Intel MoBo.

```

ventrical@ventrical-MS-7850:~/Downloads$ md5sum dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz
706fdab95c4e24f60b094e253a3ec157  dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz
ventrical@ventrical-MS-7850:~/Downloads$ 


```

Tried it on another install .. no go.

I did get BusyBox on one 64bit PC but that was it.


Regards..

---

### Post by sudodus on 2016-05-19
Kingston pendrives are known to be reliable, but some of them are rather slow, even when they are marked USB 3. I think the flash memory is slow in some of them. In general, it is hard to find fast pendrives, that are smaller than 16 GB, and yours is 8 GB. (I have both fast and slow Kingston USB 3 pendrives.)

I suspect that Disks cannot do the job correctly for you. Please try to install with mkusb :-)

---

### Post by sudodus on 2016-05-19
Concerning your problem:

First I did not understand your problem, but now I think I know, what is the problem: You need to fix the GUID partition table after cloning to a different size. It is easily done with gpt-fix according to this link, which I described in post #70, but I have failed to repeat it in later posts. Sorry for that :oops:

***gpt-fix***

If you clone the compressed iso files, you need to fix the GUID partition table, GPT, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table). I made a shellscript file

[http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix)

that does the work for you. It works for the cases that I have tested. gpt-fix uses ***gdisk*** under the hood, and you may need to install it. Run gpt-fix in the directory, where you downloaded it (or install it into a directory in $PATH).

```
sudo apt-get install gdisk  # install if necessary

sudo bash gpt-fix /dev/sdx
```

where **x** is the drive letter.

[hr][/hr]
Concerning speed with a fast USB 3 drive in a USB 2 port:

```
$ [COLOR="#0000FF"]**sudo mkusb-nox dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz**[/COLOR]
Do you want to clone dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz to a mass storage device (typically USB drive)? (y/n)
y
***  WARNING: the device will be completely overwritten      ***
***  quit with (q)                                           ***
***  Unmount the device if mounted  ****************************
 
Name: ata-SAMSUNG_HD322HJ        Dev: /dev/sda  Size: 320GB
Name: ata-OCZ-AGILITY3           Dev: /dev/sdb  Size: 60GB
Name: ata-WDC_WD1003FBYZ-010FB0  Dev: /dev/sdc  Size: 1000GB
Name: usb-SanDisk_Extreme        Dev: /dev/sdd  Size: 15694MB
Live drive: /dev/sda
 
---> 1: install to USB: SanDisk_Extreme Dev: /dev/sdd Size: 15694MB
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
g
1: source: dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz
   target: USB: SanDisk_Extreme        Dev: /dev/sdd  Size: 15694MB
 Final checkpoint 
Please check again that it is the correct target device! (y/n)
y
 
Installing dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz to /dev/sdd ...
 
xzcat "dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz" | pv -s 7799308288 | dd bs=4096  of=/dev/sdd
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
7,26GiB 0:04:21 [28,4MiB/s] [=========================================================>] 100%            
1904128+0 records in
1904128+0 records out
7799308288 bytes (7,8 GB, 7,3 GiB) copied, [COLOR="#0000FF"]**265,903 s, 29,3 MB/s**[/COLOR]
Syncing the device ...
Done :-)
```

---

### Post by QDR06VV9 on 2016-05-19
I used MKUSB to do my install and chose the intel-UEFI download after a bit of confusion :lolflag: trying to figure the password all my fault of course.
But long story short all is good...I have not run it with any significant time period yet...but so far so good.
For my install I used a San Disk Ultra 32 Gig not the fastest but suitable for this test.
Oh and I forgot to mention I used a Acer 5750 Laptop i3 CPU 4 Gigs ram and Intel 3000 Graphics

---

### Post by sudodus on 2016-05-19
@ *runrickus*, 

I'm glad to read that it works for you in an Acer. :-)

- Did you run in UEFI or BIOS mode?

- Did you install any desktop environment?

---

### Post by QDR06VV9 on 2016-05-19
In UEFI and yes i installed Mate as a  desktop environment.
As soon as i get some of my work done here I am also going to install it to the same laptop (Acer)
And so far I have very much liked the way you have this set-up..(Interface)
But I might not be as picky as some..;)
Thanks sudodus

---

### Post by sudodus on 2016-05-19
You are welcome :-)

What do you think of the idea to integrate ***gpt-fix*** into ***mkusb***? That would remove the risk to forget about it.

---

### Post by QDR06VV9 on 2016-05-19
> What do you think of the idea to integrate ***gpt-fix*** into ***mkusb***? That would remove the risk to forget about it.
I think that makes perfect sense...I was glad to see that you had already explained this here before hand though.

---

### Post by ventrical on 2016-05-20
I have mkusb on some installs but not all installs. I am trying to stick to the testing methods asked by developers, to use 'disks' to restore images. 'disks' is working just fine with other isos so I cannot help but ask why we have to use mkusb. This is doing a benchmark with a fixed set of conditions. These images should be able to be restored with 'disks'. Could it be that there is something in the way the images are formatted that is preventing 'disks' from restoring these images?



Regards..

---

### Post by sudodus on 2016-05-20
Hi again *ventrical*,

***Disks*** works with iso files. Such files are plain images without any compression. Disks has a built-in system to manage compressed image files, but if I understand correctly, there is a bug in Disks in 32-bit systems. This bug affects files compressed with xz and above a certain size (of the original uncompressed size).

To use other methods than ***mkusb*** with compressed image files, please try a two step procedure (or find another tool that works in one step),

1 - uncompress the file with ***xzcat*** or another tool, that can manage big files. This uncompressed file will be 7.8 GB.

```
xzcat -c dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz > dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img
```

2 - install alias restore the uncompressed file with the tool you prefer, in this case ***Disks***.

I think you will succeed that way.

-o-

***But as I described in post #82, I am no longer sure that the bug in Disks caused this problem.***

If you were using Disks in a 64-bit system, you were not affected by that bug, and in any case, you must use [gpt-fix](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix) or use ***gdisk*** directly to fix the GPT. (Since GPT puts/wants a backup partition table at the very end of the partition, cloning to a different drive size, bigger or smaller, makes it necessary to fix it.)

---

### Post by sudodus on 2016-05-20
> **runrickus said:**
>  [QUOTE=sudodus;13491864]
What do you think of the idea to integrate gpt-fix into mkusb? That would remove the risk to forget about it. 

I think that makes perfect sense...I was glad to see that you had already explained this here before hand though.[/QUOTE]

Done and uploaded to the ppa:mkusb/unstable: mkusb 10.6.4 :-)

In the same version I fixed a bug discovered by the Ubuntu user *yman* recently. Now mkusb and mkusb-nox can use a path with spaces and some other special characters. It worked with the filename before - it is extended to the directory part of path.

---

### Post by sudodus on 2016-05-20
High-lights from **mkusb.log**

```
start [mkusb 10.6.4] @ 2016-05-21 00:41:49
---------------------------------------------------------------------------
...
Installing /media/multimed-2/boot-usb/OneButtonInstaller/xz/dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz to /dev/sdd ...
---------------------------------------------------------------------------
do_n_show:
xzcat "dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz" | pv -n -s 7799308288 | dd bs=4096  of=/dev/sdd
 
( xzcat "dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz" | pv -n -s 7799308288 | dd bs=4096  of=/dev/sdd && echo 'Done' > /dev/stderr ) 2>&1 || ( echo '# failed';sleep 1 )
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
'pv %'; 'dd final output'
...
1904128+0 records in
1904128+0 records out
7799308288 bytes (7,8 GB, 7,3 GiB) copied, 269,21 s, 29,0 MB/s
Done
do_n_show: Work done
---------------------------------------------------------------------------
Syncing the device ...
Done :-)
[COLOR="#0000FF"]gpt_fix: success :-)[/COLOR]
Cleanup after mkusb finished :-)
---------------------------------------------------------------------------
Total time used [by mkusb] = 332 s; 00:05:32
login attempt 1

```

---

### Post by ventrical on 2016-05-23
Ok.. tried mkusb (recent) and still get  error on one machine , floppy -5 and Busy Box (initramfs) on the other machine.

Regards..
Edit: If I have time later I will try the other image.

---

### Post by sudodus on 2016-05-23
I guess you tried with the compressed image file **dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz**

It seems that it is not as portable as I have been thinking. You have found two computers where it does not work. Please describe these computers, and maybe we can find out why. Maybe something can be done to fix it, maybe these computers need some driver, that is not installed in this kind of already installed system.

It is not the result I had hoped to get :-( but it is an important result. Thank you for testing and reporting the result :-)

---

### Post by ventrical on 2016-05-23
#1

```

ventrical@ventrical-MS-7798:~$ inxi -Fxz
System:    Host: ventrical-MS-7798 Kernel: 4.4.0-23-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           Bios: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12399
           clock speeds: max: 3100 MHz 1: 3100 MHz 2: 3087 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-23-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (10.1% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB
Partition: ID-1: / size: 53G used: 7.7G (16%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 4.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 229 Uptime: 0 min Memory: 616.5/3814.3MB
           Init: systemd Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.35 
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2016-05-23
#2
```

ventrical@ventrical-luntiy-betatest:~$ inxi -Fxz
System:    Host: ventrical-luntiy-betatest Kernel: 4.2.0-36-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity 7.3.3 (Gtk 3.16.7-0ubuntu3)
           Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.17.2 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1440x900@59.89hz
           GLX Renderer: GeForce GT 610/PCIe/SSE2
           GLX Version: 4.2.0 NVIDIA 304.131 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.2.0-36-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (70.6% used)
           ID-1: /dev/sda model: Hitachi_HDS72168 size: 80.0GB
Partition: ID-1: / size: 72G used: 51G (76%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 2.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.5C mobo: 30.0C gpu: 0.0:34C
           Fan Speeds (in rpm): cpu: 4299 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 185 Uptime: 1 min Memory: 444.9/3008.1MB
           Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.421) inxi: 2.2.16 
ventrical@ventrical-luntiy-betatest:~$ 

```

---

### Post by sudodus on 2016-05-23
***A. Check that the GUID partition table is fixed and correct***

Which version of mkusb did you use? If older than 10.6.4, did you use gpt-fix?

What happens, if you run gdisk 'manually'?

```
sudo gdisk /dev/sdx
```

where x is the drive letter of 'the USB drive with the system from dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz' and test with **v** (verify)? Is the GPT good or bad?

If problems, try to fix the GPT either with gpt-fix or manually.


***B. With a good GPT***

1. I have no idea why it starts talking about floppy in the first computer. It seems to fail in that computer.

2. I have a guess about the second computer: the nvidia graphics. Maybe it works with the boot option **nomodeset**.

---

### Post by ventrical on 2016-05-23
> **sudodus said:**
> ***A. Check that the GUID partition table is fixed and correct***

Which version of mkusb did you use? If older than 10.6.4, did you use gpt-fix?

What happens, if you run gdisk 'manually'?

```
sudo gdisk /dev/sdx
```

where x is the drive letter of 'the USB drive with the system from dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz' and test with **v** (verify)? Is the GPT good or bad?

If problems, try to fix the GPT either with gpt-fix or manually.


***B. With a good GPT***

1. I have no idea why it starts talking about floppy in the first computer. It seems to fail in that computer.

2. I have a guess about the second computer: the nvidia graphics. Maybe it works with the boot option **nomodeset**.


```

ventrical@ventrical-luntiy-betatest:~$ sudo gdisk /dev/sdb
[sudo] password for ventrical: 
GPT fdisk (gdisk) version 1.0.0

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
*********************************

```

---

### Post by ventrical on 2016-05-23
> **sudodus said:**
> ***A. Check that the GUID partition table is fixed and correct***

Which version of mkusb did you use? ****

Is,

---

### Post by sudodus on 2016-05-23
You need to fix the GPT. I *think* that it works with gpt-fix, but I am not sure; it is part of the test. Maybe it fails, and you have to do something else, in that case manually with gdisk.

***gpt-fix:***

```
#!/bin/bash

user=$(whoami)
if [ "$user" != "root" ] || ! test -b "$1"
then
 echo ""
 echo "Usage:   sudo $0 <device>"
 echo ""
 echo "Example: sudo $0 /dev/sdx"
 echo ""
 echo "$0 needs 'gdisk'"
 echo ""
 exit
fi


echo \
"v
q" \
| gdisk "$1" 2>/dev/null |grep -e 'GPT: damaged' -e 'Problem:'
if [ $? -ne 0 ]
then
 echo "The GPT seems fine or there is no GPT on '$1'"
 exit
fi

umount "$1"?
df -h | grep "$1"

if [ $? -ne 0 ]
then
 echo "--------------------------------------------------"
 read -p "Do you want to fix the GPT on '$1'? (y/N) " ans
 if [ "$ans" == "y" ]
 then

echo \
"v
x
e
r
d
w
y" \
| gdisk "$1"

 fi
fi

```

If you clone a compressed iso file with a GUID partition table, GPT, you must fix it, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table). I made a shellscript file, gpt-fix, that does the work for you. It works for the cases that I have tested. gpt-fix uses gdisk under the hood. There is a slightly modified version in mkusb version 10.6.4, but you need not redo the whole installation. It should be enough to run gpt-fix or run a few commands manually in gdisk.

---

### Post by ventrical on 2016-05-23
> **sudodus said:**
> Concerning your problem:

First I did not understand your problem, but now I think I know, what is the problem: You need to fix the GUID partition table after cloning to a different size. It is easily done with gpt-fix according to this link, which I described in post #70, but I have failed to repeat it in later posts. Sorry for that :oops:

***gpt-fix***

If you clone the compressed iso files, you need to fix the GUID partition table, GPT, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table). I made a shellscript file

[http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix)

that does the work for you. It works for the cases that I have tested. gpt-fix uses ***gdisk*** under the hood, and you may need to install it. Run gpt-fix in the directory, where you downloaded it (or install it into a directory in $PATH).

```
sudo apt-get install gdisk  # install if necessary

sudo bash gpt-fix /dev/sdx
```

where **x** is the drive letter.

[HR][/HR]
Concerning speed with a fast USB 3 drive in a USB 2 port:

```
$ [COLOR=#0000FF]**sudo mkusb-nox dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz**[/COLOR]
Do you want to clone dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz to a mass storage device (typically USB drive)? (y/n)
y
***  WARNING: the device will be completely overwritten      ***
***  quit with (q)                                           ***
***  Unmount the device if mounted  ****************************
 
Name: ata-SAMSUNG_HD322HJ        Dev: /dev/sda  Size: 320GB
Name: ata-OCZ-AGILITY3           Dev: /dev/sdb  Size: 60GB
Name: ata-WDC_WD1003FBYZ-010FB0  Dev: /dev/sdc  Size: 1000GB
Name: usb-SanDisk_Extreme        Dev: /dev/sdd  Size: 15694MB
Live drive: /dev/sda
 
---> 1: install to USB: SanDisk_Extreme Dev: /dev/sdd Size: 15694MB
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
g
1: source: dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz
   target: USB: SanDisk_Extreme        Dev: /dev/sdd  Size: 15694MB
 Final checkpoint 
Please check again that it is the correct target device! (y/n)
y
 
Installing dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz to /dev/sdd ...
 
xzcat "dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz" | pv -s 7799308288 | dd bs=4096  of=/dev/sdd
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
7,26GiB 0:04:21 [28,4MiB/s] [=========================================================>] 100%            
1904128+0 records in
1904128+0 records out
7799308288 bytes (7,8 GB, 7,3 GiB) copied, [COLOR=#0000FF]**265,903 s, 29,3 MB/s**[/COLOR]
Syncing the device ...
Done :-)
```


gpt-fix won't find:

```

ventrical@ventrical-luntiy-betatest:~$ sudo bash gpt-fix /dev/sdb
bash: gpt-fix: No such file or directory
ventrical@ventrical-luntiy-betatest:~$ sudo -i
root@ventrical-luntiy-betatest:~# sudo bash gpt-fix /dev/sdb
bash: gpt-fix: No such file or directory
root@ventrical-luntiy-betatest:~# 

```

---

### Post by sudodus on 2016-05-23
> **ventrical said:**
> Is, [mkusb 10.6.4] 

***gpt_fix*** built into mkusb is not doing its job to fix the GPT. I have to make that better - first identify the conditions, when it goes wrong and then make it work also in those cases.

---

### Post by sudodus on 2016-05-23
1. Is gpt-fix in the current directory? Then **sudo bash gpt-fix /dev/sdx** should work.

2. Please post the output of the following commands for the drive with the system we are trying to make bootable.

```
sudo lsblk -fm /dev/sdx

sudo parted /dev/sdx print
```

---

### Post by ventrical on 2016-05-23
> **sudodus said:**
> 1. Is gpt-fix in the current directory? 
Not sure. This should be global, don't you think?


> 
Then **sudo bash gpt-fix /dev/sdx** should work.

2. Please post the output of the following commands for the drive with the system we are trying to make bootable.

```
sudo lsblk -fm /dev/sdx

sudo parted /dev/sdx print
```


and

```

ventrical@ventrical-luntiy-betatest:~$ sudo lsblk -fm /dev/sdb
[sudo] password for ventrical: 
NAME FSTYPE LABEL UUID MOUNTPOINT NAME  SIZE OWNER GROUP MODE
sdb                               sdb   7.3G root  disk  brw-rw----
ventrical@ventrical-luntiy-betatest:~$ sudo parted /dev/sdb print
Error: Invalid argument during seek for read on /dev/sdb
Retry/Ignore/Cancel? r                                                    
Error: Invalid argument during seek for read on /dev/sdb
Retry/Ignore/Cancel? i                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? o                                                              
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 7862MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
ventrical@ventrical-luntiy-betatest:~$ 



```

---

### Post by ventrical on 2016-05-23
sigh .. what directory is gpt-fix in?

---

### Post by ventrical on 2016-05-23
> **sudodus said:**
> ***gpt_fix*** built into mkusb is not doing its job to fix the GPT. I have to make that better - first identify the conditions, when it goes wrong and then make it work also in those cases.

uhmmm  it perhaps is not finding the file in current ?? whatever that may be. Is gpt-fix not linked to a global PATH?
it is certainly  not finding it in root either way.
regards..

---

### Post by ventrical on 2016-05-23
> **sudodus said:**
> ***gpt_fix*** built into mkusb is not doing its job to fix the GPT. I have to make that better - first identify the conditions, when it goes wrong and then make it work also in those cases.

As I was watching the script file it never even called gpt-fix.

regards..

---

### Post by sudodus on 2016-05-23
> **ventrical said:**
> Not sure. This should be global, don't you think?


*No*, you have to create it and use it locally or install it manually.
> 
[QUOTE]

Then **sudo bash gpt-fix /dev/sdx** should work.

2. Please post the output of the following commands for the drive with the system we are trying to make bootable.

```
sudo lsblk -fm /dev/sdx

sudo parted /dev/sdx print
```


and

```

ventrical@ventrical-luntiy-betatest:~$ sudo lsblk -fm /dev/sdb
[sudo] password for ventrical: 
NAME FSTYPE LABEL UUID MOUNTPOINT NAME  SIZE OWNER GROUP MODE
sdb                               sdb   7.3G root  disk  brw-rw----
ventrical@ventrical-luntiy-betatest:~$ sudo parted /dev/sdb print
Error: Invalid argument during seek for read on /dev/sdb
Retry/Ignore/Cancel? r                                                    
Error: Invalid argument during seek for read on /dev/sdb
Retry/Ignore/Cancel? i                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? o                                                              
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 7862MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
ventrical@ventrical-luntiy-betatest:~$ 



```[/QUOTE]

The partition table is borked. Neither ***lsblk*** nor ***parted*** can find it. The USB drive should be big enough, it is more than 7800 MB. It is hard to tell now, what happened, or when it happened. Directly after cloning ***lsblk*** should be able to see the partitions (even when the GPT backup table is missing or wrong).

---

### Post by ventrical on 2016-05-23
I am using 'disks' to do a 'slow' format. We'll see. :)

---

### Post by sudodus on 2016-05-23
***gpt-fix*** is a separate script file (you find it in post #99). You run it manually (or if you prefer, do the repair commands manually in gdisk).

***gpt_fix*** is a function within mkusb (and no separate file). It should be called near the end of the execution of mkusb (after the cloning process, if parted sees a corrupted GPT).

---

### Post by sudodus on 2016-05-23
> **ventrical said:**
> I am using 'disks' to do a 'slow' format. We'll see. :)

It will be interesting to see the result. It may work better with a clean slow formatted alias wiped drive, and in that case gpt-fix is not robust enough to manage the situation, when there are 'certain disturbing data'.

I have tested with three fast USB 3 pendrives and one SSD (in an external box, connected via USB (2 and 3) and via eSATA. I did *not* wipe them before cloning.

-o-

After these problems, I try to see alternatives, that might be easier.

I will try using an MSDOS partition table instead of GPT. Windows does not want that in UEFI mode, but it should work with linux, and for external drives, it might be a good alternative, that should still work in both UEFI and BIOS mode. This will take some time to do ...

---

### Post by ventrical on 2016-05-23
after format..
```

ventrical@ventrical-luntiy-betatest:~$ sudo gdisk /dev/sdb
[sudo] password for ventrical: 
GPT fdisk (gdisk) version 1.0.0

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Command (? for help): 

Command (? for help): 

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): v

No problems found. 15356093 free sectors (7.3 GiB) available in 1
segments, the largest of which is 15356093 (7.3 GiB) in size.

Command (? for help): 

```


now mkusb try..

---

### Post by ventrical on 2016-05-23
Same thing... busy box .. etc..

I did not see fix-gpt  working in background etc..

---

### Post by ventrical on 2016-05-23
right back where I started... so it must be the image..?

```

[sudo] password for ventrical: 
GPT fdisk (gdisk) version 1.0.0

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): 

```

 I'll be back later..

regards..

---

### Post by sudodus on 2016-05-23
But you have the correct md5sum as the compressed image file, that works for me.

Can you try now to

1. run the commands

```
sudo lsblk -fm /dev/sdx

sudo parted /dev/sdx print
```

2. run gpt-fix (the separate script from post #99)

3. run again

```
sudo lsblk -fm /dev/sdx

sudo parted /dev/sdx print
```

4. run gpt-fix again

5. try to boot from the drive

---

### Post by ventrical on 2016-05-23
Nope. No go .. All I am getting right now are snakes and ladders :) I'll have to try again later. 

Thanks 

Regards..

---

### Post by sudodus on 2016-05-23
I'm making another attempt to make it work with GPT: The function ***gpt_zap*** in mkusb clears old GPT structures (partition table and backup partition table) before the cloning starts. Then ***gpt_fix*** should not be confused, when it is run after the cloning. It is uploading now to Launchpad, so wait a while to get ***mkusb version 10.6.5*** ...

---

### Post by sudodus on 2016-05-24
> **ventrical said:**
> Nope. No go .. All I am getting right now are snakes and ladders :) I'll have to try again later. 

Thanks 

Regards..

***mkusb 10.6.5*** is uploaded to ppa:mkusb/unstable now.

[hr][/hr]
I don't understand. It seems to me, that the USB pendrive 'only pretends' that it is being written to, but that at least some part of it refuses to be changed. But that is very unlikely. It could be worthwhile to try with another pendrive just in case.

We will not succeed until there is a good GUID partition table after cloning. So either the built-in sequence in mkusb 10.6.5 should do it:

*gpt_zap - cloning - gpt_fix*

or it should be done manually with ***gdisk***.

When there is a good GUID partition table in the pendrive, chances are that at least some of your 64-bit computers can boot from it. Maybe not all of them.

---

### Post by ventrical on 2016-05-24
> **sudodus said:**
> ***mkusb 10.6.5*** is uploaded to ppa:mkusb/unstable now.

[HR][/HR]
I don't understand. It seems to me, that the USB pendrive 'only pretends' that it is being written to, but that at least some part of it refuses to be changed. 

Yes.. 'pretends'. It is not changing. btw the pendrive I am using  already had one of your images (not sure which one) cloned on it using mkusb a couple months back.

> 
 But that is very unlikely. It could be worthwhile to try with another pendrive just in case.

Yes .. this is sound reasoning but I am trying to avoid this.

> 
We will not succeed until there is a good GUID partition table after cloning. So either the built-in sequence in mkusb 10.6.5 should do it:

*gpt_zap - cloning - gpt_fix*

or it should be done manually with ***gdisk***.

When there is a good GUID partition table in the pendrive, chances are that at least some of your 64-bit computers can boot from it. Maybe not all of them.

I am confident in my hardware. I'll have to take a back-step and  review and see if I can learn this logic better.

Regards..

---

### Post by ventrical on 2016-05-24
Tried another USB drive + new mkusb and same problem on both machines.  I do not think gpt-fix is working or I do not have it installed. I tried to run the script but it will not run or I am doing it wrong.

 I'll try again to download other image.
edit:

 I seen gpt_zap in log at beggining but not gpt_fix and end of cloning
.
regards..

---

### Post by sudodus on 2016-05-24
I'm sure you know your computers well, and that they are working correctly :-)

It could be that the pendrive is failing. You could make a new partition table and file system, write files to it and check if you can read those files from it. In order to avoid the problem of reading from cache, you should unmount it and move it to another computer to check that you can read what you wrote.

It could be that part of the pendrive is good and it is used for the head end, but some addresses are pointing to bad memory cells or no cells at all. Maybe there are not enough good cells to allocate to the tail end position of the partition table. If this is the case, it can work well to clone iso files into it. The Ubuntu family iso files will occupy less than 2 GB near the head end, and there is no checking of any backup partition table at the end of the drive.

I have also heard of fake USB drives - some manufacturer is imitating well-known brand pendrives but they are actually smaller or slower than specified, or simply not working correctly.

---

### Post by sudodus on 2016-05-24
> **ventrical said:**
> Tried another USB drive + new mkusb and same problem on both machines.  I do not think gpt-fix is working or I do not have it installed. I tried to run the script but it will not run or I am doing it wrong.

 I'll try again to download other image.
edit:

 I seen gpt_zap in log at beggining but not gpt_fix and end of cloning
.
regards..

In which version of Ubuntu are you running these tests?

I am working in Xenial now, and I do some testing in other versions (the previous still supported Precise, Trusty and Wily plus Yakkety). I can set up a system with the same version that you are using. That way I should get the same versions of the tools, that are used by mkusb.

For example, parted is checking if gpt_fix needs to run after the cloning. If your version of parted does not behave like I expect, it can cause your problem.

***Edit:*** I have a clue now: ***parted*** is acting differently in Trusty and Xenial, when it sees errors. So I will change the logic around ***gpt_fix*** to work without using parted. When I'm ready, I will upload a new version, that has fixed that issue. Let us hope that it will work for you :-)

---

### Post by sudodus on 2016-05-24
***mkusb version 10.6.6*** 'Hastings' is uploaded for Trusty now, and it is uploading for the other versions of Ubuntu. I tested and it works for me in Trusty, where there was a problem because I had not tested and found that parted is acting differently in Trusty and Xenial. ***gpt_fix*** is invoked as it should.

---

### Post by ventrical on 2016-05-24
I am doing my tests (mkusb) on fully updated install of wily. I am using 'disks' on trusty and xenial in other instances.

regards..

---

### Post by ventrical on 2016-05-24
> **sudodus said:**
> ***mkusb version 10.6.6*** 'Hastings' is uploaded for Trusty now, and it is uploading for the other versions of Ubuntu. I tested and it works for me in Trusty, where there was a problem because I had not tested and found that parted is acting differently in Trusty and Xenial. ***gpt_fix*** is invoked as it should.

I have mkusb on an Intel form factor with vivid (since I started mkusb). 

I might have some time today.

regards..

---

### Post by ventrical on 2016-05-24
Kingston data traveller on my  vivid install.

```

ventrical@ventrical-MS-7798:~$ cd Desktop
ventrical@ventrical-MS-7798:~/Desktop$ sudo bash gpt-fix /dev/sdb1
The GPT seems fine or there is no GPT on '/dev/sdb1'
ventrical@ventrical-MS-7798:~/Desktop$ sudo bash gpt-fix /dev/sdb
The GPT seems fine or there is no GPT on '/dev/sdb'
ventrical@ventrical-MS-7798:~/Desktop$ 

```

I did not know we had to copy (download) script and compile fix-gpt.  yes i see .. my bad .. anyways I am downloading the other image (non-intel) and see whats up.

---

### Post by sudodus on 2016-05-24
***mkusb version 10.6.6*** 'Hastings' is uploaded for all versions of Ubuntu now. I suggest that you try it. If you don't want to waste time, you can try to expand and install the following file. (It expands to a GPT with an almost empty partition, and I have used it to test that gpt_zap and gpt_fix work (It is much faster than to test with a full operating system.)

It contains a 64 MB ext4 partition with the file 'greeting.txt'.

File to test: [dd_no-biggie-68MB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_no-biggie-68MB.img.xz)

and the md5sum: [dd_no-biggie-68MB.img.xz.md5](http://phillw.net/isos/linux-tools/compressed-images/dd_no-biggie-68MB.img.xz.md5)

```
[COLOR="#0000FF"]$ sudo mkusb-nox dd_no-biggie-68MB.img.xz[/COLOR]
Do you want to clone dd_no-biggie-68MB.img.xz to a mass storage device (typically USB drive)? (y/n)
y
***  WARNING: the device will be completely overwritten      ***
***  quit with (q)                                           ***
***  Unmount the device if mounted  ****************************
 
Name: ata-SAMSUNG_HD322HJ        Dev: /dev/sda  Size: 320GB
Name: ata-OCZ-AGILITY3           Dev: /dev/sdb  Size: 60GB
Name: ata-WDC_WD1003FBYZ-010FB0  Dev: /dev/sdc  Size: 1000GB
Name: usb-SanDisk_Extreme        Dev: /dev/sdd  Size: 15694MB
Live drive: /dev/sda
 
---> 1: install to USB: SanDisk_Extreme Dev: /dev/sdd Size: 15694MB
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
g
1: source: dd_no-biggie-68MB.img.xz
   target: USB: SanDisk_Extreme        Dev: /dev/sdd  Size: 15694MB
 Final checkpoint 
Please check again that it is the correct target device! (y/n)
y
 
Installing dd_no-biggie-68MB.img.xz to /dev/sdd ...
 
[COLOR="#B22222"]gpt_zap: done[/COLOR]
xzcat "dd_no-biggie-68MB.img.xz" | pv -s 68157440 | dd bs=4096  of=/dev/sdd
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
  65MiB 0:00:00 [ 255MiB/s] [==================================================================================>] 100%            
16640+0 records in
16640+0 records out
68157440 bytes (68 MB, 65 MiB) copied, [COLOR="#B22222"]2,52789 s[/COLOR], 27,0 MB/s
[COLOR="#B22222"]gpt_fix: done :-)[/COLOR]
Syncing the device ...
Done :-)

$ [COLOR="#0000FF"]sudo mount /dev/sdd1 /mnt[/COLOR]

$ [COLOR="#0000FF"]sudo lsblk -fm /dev/sdd[/COLOR]
NAME   FSTYPE LABEL     UUID                                 MOUNTPOINT NAME    SIZE OWNER GROUP MODE
sdd                                                                     sdd    14,6G root  disk  brw-rw----
&#9492;&#9472;sdd1 ext4   no-biggie a7345d97-7b39-4f67-9e8d-15fb02a02127 /mnt       &#9492;&#9472;sdd1   64M root  disk  brw-rw----

$ [COLOR="#0000FF"]sudo parted /dev/sdd print[/COLOR]
[sudo] password for olle: 
Modell: SanDisk Extreme (scsi)
Disk /dev/sdd: 15,7GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: [COLOR="#B22222"]gpt[/COLOR]
Disk Flags: 

Nummer  Början  ****    Storlek  Filsystem  Namn  Flaggor
 1      1049kB  68,2MB  67,1MB   ext4

$ [COLOR="#0000FF"]ls -l /mnt[/COLOR]
totalt 13
drwx------ 2 root root 12288 maj 24 16:28 lost+found
-rw-r--r-- 1 root root    16 maj 24 16:30 greeting.txt

$ [COLOR="#0000FF"]cat /mnt/greeting.txt [/COLOR]
Hello World :-)
```

---

### Post by sudodus on 2016-05-24
> **ventrical said:**
> Kingston data traveller on my  vivid install.

```

ventrical@ventrical-MS-7798:~$ cd Desktop
ventrical@ventrical-MS-7798:~/Desktop$ sudo bash gpt-fix /dev/sdb1
The GPT seems fine or there is no GPT on '/dev/sdb1'
ventrical@ventrical-MS-7798:~/Desktop$ sudo bash gpt-fix /dev/sdb
The GPT seems fine or there is no GPT on '/dev/sdb'
ventrical@ventrical-MS-7798:~/Desktop$ 

```

I did not know we had to copy (download) script and compile fix-gpt.  yes i see .. my bad .. anyways I am downloading the other image (non-intel) and see whats up.

We are both making progress :-) You with gpt-fix, and I with the built-in gpt_fix in mkusb. As usual, things are a bit more complicated than they look in the beginning. I think that you will soon have a working system installed from ***dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz***. And you have made me improve mkusb for this purpose.

-o-

If we have some energy left, maybe we will improve the system in the compressed image file too :-P

-o-

***Edit:*** I have tested mkusb and mkusb-nox in Precise, Trusty, Wily, Xenial and Yakkety. gpt_zap and gpt_fix are invoked and work (for me in my computers).

---

### Post by ventrical on 2016-05-24
Works !!!!!!!!!!!!!!


ahh ahhh .. awesome :)  I can't believe you did this !!

Kudos..

---

### Post by sudodus on 2016-05-24
That's great ventrical,

Thanks a lot for your patience and endurance :-)

From which compressed iso file did you make it work? A text based mini system or Ubuntu or Lubuntu, with or without the intel package? Or have more than one system started to work now? And in which computers? :-P

---

### Post by ventrical on 2016-05-24
I am using:

```

[SIZE=4][SIZE=2]A new compressed image file is uploaded: 'dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz'[/SIZE]
[/SIZE]
```[SIZE=4]

[SIZE=2]and I am currently downloading Mate DE.

Give me time to play with it[/SIZE] :)


 [SIZE=2]I got some ideas about unity8 .. etc..[/SIZE]

[/SIZE]

---

### Post by sudodus on 2016-05-24
I'm looking forward to it :-P

I will share the tools and methods to make these compressed image files, just tell me.

---

### Post by sudodus on 2016-05-24
So you are keeping an eye on own adventures, *runrickus* :-D

---

### Post by ventrical on 2016-05-24
I installed Mate DE and got Gnome3!! After I installed Mate there was no desktop so I installed gdm:

```

sudo apt-get install gdm

```

then

```

sudo service gdm start

```

and 'guru' gdm greeter came up , logged on  gnome3 desktop.. works great. uhh ummm.. I think it would be neat to use something small like razorqt because Mate is so huge to install.

Lots of questions .. but later  :)

regards...

---

### Post by ventrical on 2016-05-24
Kewl eh? :)

```

guru@uefi-n-bios:~$ inxi -Fxz
System:    Host: uefi-n-bios Kernel: 4.4.0-21-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Gnome 3.18.4 (Gtk 3.18.9-1ubuntu3)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           Bios: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12399
           clock speeds: max: 3100 MHz 1: 3100 MHz 2: 3100 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 driver: N/A
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-21-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 7.9GB (52.0% used)
           ID-1: USB /dev/sda model: DataTraveler_3.0 size: 7.9GB temp: 0C
Partition: ID-1: / size: 6.4G used: 3.4G (56%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 0.54GB used: 0.00GB (0%) fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 189 Uptime: 1:38 Memory: 873.9/3814.3MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.421) inxi: 2.2.35 
guru@uefi-n-bios:~$ 

```

and

```

guru@uefi-n-bios:~$ inxi -Fxz
System:    Host: uefi-n-bios Kernel: 4.4.0-22-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Gnome 3.18.4 (Gtk 3.18.9-1ubuntu3)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 driver: N/A
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-22-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 87.9GB (4.7% used)
           ID-1: /dev/sda model: Hitachi_HDS72168 size: 80.0GB
           ID-2: USB /dev/sdb model: DataTraveler_3.0 size: 7.9GB
Partition: ID-1: / size: 6.4G used: 3.4G (56%) fs: ext4 dev: /dev/sdb3
           ID-2: swap-1 size: 0.54GB used: 0.00GB (0%) fs: swap dev: /dev/sdb4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 35.5C mobo: 27.0C gpu: 27.0
           Fan Speeds (in rpm): cpu: 4245 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 216 Uptime: 1 min Memory: 683.7/3007.8MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.421) inxi: 2.2.35 
guru@uefi-n-bios:~$ 

```

---

### Post by ventrical on 2016-05-24
I did ...
```


sudo update-grub

```

and now it boots right into gnome3 :)  geesh .. heheh

---

### Post by sudodus on 2016-05-24
> **ventrical said:**
> I installed Mate DE and got Gnome3!! After I installed Mate there was no desktop so I installed gdm:

```

sudo apt-get install gdm

```

then

```

sudo service gdm start

```

and 'guru' gdm greeter came up , logged on  gnome3 desktop.. works great. uhh ummm.. I think it would be neat to use something small like razorqt because Mate is so huge to install.

Lots of questions .. but later  :)

regards...

Which meta-package did you install: **mate-desktop** or **ubuntu-mate-desktop** or some other package(s)?

---

### Post by sudodus on 2016-05-24
> **ventrical said:**
> I did ...
```


sudo update-grub

```

and now it boots right into gnome3 :)  geesh .. heheh

But you installed MATE, didn't you? Do you mean that it is MATE, but looks like gnome3?

---

### Post by ventrical on 2016-05-24
> **sudodus said:**
> But you installed MATE, didn't you? Do you mean that it is MATE, but looks like gnome3?

Look again.... gnome3!

```

guru@uefi-n-bios:~$ inxi -b
System:    Host: uefi-n-bios Kernel: 4.4.0-22-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.4 Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 2995 MHz (max)
Graphics:  Card: NVIDIA GF119 [GeForce GT 610]
           Display Server: X.Org 1.18.3 driver: N/A
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9 GLX Version: 3.0 Mesa 11.2.0
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 87.9GB (4.7% used)
Info:      Processes: 205 Uptime: 8 min Memory: 735.5/3007.8MB
           Client: Shell (bash) inxi: 2.2.35 
guru@uefi-n-bios:~$ 

```

either the menu inadvertently selected gnome desktop or I did .. but I am certain I chose Mate.

---

### Post by ventrical on 2016-05-24
> **sudodus said:**
> Which meta-package did you install: **mate-desktop** or **ubuntu-mate-desktop** or some other package(s)?

I chose Mate-desktop... there is only one  Mate in the menu.... I'll look again..

Ok .. I chose..

Install Ubuntu Mate!! It would not boot into Mate desktop so I had to install gdm and then it would boot into gnome3.

  The bright spark in all of this is that it is using so little resources and is very fast. I am certain there are bugs .. but they can be fixed later.

Underneath that it says : Install Ubuntu (standard desktop) and I DID NOT choose that. Also I have a comment about that one. Ubuntu (standard desktop) is *UNITY* and this should be made clear in the menu (IMHO).

regards..

---

### Post by ventrical on 2016-05-24
razorqt desktop installed on your image:

---

### Post by sudodus on 2016-05-24
It seems wrong, I have to check the menu.

Manual inspection tells me that the menu item **07 - Install Ubuntu MATE** brings you to

```
sudo apt-get install ubuntu-mate-desktop
```

But sometimes it is not enough with manual inspection. Testing will reveal what really happens.

---

### Post by QDR06VV9 on 2016-05-24
> **sudodus said:**
> So you are keeping an eye on own adventures, *runrickus* :-D
Always... My eyes are Wide Open...:lol:

---

### Post by sudodus on 2016-05-24
> **ventrical said:**
> razorqt desktop installed on your image:

It looks nice :-)

This is maybe the best thing with this system. It is easy to make your own custom system with ***your*** selected packages and tweaks :-)

---

### Post by QDR06VV9 on 2016-05-24
> **ventrical said:**
> [U][B]I chose Mate-desktop... there is only one  Mate in the menu.... I'll look again..

Ok .. I chose..

Install Ubuntu Mate!! It would not boot into Mate desktop[/B][/U] so I had to install gdm and then it would boot into gnome3.

  The bright spark in all of this is that it is using so little resources and is very fast. I am certain there are bugs .. but they can be fixed later.

Underneath that it says : Install Ubuntu (standard desktop) and I DID NOT choose that. Also I have a comment about that one. Ubuntu (standard desktop) is *UNITY* and this should be made clear in the menu (IMHO).

regards..
Yes I had the same Issue..For what it's worth.

---

### Post by sudodus on 2016-05-24
I'm installing Ubuntu MATE via the menu now. I did an ***update & dist-upgrade*** before (via the main menu). Otherwise there will be problems. ***Maybe that should be built into the installer menu?***

And after that the system boots into the MATE desktop with the login screen that I recognize. See the attached screenshot :-)

---

### Post by QDR06VV9 on 2016-05-24
> I did an ***update & dist-upgrade***
Doohh! Never even occurred to me till just now...;)
But that makes perfect sense now.
Thanks sudodus

---

### Post by sudodus on 2016-05-24
A lot happens with an operating system not only during the weeks before the release but also during the weeks after the release. I have learned to update & dist-upgrade after installing as a general rule, except when using "today's daily iso file" :-)

---

### Post by ventrical on 2016-05-24
> **sudodus said:**
> I'm installing Ubuntu MATE via the menu now. I did an ***update & dist-upgrade*** before (via the main menu). Otherwise there will be problems. ***Maybe that should be built into the installer menu?***

And after that the system boots into the MATE desktop with the login screen that I recognize. See the attached screenshot :-)

Yes .. there is a definite order of logic which needs to be followed. You DO have update&dist-upgrade already built in .. it is just  that I didn't see it. I'm just navigating , trying it out .. not thinking about it .. ya know ..

The really kewl thing is that you are using LXD containers (I assume) which is what we are supposed to be testing.

It is also working very fast with Kingston 3.0v USB. Almost like SSD.

Another thing I noticed during the bootstrap is that it probes hardware and relegates the appropiate drivers without breaking the desktop. So far , so good!

Regards..

---

### Post by ventrical on 2016-05-24
> **runrickus said:**
> Yes I had the same Issue..For what it's worth.

Duplicating a benchmark of any kind is always worth it's weight in gold because  is validates a bug/logic-bug.

Thanks !

Regards..
Hey .. thanks for fixing humungous FONTS! hehehehe

---

### Post by sudodus on 2016-05-25
The default font can be too small to read (at least with old eyes), if you want to stay with a text interface and a high resolution screen. A typical example is the console of a server.

So it helps to be able to increase the font size. Kudos to [*gtree:* How to change default font size in console mode](http://ubuntuforums.org/showthread.php?t=2319718&p=13466678#post13466678)

---

### Post by sudodus on 2016-05-25
> **ventrical said:**
> Yes .. there is a definite order of logic which needs to be followed. You DO have update&dist-upgrade already built in .. it is just  that I didn't see it. I'm just navigating , trying it out .. not thinking about it .. ya know ..

The really kewl thing is that you are using LXD containers (I assume) which is what we are supposed to be testing.

It is also working very fast with Kingston 3.0v USB. Almost like SSD.

Another thing I noticed during the bootstrap is that it probes hardware and relegates the appropiate drivers without breaking the desktop. So far , so good!

Regards..

I'm glad it works well for you. But I have done nothing to implement LXD containers. I had to browse the internet to learn about them, so if they are implemented, it is because they came with the Ubuntu system by default.

---

### Post by ventrical on 2016-05-25
> **sudodus said:**
> I'm glad it works well for you. But I have done nothing to implement LXD containers. I had to browse the internet to learn about them, so if they are implemented, it is because they came with the Ubuntu system by default.

Ahhh... well . I see that LXD is called during the verbose script boot-up so I assumd you are using them. Pehaps further investigation is needed.

---

### Post by sudodus on 2016-05-25
> **sudodus said:**
> I'm installing Ubuntu MATE via the menu now. I did an ***update & dist-upgrade*** before (via the main menu). Otherwise there will be problems. ***Maybe that should be built into the installer menu?***

And after that the system boots into the MATE desktop with the login screen that I recognize. See screenshot #5 :-)

[SIZE=4]Two updated compressed image files are uploaded[/SIZE]

[s][dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz)[/s] ; replaced by newer versions
[s][dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz)[/s] ; replaced by newer versions

One of these images has the package 'xserver-xorg-video-intel' installed, which makes it work with some old Intel graphics chips.

These are image files of a mini system with text screen (no graphic desktop environment). They were made starting from the Ubuntu Server 16.04 64-bit iso file. A minimal system was created as a starting point for any of the Ubuntu flavours including Ubuntu Server. See screenshots #1-4.

*Update 1:* The systems are updated & dist-upgraded and up to date 2016-05-25 (May 25).

*Update 2:* Before entering the installer sub-menu, you are prompted to update & dist-upgrade, so that the system will be up to date before installing a desktop meta-package. See screenshot #4.

Newer versions of these systems are available at [http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

There is a detailed description at [UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

[hr][/hr]
Log in with the following user and password,
user:     **guru**
password: **changeme**

[hr][/hr]
***gpt-fix***

If you clone the compressed iso files, you need to fix the GUID partition table, GPT, because in most cases you clone to another drive size, and GPT is sensitive to that (which is different from the old MSDOS partition table). I made a shellscript file

[http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix)

that does the work for you. It works for the cases that I have tested. gpt-fix uses ***gdisk*** under the hood, and you may need to install it. Run gpt-fix in the directory, where you downloaded it (or install it into a directory in $PATH).

```
sudo apt-get install gdisk  # install if necessary

sudo bash gpt-fix /dev/sdx
```

where **x** is the drive letter.

The GUID partition table, GPT, is fixed automatically, if you use ***mkusb 10.6.6*** or a newer version to install from these compressed image files. If you use other tools, you need ***gpt-fix*** or to fix the GPT manually with ***gdisk***.

[hr][/hr]
***Edit:*** there is an update 2016-05-27. The main difference is the ***tasksel*** menu, described in [post #155](http://ubuntuforums.org/showthread.php?t=2213631&page=8&p=13495646#post13495646),

**11 Install Server and other packages (tasksel)**

---

### Post by sudodus on 2016-05-25
> **ventrical said:**
> Ahhh... well . I see that LXD is called during the verbose script boot-up so I assumd you are using them. Pehaps further investigation is needed.

Yes, LXD is installed. When I was testing the system tonight, there was an update. But I don't think it is activated.

---

### Post by sudodus on 2016-05-27
*Oldfred* taught me to use ***tasksel*** to make it convenient to install all the metapackages that are available from the Ubuntu Server iso file. So I made a new version of the compressed image files. (I also added a menu entry for htop, while I was modifying the systems.)

[SIZE=4]Two updated compressed image files are uploaded[/SIZE]

[s][dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz)[/s] ; replaced by newer versions, see [this link](http://phillw.net/isos/linux-tools/uefi-n-bios).
[s][dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz)[/s] ; replaced by newer versions

The systems were updated & dist-upgraded and up to date 2016-05-25 (May 25), the only differences now (2016-05-27) are the changes in the menus described above, but the tasksel menu item is a big improvement, see the attached screenshots.

**11  Install Server and other packages (tasksel)**

- Select the high-lighted item in the tasksel menu with the *space* key. You can select several items.

- Start the installation of them all at the same time by pressing the *Enter* key.

- Quit from the tasksel menu with the *Escape* key.

---

### Post by sudodus on 2016-05-27
> **ventrical said:**
> Ahhh... well . I see that LXD is called during the verbose script boot-up so I assumd you are using them. Pehaps further investigation is needed.

Maybe LXD is used if you install 'Virtual Machine host' according to the attached screenshot. I have not tried it yet, so I don't know if it uses KVM or LXD or something else.

---

### Post by ventrical on 2016-06-02
> **sudodus said:**
> Maybe LXD is used if you install 'Virtual Machine host' according to the attached screenshot. I have not tried it yet, so I don't know if it uses KVM or LXD or something else.

LXD is the new hypervisor to replace qemu kvm.  Sorry for time in getting back. 

Regards..

---

### Post by ventrical on 2016-06-08
Tested this:

[dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz")


in both BIOS and UEFI mode.

Installed using latest mkusb.

As usual , excellent workmanship.

Regards..

---

### Post by sudodus on 2016-06-09
Thanks for testing ventrical,

Your testing is always valuable, probably most valuable when you find bugs or similar, but I am very happy to read that things are working correctly :-)

---

### Post by ventrical on 2016-06-09
When I first booted , went to menu and chose to install xubuntu-desktop standard. I had to install gdm .. etc.. took a long time but xubuntu never installed .. only ubuntu-gnome like last time. 

Another good thing is that it didn't affect my ssd card because when I installed gdm in must have installed grub (or grub was already installed and it auto-updated) and pulled in the two installs I have on my ssd. When I test USBs on UEFI machines I disconnect my ssds but this time I forgot.

I'll do more testing later but not today. Too sore.  :)

Regards..

---

### Post by udestudent on 2016-07-04
> **sudodus said:**
> [SIZE=4]Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode[/SIZE]
....


Hi sudodus,

thank you very much for your advanced tutorial.
I need a full encrypted pendrive, therefore i would like to use encrypt the whole drive during installation.

i have some questions:

1) You have two different versions of an image, either 4-pendrive or nothing. What is exactly the difference between these two image files?

2) What do you mean with "[COLOR=#000000]Boot into Ubuntu [/COLOR][B]*live* from an [B]*amd64* iso file in UEFI mode. "
[/B][/B]do you mean with a live boot the normal Ubuntu image or the modified one from you?

3) How can i boot in BIOS mode on a UEFI Mac?  (Step C: [COLOR=#000000]Reboot the live system into BIOS mode, install [/COLOR][B]*grub-pc* and install the bootloader for BIOS mode/media/multimed-2/boot-usb/OneButtonInstaller/dd_Ubuntu_16.04-gamma-UEFI-n-BIOS-4-pendrive-12GB.png )

[/B]Thank you very much[B]
[/B]

---

### Post by sudodus on 2016-07-04
Welcome to the Ubuntu Forums, udestudent :-)

> **udestudent said:**
> Hi sudodus,

thank you very much for your advanced tutorial.
I need a full encrypted pendrive, therefore i would like to use encrypt the whole drive during installation.

i have some questions:

1) You have two different versions of an image, either 4-pendrive or nothing. What is exactly the difference between these two image files?

The difference is the tweaks for pendrives as illustrated at these links:

[UEFI-and-BIOS/stable-alternative#Ubuntu](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#Ubuntu)
[UEFI-and-BIOS/stable-alternative#Decrease_wear_for_a_pendrive](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#Decrease_wear_for_a_pendrive)

> 
2) What do you mean with "[COLOR=#000000]Boot into Ubuntu [/COLOR][B]*live* from an [B]*amd64* iso file in UEFI mode. "
[/B][/B]do you mean with a live boot the normal Ubuntu image or the modified one from you?

An iso file is a normal Ubuntu image and amd64 means the 64-bit version.
> 
3) How can i boot in BIOS mode on a UEFI Mac?  (Step C: [COLOR=#000000]Reboot the live system into BIOS mode, install [/COLOR][B]*grub-pc* and install the bootloader for BIOS mode/media/multimed-2/boot-usb/OneButtonInstaller/dd_Ubuntu_16.04-gamma-UEFI-n-BIOS-4-pendrive-12GB.png )

[/B]Thank you very much[B]
[/B]

I have no Mac computer, and I know very little about booting them with linux. I suggest that you ***create an own thread*** in the sub-forum [Installation & Upgrades](http://ubuntuforums.org/forumdisplay.php?f=333). Make a good descriptive title and describe the computer and what you want in the first post. That way you have better chances to get good help. If you want me to find it, please post a link here :-)

---

### Post by gainiac on 2016-09-18
Started the latest Intel Installer on my Surface Pro 3. Can choose which Version of Ubuntu i want to install, but then it gives me errors. Is there a chance to get a good detailed tutorial how to install it correctly?

---

### Post by sudodus on 2016-09-18
Welcome to the Ubuntu Forums, gainiac :-)

First of all, this is your first post here. Please tell me if linux is new for you, and if not, what linux distros you have been using and for how long. It will make it easier for me to help you.

-o-

'Surface Pro 3' rings a bell for me. I remember that there were problems, but it works with Ubuntu 16.04.1. So it should work for you according to the tips and links from these threads at our Ubuntu Forums:

[Installing full Ubuntu on an SD card (Surface Pro 2 issues with Grub)](https://ubuntuforums.org/showthread.php?t=2310300)

[Installing Ubuntu onto a microSD card (or USB drive) on a Surface Pro 3](https://ubuntuforums.org/showthread.php?t=2309963&p=13424583#post13424583)

This method is the conventional one, starting from an Ubuntu desktop iso file.

-o-

But you are asking in this thread, so I guess that you have tried to install from a compressed image file. Let us hope that it will work all the way in your Surface Pro 3. ***Please tell me how far it works,*** the steps that worked before it gives you errors.

- Which compressed image file did you download?
- Did you check it with md5sum?
- Which tool did you use to flash it?
- Did you flash into a USB pendrive or a flash card? What size is it?

- Did it seem that the flashing operation was successful?
- Did it boot into a text screen from the USB pendrive or flash card?

Please describe the errors with as many details as possible:-)

---

### Post by gainiac on 2016-10-04
Hey sudodus,
thanks for your reply. At first, I'm very sorry for my late response. I'm quite familiar with Linux, used 16.04 on my Tower. 
Regarding my question, I have good news: It works perfectly fine!
I decided to use your way to get Ubuntu on my SP3, since I didn't want to mess my SP3 up. So I extracted the image as you explained on an external 1TB HDD (!) and runned the installer. My Problem was that I had no connection to the Internet, which I solved by using an USB to Ethernet adapter. After that, I could install Gnome after a distro upgrade without any problems or additional steps. Only "Problem" left was the non-working touchpad. This coul be solved by this tutorial for the Surface Book over at Reddit: [https://www.reddit.com/r/SurfaceLinux/comments/4l8iv1/surface_book_1604_install_step_by_step/](https://www.reddit.com/r/SurfaceLinux/comments/4l8iv1/surface_book_1604_install_step_by_step/)
Only use the step before the last one and everything works as it should. 
As you can see, your tutorial and files Show that it's not Magic to run a fully working Ubuntu Distro on a Surface Pro 3 without messing up the boot Manager or you EFI partition and I'm sure this will work on every Surface, maybe also on every other Windows tablet.

Btw. I used the latest Image for X64 on your Server!

---

### Post by sudodus on 2016-10-04
Congratulations *gainiac* :KS

I'm glad you made it work, and thanks for sharing your solution :-)

---

### Post by sudodus on 2017-01-15
[size=4]There is a torrent file that you can use to build your own custom operating system[/size]

The dd_text_16.04-UEFI-n-BIOS compressed image file was made up to date, and a torrent file was uploaded in January 2017. It can be used, if you want to start with a light-weight system and install your own selection of program packages - desktop packages, server packages and application packages.

[dd_text_16.04-UEFI-n-BIOS_2017-01-15_intel-4-pendrive-7.8GB.img.xz.torrent](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS?action=AttachFile&do=view&target=dd_text_16.04-UEFI-n-BIOS_2017-01-15_intel-4-pendrive-7.8GB.img.xz.torrent)

Use ***mkusb*** to install from the downloaded compressed image file to a USB pendrive, a memory card, or maybe an external SSD or HDD.

See details at this link: [Installation/UEFI-and-BIOS/torrent](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/torrent)

[hr][/hr]
***Edit:*** The corresponding file (the whole file, not torrent)  and two other new files are also available from

**[http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)**

[s][dd_dus-lxde_16.04-UEFI-n-BIOS_2016-12-12_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_dus-lxde_16.04-UEFI-n-BIOS_2016-12-12_intel-4-pendrive-7.8GB.img.xz)[/s]
[dd_text_16.04-UEFI-n-BIOS_2017-01-15_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2017-01-15_intel-4-pendrive-7.8GB.img.xz)
[dd_Ubuntu_16.04.1_2017-01-17_UEFI-n-BIOS-12GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_16.04.1_2017-01-17_UEFI-n-BIOS-12GB.img.xz)

---

### Post by sudodus on 2017-05-07
[SIZE=4]Updated installed operating systems that can boot in both UEFI and BIOS mode.[/SIZE]

Look for newer versions of compressed image files of installed operating systems that can boot in both UEFI and BIOS mode at

[phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

May 07 2017 two files were uploaded,

[dd_text_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz)
[dd_dus-lxde_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_dus-lxde_16.04-UEFI-n-BIOS_2017-05-07_intel-4-pendrive-7.8GB.img.xz)

---

### Post by C.S.Cameron on 2017-12-07
**Mkusb** makes a great base for many bootable pendrive projects, from grub2 bootable Puppy Linux to multiboot Persistent systems to multiboot Full systems and mixed/hybred Persistent/Full systems.

I used the following method to make a BIOS/UEFI Full install:

Use mkusb to make a Live system on a USB (2GB or larger).
Use mkusb to make a Persistent system on a USB 16GB or larger, using default settings with ~12GB persistence.
Remove HDD before proceeding, (optional but recommended).
Insert both USB drives.
Boot Installer drive, select Install.
Select Something else.
Select sdb5, (the target drive), and click Change.
Select Use as: ext4, Format, Mount point /.
Don't touch any other partitions.
Select sdb5 for boot loader installation.
Complete installation.
Cut grub.cfg from sdb5/boot/grub and paste to sdb3/boot/grub, overwriting the existing grub.cfg file.
Delete sdb4, the ISO9660 partition and expand sdb5 into the recovered space.
Boot the target drive and run sudo update grub, (optional).

Managed to find a computer with working UEFI the next village over and this method seems to work fine.
I figure it should work on any computer a mkusb drive works on.
Forgive me Sudodus, if you have previously posted same method, I could not find it if you did.

---

### Post by sudodus on 2017-12-08
No worries C.S.Cameron,

I have created several alternative methods for this purpose, but not this one, I think you invented it right now :-)

[hr][/hr]
My first test was to repeat what you did (with standard Ubuntu 17.10 in BIOS mode in my Toshiba laptop with 3rd generation Intel i5 hardware and an Insyde BIOS/UEFI system.

1. **Main result: The created installed system boots both in BIOS mode and UEFI mode as it should :-)**

2. **I would suggest some modifications of your recipe:**

- Insert the live-only USB drive and boot. When the system is running (and you are at the desktop environment), insert the persistent live USB drive. (Otherwise it might boot from the persistent live drive and prevent some of the tasks later in your recipe.)

- Things will be smoother, if you delete sdb4, the ISO9660 partition and expand sdb5 into the recovered space before installing. (You need not move all the installed files.) In order to do this you must first unmount the involved partitions. I did this with gparted, but it is possible also with other tools.

- Mount the sdb3 and sdb5 partitions.

```

sudo mkdir /mnt/sd3
sudo mkdir /mnt/sd5
sudo mount /dev/sdb3 /mnt/sd3
sudo mount /dev/sdb5 /mnt/sd5

```

- Copy grub.cfg (an explicit description will avoid confusion)

```

sudo cp -p   /mnt/sd5/boot/grub/grub.cfg /mnt/sd3/boot/grub/

```

I am not sure that it works the other way - or let us put it this way: We might need some modifications to avoid problems, when installing in UEFI mode and wanting to make it work in BIOS mode. In this case, the bootloader (the EFI system partition) will be installed into a target drive automatically, which is probably not what we want.

But I have not tested it yet. I will go outdoors and shovel show for an hour or two now ;-)

---

### Post by C.S.Cameron on 2017-12-08
Thanks Sudodus, you are right, it is a lot faster to expand a partition in GParted when it is empty, I was booting with both drives inserted using F9 on a HP and selecting the Live USB to boot. I'll try creating the drive in UEFI mode tomorrow. 

I don't think there is a word for snow in Sinhalese.

---

### Post by sudodus on 2017-12-08
> **C.S.Cameron said:**
> Thanks Sudodus, you are right, it is a lot faster to expand a partition in GParted when it is empty, I was booting with both drives inserted using F9 on a HP and selecting the Live USB to boot. I'll try creating the drive in UEFI mode tomorrow. 

My second test was to modify (repeat but in UEFI mode) what you did (with standard Ubuntu 17.10 in UEFI mode in my Toshiba laptop with 3rd generation Intel i5 hardware and an Insyde BIOS/UEFI system).

**Important comment:** There is no internal drive in the Toshiba laptop during these tests, so there is no problem with any EFI system partition being written to the internal drive. I am not yet sure if this will happen when using 'Something else', but it should be tested (with an internal system, that I can afford to destroy).

1. **Main result: The created installed system boots both in BIOS mode and UEFI mode as it should** :-) 

2. Some UEFI/BIOS systems will select boot drive automatically, for example the system in my Toshiba laptop. For that reason it is a good idea to plug in the live-only pendrive and let the boot finish before plugging in the persistent live one.

3. I noticed that gparted did not want to unmount the iso9660 partition /dev/sdb4, so we should recommend to unmount with a umount command line before starting gparted.

```

sudo umount /dev/sdb?

```

So your method works when the installation is done both in BIOS mode and UEFI mode (at least when the internal drive is unplugged).

> 
I don't think there is a word for snow in Sinhalese.

I think I understand why :-)

---

### Post by sudodus on 2017-12-09
My third test was to modify (repeat in UEFI mode) what I did but with an internal drive connected (with standard Ubuntu 17.10 in UEFI mode in my Toshiba laptop with 3rd generation Intel i5 hardware and an Insyde BIOS/UEFI system).

As expected, the EFI boot of the internal drive was overwritten, and pointed to the external drive. I could repair it by logging in via the grub menu of the external drive (which contained the systems in the internal drive) and using **grub-install** according to the following dialogue,

```

guru@guru-SATELLITE-PRO-C850-19W:~$ sudo lsblk -fm
NAME   FSTYPE LABEL            UUID                                 MOUNTPOINT                                       NAME     SIZE OWNER GROUP MODE
sda                                                                                                                  sda    111,8G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat                    9383-1DCE                            /boot/efi                                        &#9500;&#9472;sda1   480M root  disk  brw-rw----
&#9500;&#9472;sda2 ext4   lubuntu-efi-mode d577a6b4-abe4-4f16-ab4b-7f972dc43526 /                                                &#9500;&#9472;sda2    40G root  disk  brw-rw----
&#9500;&#9472;sda3 swap                    92124f3c-1fb3-46bd-ac2d-5577962e83c1 [SWAP]                                           &#9500;&#9472;sda3   3,9G root  disk  brw-rw----
&#9500;&#9472;sda4                                                                                                               &#9500;&#9472;sda4     2M root  disk  brw-rw----
&#9492;&#9472;sda5 ext4   ubuntu-bios-mode cc7dcfe4-ffbb-4cfd-9a12-4f8c82e48bb3                                                  &#9492;&#9472;sda5  67,4G root  disk  brw-rw----
sdb                                                                                                                  sdb     14,9G root  disk  brw-rw----
&#9500;&#9472;sdb1 ntfs   usbdata          7B80898E53F4CC29                     /media/guru/usbdata                              &#9500;&#9472;sdb1   1,3G root  disk  brw-rw----
&#9500;&#9472;sdb2                                                                                                               &#9500;&#9472;sdb2     1M root  disk  brw-rw----
&#9500;&#9472;sdb3 vfat   usbboot          F53E-02E2                                                                             &#9500;&#9472;sdb3   244M root  disk  brw-rw----
&#9492;&#9472;sdb5 ext4                    46c6f0f7-114b-479c-9fcf-40dcb9dd7588 /media/guru/46c6f0f7-114b-479c-9fcf-40dcb9dd7588 &#9492;&#9472;sdb5  13,4G root  disk  brw-rw----
sr0                                                                                                                  sr0     1024M root  cdrom brw-rw----
guru@guru-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo grub-install --efi-directory=/boot/efi /dev/sda[/COLOR]

```

**I failed to repair/update grub of the USB drive to make it boot without the internal drive.** This must be possible with some manual tweaks, but I can conclude, that things get complicated in UEFI mode, when an internal drive is connected. The easy solution is to disconnect/unplug the internal drive and do the installation according to the previous posts.

---

### Post by oldfred on 2017-12-09
I just copy /EFI/ubuntu to /EFI/version in ESP, before any second UEFI install.
And then copy grub.cfg back into /EFI/ubuntu, after install. 

And (before above) I copy all of /EFI/ubuntu to external drive twice, once to /EFI/ubuntu as that is where full install of grub expects more files.
But UEFI requires all external drives to boot from /EFI/Boot/bootx64.efi, so I copy second time to /EFI/Boot and rename shimx64.efi to bootx64.efi.
Then UEFI finds bootx64.efi and boots Ubuntu on external directly.
I also update fstab in external to refer to ESP on external drive.

---

### Post by sudodus on 2017-12-09
Thanks, oldfred,

I will try according to your instructions :-)

---

### Post by C.S.Cameron on 2017-12-10
> **sudodus said:**
> The easy solution is to disconnect/unplug the internal drive and do the installation according to the previous posts.

+1

Or else maybe enable BIOS boot, if available, to do the Full install, (the computer I am borrowing has about a dozen screws with odd heads to just access the hard drive).

Could not find the files OldFred is talking about?
My usbboot/EFI only has /BOOT/bootia32.efi and bootx64.efi in it, (just like a mkusb persistent system), cant find /EFI/ubuntu or ESP/EFI/version or shimx64.efi anywhere and EFI has no grub.cfg file in it.

OldFred: please try the above method that uses mkusb, if you have not already, it does not take much longer than a normal install.

---

### Post by oldfred on 2017-12-11
@ C.S.Cameron
If you only have bootia32.efi, then you have 32 bit UEFI.

 [https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/)
The firmware will look through each EFI system partition on the disk in the order they exist on the disk. Within the ESP, it will look for a file with a specific name and location. On an x86-64 PC, it will look for the file \EFI\BOOT\BOOTx64.EFI. What it actually looks for is \EFI\BOOT\BOOT{machine type short-name}.EFI &#8211; &#8216;x64&#8242; is the &#8220;machine type short-name&#8221; for x86-64 PCs. The other possibilities are [COLOR=#b22222]BOOTIA32.EFI (x86-32)[/COLOR], BOOTIA64.EFI (Itanium), BOOTARM.EFI (AArch32 &#8211; that is, 32-bit ARM) and BOOTAA64.EFI (AArch64 &#8211; that is, 64-bit ARM).

---

### Post by C.S.Cameron on 2017-12-11
Thanks OldFred, /EFI/BOOT/ has only bootia32.efi and bootx64.efi in it, no shimx64.efi or grub.cfg.

---

### Post by oldfred on 2017-12-11
Sorry, confusing a live installer with a full install.
The full  install of grub is different that the pre-configured grub that is already renamed bootx64.efi in live installer for 64 bit USB boot.
The full install of grub does not create a /EFI/Boot folder nor bootx64.efi. You have to manually create that yourself.

---

### Post by sudodus on 2017-12-12
> **C.S.Cameron said:**
> OldFred: please try the above method that uses mkusb, if you have not already, it does not take much longer than a normal install.

@oldfred,

If you try according to C.S.Cameron's method (in UEFI mode with and without an internal drive), it will be easier for us to understand your advice. Otherwise we might talk about different things.

---

### Post by LostFarmer on 2017-12-13
> The full install of grub does not create a /EFI/Boot folder nor bootx64.efi. You have to manually create that yourself.          That can be created by running ```
sudo grub-install --removable /dev/sdX  
``` where sdX is the correct device and must have the correct usb hdd EFI partition mounted.
that will write to the efi partition :  efi/boot/bootx64.efi  if running on a x64 os.  You need to be booted into the usb installed linux or chroot into it.  You can be booted into a different linux and add more switches to grub-install command if you do not want to boot/chroot into the usb install.  If you are still in the install environment do not know just what would be needed.

That **should permit**  usb connected hdd/stick partitioned with gpt to boot in efi mode on all computers. I did say should. You will need to enter the firmware on boot to select the efi usb device.

I did try it on Mint installed on a sata hdd connected to USB. 

More complicated and requires more then I will post is 
```
sudo grub-mkstandalone -d /usr/lib/grub/x86_64-efi/ -O x86_64-efi --compress="xz" --modules="part_gpt part_msdos ls cat configfile gettext " --fonts="unicode" -o "/boot/efi/EFI/boot/bootx64.efi"  "boot/grub/grub.cfg=/tmp/grub.cfg" -v
```

---

### Post by sudodus on 2017-12-13
@LostFarmer,

The reason for using mkusb as a starter for a full install is that it is doing something similar to what you describe in your post. I have not used grub-mkstandalone (not even been aware of it).

It looks interesting, and might be the way to make things work, when it is difficult to remove the internal drive for example in computers with a soldered SSD or where the guarantee prescribes that the computer must not be opened :-)

---

### Post by palindrom2 on 2018-10-17
> **sudodus said:**
> [SIZE=4]A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode[/SIZE]


***1. Current system, seems very stable so far***

The current system contains a live system and an installed system, and both work in UEFI and BIOS mode. The compressed image file

**dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz**

at

[http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

is created like this (only a crude description so far)


So I tried to follow your instructions but with Ubuntu 18.04, but so far with no success.  It would be very nice, if you could help me with this.

So here's what I did:

I'm using a SanDisk Ultra Fit USB 3.0 with 128 GB. My goal is to have a portable system which can be booted from most Computers including my Surface Pro 3. As I need the Surface and don't want to constantly repair its booloader (you can't disable the harddrive), I do all the work in VirtualBox. 
I partitioned the stick using Gparted as you described in step A, but with an additional partition as partition 1, which is an NTFS partition for exchanging files with Windows.
So sda2 is my Fat32 partition with the live system. I installed the system using Linux Live USB Creator in Windows, because I couldn't download the file in VirtualBox (download errors, not enough free space...)
sda5 is the partition I want to install Ubuntu to.

listed by fdisk -lu
```

Festplatte /dev/sda: 115,7 GiB, 124218507264 Bytes, 242614272 Sektoren
Einheiten: Sektoren von 1 * 512 = 512 Bytes
Sektorgröße (logisch/physikalisch): 512 Bytes / 512 Bytes
E/A-Größe (minimal/optimal): 512 Bytes / 512 Bytes
Festplattenbezeichnungstyp: dos
Festplattenbezeichner: 0x0009c581

Gerät      Boot    Anfang      Ende  Sektoren Größe Kn Typ
/dev/sda1            2048 112642047 112640000 53,7G  7 HPFS/NTFS/exFAT
/dev/sda2  *    112642048 121653247   9011200  4,3G  c W95 FAT32 (LBA)
/dev/sda3       121655294 242614271 120958978 57,7G  5 Erweiterte
/dev/sda5       121655296 203831077  82175782 39,2G 83 Linux
/dev/sda6       203833344 242614271  38780928 18,5G 82 Linux Swap / Solaris

```

listed by parted -l
```

Modell: SanDisk Ultra Fit (scsi)
Festplatte  /dev/sda:  124GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Typ       Dateisystem     Flags
 1      1049kB  57,7GB  57,7GB  primary   ntfs
 2      57,7GB  62,3GB  4614MB  primary   fat32           boot, LBA
 3      62,3GB  124GB   61,9GB  extended
 5      62,3GB  104GB   42,1GB  logical   ext4
 6      104GB   124GB   19,9GB  logical   linux-swap(v1)

```

listed by lsblk
```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    1 115,7G  0 disk 
&#9500;&#9472;sda1   8:1    1  53,7G  0 part /media/jo/Ubuntu Daten
&#9500;&#9472;sda2   8:2    1   4,3G  0 part /media/jo/MYLINUXLIVE
&#9500;&#9472;sda3   8:3    1     1K  0 part 
&#9500;&#9472;sda5   8:5    1  39,2G  0 part /media/jo/58338c12-15fd-4212-960d-6eb503964c24
&#9492;&#9472;sda6   8:6    1  18,5G  0 part 

```


But in step C, when I try to install to sda5 I get an error during/at the end of the installation process. 
* grub-efi-amd64-signed package failed to install into /target/*
I tried installing from a live image or without connection to the internet as that were the solutions I could find through Google.
When this didn't work I installed grub using grub-install after the installation failed. I then proceeded to try and change the configuration files, but as there is no file named vmlinuz-4.15.0-29-generic.efi.signed in sda5/boot I get an error when choosing the new boot option.
There is although a file named vmlinuz-4.15.0-29-generic in this directory.
When using grub-install I made a mistake, rendering the live system unusable too. I reinstalled the live system using LiLi Usb Creator as before. I tried to install Ubuntu to sda5 again after this, getting the same error message and now I don't dare using grub-install again, as I'm just a beginner with Ubuntu and don't know how to do it properly.

So now I can boot the live system, but after trying and failing to boot using the new entry I too get an error message saying /boot/vmlinuz could not be found.

This are the files I changed:
MYLINUXLIVE/boot/grub/grub.cfg
```


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

set timeout=5
menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash locale=de_DE bootkbd=de console-setup/lazoutcode=de ---
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash ---
	initrd	/casper/initrd.lz
}


menuentry 'Installed Ubuntu, with Linux 4.15.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-29-generic-advanced-2a914602-bccd-4248-8b0a-66cff22173db' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  2a914602-bccd-4248-8b0a-66cff22173db
	else
	  search --no-floppy --fs-uuid --set=root 2a914602-bccd-4248-8b0a-66cff22173db
	fi
	echo	'Loading Linux 4.15.0-29-generic ...'
	linux	/boot/vmlinuz-4.15.0-29-generic.efi.signed root=UUID=2a914602-bccd-4248-8b0a-66cff22173db ro  quiet splash $vt_handoff
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-4.15.0-29-generic
}

```

MYLINUXLIVE/syslinux/txt.cfg
```

label persist
menu label ^Persistenter Modus
  kernel /casper/vmlinuz
  append  bootkbd=de console-setup/layoutcode=de console-setup/variantcode=nodeadkeys locale=de_DE  persistent noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash --
label live
  menu label ^Live Modus
  kernel /casper/vmlinuz
  append   bootkbd=de console-setup/layoutcode=de console-setup/variantcode=nodeadkeys locale=de_DE noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash --
label live-install
  menu label ^Installation
  kernel /casper/vmlinuz
  append   bootkbd=de console-setup/layoutcode=de console-setup/variantcode=nodeadkeys locale=de_DE  only-ubiquity noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash --
label check
  menu label ^Uberprufung der Integritat
  kernel /casper/vmlinuz
  append   bootkbd=de console-setup/layoutcode=de console-setup/variantcode=nodeadkeys locale=de_DE noprompt boot=casper integrity-check initrd=/casper/initrd.lz splash --
label memtest
  menu label ^Uberprufung des Arbeitsspeichers
  kernel /install/mt86plus
# ------------------------------------------------------------------
label ubu-installed
  menu label ^Installed Ubuntu in partition 5 with grub in PBR
  com32 chain.c32
  append boot 5

```



I think the two main problems are grub not being installed during the installation of Ubuntu 18.04 and the file vmlinuz-4.15.0-29-generic.efi.signed missing, but I don't know how to fix this.
Any help would be appreciated.

---

### Post by sudodus on 2018-10-17
@palindrom2,

That method works for Ubuntu 14.04 LTS, but several things have changed during the four years since then, and I can understand that there are problems to use the same method for Ubuntu 18.04 LTS.

You have found one difference, the name of the kernel file. Another difference is that there is another Ubuntu Startup Disk Creator, and it creates another partition structure than the old one. You must use another tool in 18.04 LTS to get the same result, for example Rufus (a Windows tool).

But I would like to ask a few questions before continuing with details.

What do you want to achieve?

- Do you want a live or persistent live system?

- Do you want an installed system?

- Or do you want ***both*** a live or persistent live ***and*** an installed system in the USB pendrive?

- Is it important that it can boot both in BIOS and UEFI mode?

Depending on your answers to these questions, I will give you different advice.

---

### Post by palindrom2 on 2018-10-18
@sudodus,
Thank you for your quick answer. 

> **sudodus said:**
> @palindrom2,

- Do you want a live or persistent live system?

- Do you want an installed system?

- Or do you want ***both*** a live or persistent live ***and*** an installed system in the USB pendrive?


Foremost I want an installed system in the USB pendrive. 
A live persistent system would be nice, as I read in many threads that an installed system can never be this adaptable with different hardware.
But most important is the installed system.

> **sudodus said:**
> 
- Is it important that it can boot both in BIOS and UEFI mode?
 

This is important, as you can't configure the surface to boot in BIOS mode and I too want to use it on a PC that can only be booted in BIOS mode.

I tried other methods you described too([One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682").  and [Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13468260#post13468260")), but the error message "System BootOrder not found. Initializing defaults. Reset System" was displayed and I got stuck in an boot loop when trying to boot the Surface. 
When I googled this I found that this might be a problem with the UEFI of the Surface. As I can boot the live system from a pendrive, I thought using the live system to boot the installed system as you described would solve this.

---

### Post by sudodus on 2018-10-18
> **palindrom2 said:**
> Foremost I want an installed system in the USB pendrive. 
A live persistent system would be nice, as I read in many threads that an installed system can never be this adaptable with different hardware.
But most important is the installed system.

Booting in UEFI as well as in BIOS mode is important, as you can't configure the surface to boot in BIOS mode and I too want to use it on a PC that can only be booted in BIOS mode.


I suggest that you try with

1. A persistent live system created directly (and automatically) with mkusb according to the following links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

2. An installed system created with the help of the following link (starting from mkusb, but with additional manual tweaks),

[BIOS/UEFI Full Install](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/984285#984285)

---

### Post by sudodus on 2019-02-08
[SIZE=4]Stable alternative with Lubuntu 18.04.1 LTS[/SIZE]

[SIZE=3]Live, persistent live and installed systems[/SIZE]

The compressed image file
```

dd_lubuntu-18.04.1-desktop-amd64-persistent-n-installed_15GB.img.xz

```
contains a

-    a live part, that can be run as
 .        live-only
 .        persistent live
 .       installer 
-    an installed part (installed like into an internal drive) 

[SIZE=3]UEFI and BIOS[/SIZE]

All these operation modes work in

-    UEFI mode (including secure boot) and
-    BIOS mode (alias CSM alias legacy mode)

Get the file and its md5sum at [phillw.net/isos/linux-tools/uefi-n-bios](https://phillw.net/isos/linux-tools/uefi-n-bios)

See details in the screenshots.

See more details at this Ubuntu help page: [help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1)

---

### Post by C.S.Cameron on 2019-02-14
I have made an attempt to link the home partition of the Persistent install with the home partition of the Full install, (as we discussed in another post).

What worked in Something else was to use the home-rw partition as the /home partition.

And copy & paste a few things in grub.cfg afterwards.

I have only had success between same flavors of 'buntu, Ubuntu with Lubuntu had problems.

It is a little freaky working with the same home on two different installs.

Persistent install has GParted, Full install doesn't yet, Full install needs a password when Persistent install doesn't, etc

I will try to remember the details.

Edit:

New users can be added but they must be added to each install individually, Adding a user to the Full install does not automatically add them to the Persistent install.
But once installed to both they share the directory.
You can allow a certain user on the Persistent install but not on the Full install and vice versa.

---

### Post by sudodus on 2019-02-14
Interesting @C.S.Cameron :-)

You wrote that it is 'a little freaky'. Do you think it is worthwhile to merge the homes or do you think it will create too much confusion?

---

### Post by C.S.Cameron on 2019-02-14
It only seems weird to me when using the same user and sharing the same home folder, but it is something that you get used to. 

With different users everything seems normal. 

I think it is better use of space just having one home partition. It makes it easier when updating and upgrading also.

I think it is a good idea to have a single /home, home-rw partition.

Edit:

It works to share home folder between the same flavors of Ubuntu even if they are different editions.
I am thinking it may work to share the home partition between different flavors as long as the usernames are different.
That would be an easy way to have multiple persistent bootable ISO's without the 4GB limit.

---


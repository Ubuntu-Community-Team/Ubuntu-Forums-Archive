---
title: "Booting from eSata/usb"
date: 2009-12-11
forum: System76 Support
---

### Post by miniyak on 2009-12-11
Has anyone booted a persistent distro install on a external flash or disc eSata drive? In particular I'm wondering if this is possible on the panp5

If you have, were there any special steps involved?

What brand drive did you use? (if that matters, i know it does with usb sometimes)


I also have the same exact questions for usb.

Along with what usb writing/set-up program you used?

I have tried unetbooten and the live usb creator included with ubuntu and i have yet to get a drive working.

---

### Post by thomasaaron on 2009-12-14
You should *definitely* be able to boot from USB. Did you set the USB as the first boot device in the BIOS?

I'm not sure about booting to eSATA. I don't have a way to test that one in the shop. This looks like it might be heading in the right direction...
[http://ubuntuforums.org/showthread.php?t=566260](http://ubuntuforums.org/showthread.php?t=566260)

---

### Post by miniyak on 2009-12-14
I just bought an 2.5 enclosure with an eSata connection today so I should be able to test this soon

now if antec only included the damn eSata cable i'ld be all set to test it out. It doesn't seem any store near-by wants to sell the eSata cables ether... no wonder nobody uses it...

---

### Post by jdmelton on 2009-12-15
I use UNetbootin to boot DSL 3, Fedora 12, and Ubuntu 9.10 on different USB drives.

I like to reformat the drives, usually 2 GB, with two separate partitions with labels. The first is the VFAT 16 and the second is Linux. The idea is that the root partition will be set to the label. On different systems, the hardware address will change, and this makes the USB able to boot on multiple systems.

There is a quirk that I found the first time I tried to use it. When selecting an image, the root boot parameter is given the iso image name. My experience has been that this parameter needs to be the same as the partition label.

For example, my Fedora 12 USB stick has two partitions, fedora12 and usblinux. The fedora12 partition is VFAT 16 and the usblinux partition is ext2. The fedora12 is marked as bootable.

When I tried to boot, the kernel was found but the root filesystem was not. Here is the way that UNetbootin set up syslinux.cfg in the fedora12 partition:

label ubnentry0
menu label Fedora-12-i686-Live
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=live:LABEL=Fedora-12-i686-Live rootfstype=auto ro liveimg quiet  rhgb

Note that the 'append' should be only one line. After some trial and error, I added another entry with LABEL=fedora12, like this:

label ubnentry6
menu label fedora12
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=live:LABEL=fedora12 rootfstype=auto ro liveimg quiet  rhgb rd_NO_LUKS rd_NO_MD noiswmd

The above trick worked, and now I can boot the USB drive on my systems. This works for Ubuntu and other distributions as well using the appropriate live image. I use these, instead of CDs, to for emergency repairs and to test new distributions.

The USB drives now boot on a 2007 System76 Serval P3, a 2009 System78 Meerkat Ment1, a diskless Mini-Itx from Damn Small Linux, a 2009 Dell Inspiron Mini 10, and a 2008 Dell Vostro 1000,

There is probably a more elegant way to do this.

As thomasaaron posted, the BIOS needs to be set to boot from USB before the hard drive.

---

### Post by miniyak on 2009-12-15
hmmm, thanks for the info jdmelton

so basically what your saying is that if i try to do a regular install on the thumb drive ill only be able to boot on the system it was installed from, am i following you right? Or is it that using a particular type of of filesystem like vfat16 as the first partition is more cross system compatible then a full ext3/4?

sorry for the ignorance, ive been using ubuntu/linux for 2 years now and the "real" partitioning process has been abstracted away from me the whole time. So I am unfamiliar with process of even changing the partition lables

I wonder If the problem im running into with the new hard drive is similar- [http://ubuntuforums.org/showthread.php?t=1355112]("http://ubuntuforums.org/showthread.php?t=1355112")

---

### Post by miniyak on 2009-12-15
Ok heres what I have found out so far

16gb pny "attache" live usb install using "USB start-up disc creator"
on my hp tc4400- boots to the menu that prompts "try ubuntu without making changes to you computer" the freezes up at the black and white ubuntu logo
on my s76 panp5- same deal

Same drive using unetbootin
hp tc4400- boots to the main live menu again but this time it has different options

live
live install
check integrity 
ect.

when live install was selected, got past B&W logo to freeze at a blank screen
same with plain old live
check integrity- says no errors

Antec 2.5 hard drive enclosure w/ WD scorpio blue: installed via live cd when the WD drive was in the hp tc4400 
Through usb on panp5= amazing, works just like real install
Through eSata= dont know antec didn't include the cable *waves fist*

dose anyone know of a way to just do the full install on the pny flash drive with out any of the live stuff? (I dont think any one who boots from usb wants to do the live stuff...)

---

### Post by miniyak on 2010-01-19
ok I just got the eSata cable yesterday.

heres the issue im running into 

I'm having a hard time telling whether the drive is running from usb or eSata. Is the a way to check for this?

The way the enclosure is set up the power is drawn from a usb port. The usb cable as two three plugs one mini to the enclosure two regular to plug into the computer. one of these is red so i supposed this meant power only but i guess it will mount from just this also...wait.... i have a power only cable lying around... i'll brb

---

### Post by miniyak on 2010-01-19
ok i just tested it w/ the power only usb cable to make sure

transfer speeds = around 50 or so mb/s compared to around 5 to 15 w/ usb

booting from eSata w/ default panp5 settings = fail

I'm fairy certain this is just because this sata port is not in the boot order (bios)... Is there a way to add esata to this list?

or maybe even chain boot from grub?

---

### Post by vgrisham on 2010-03-17
> **miniyak said:**
> ok i just tested it w/ the power only usb cable to make sure

transfer speeds = around 50 or so mb/s compared to around 5 to 15 w/ usb

booting from eSata w/ default panp5 settings = fail

I'm fairy certain this is just because this sata port is not in the boot order (bios)... Is there a way to add esata to this list?

or maybe even chain boot from grub?

What's that about flashing the bios? I think I have the latest available from System76. Is there another bios version out there that would allow esata booting?

---

### Post by miniyak on 2010-03-17
> **vgrisham said:**
> What's that about flashing the bios? I think I have the latest available from System76. Is there another bios version out there that would allow esata booting?

To be honest you would have to look up/talk with phoenix or or one of the open-source bios developers. It looks as though phoenix has outsource their help..

with phoenix you would probably have to buy (to do something it should have done in the first place...plus at the risk of borking everything)

putting a instance of grub on your external then "chain booting" from your internal grub instance would probably be more practical. All i really know at this point is that this that grub 2 has a neat feature called chain booting that i saw used to make a multi disto "usb multi-pass" on an ep of hak5

---

### Post by Skaperen on 2010-03-18
For booting from USB memory stick flash drives, I do it one of two ways:

1.  Install Ubuntu in the usual way, but with the flash drive as the target to be installed to.  I turn off swap and set filesystems to noatime option to minimize write activities.  I currently have a 16GB SDHC card set up like this for my Asus EeePC 900 as a backup boot.

2.  Put the ISO image on the flash drive, with modifications to make it bootable as a hard drive (change bootloader to GRUB1 modified with a built-in config file to look for a kernel and initrd at the end of the disk, and append the kernel and initrd extracted from the ISO at the end of the image).  Casper (not modified) just looks for a device with the right filesystem, whether that it a CD/DVD drive, or a hard drive.  I have 4 of these I use to work on my servers.  I have one running on a System76 Jackal Pro 2U right now.  You may have to change the boot order of hard drives in BIOS.

---


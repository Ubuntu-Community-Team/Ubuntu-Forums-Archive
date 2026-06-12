---
title: "Install to USB device"
date: 2013-03-29
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-03-29
I'm posting this about and to RARING (daily 13.04) because that's the only experience that I can attest!

Over the past few days I've been reading about persistence, live dvd & usb sticks, grub2, plop, etc. There exists some confusion about persistence and live dvds using usb sticks. 
My experience is that a dvd CAN):P be made persistent by using a formatted usb stick. [I followed this guidline]("https://help.ubuntu.com/community/LiveCD/Persistence")

I also found that a full OS can be installed to a usb hard drive or usb stick following these steps:
I partitioned the usb stick prior to starting ... hind site you can do this step after booting in step #2```

[LIST=1]
[*]Boot a live dvd
[*]Select try Ubuntu
[*]Start gparted (it's  installed on live dvd)
[*]Identify the usb device (in my instance /dev/sdb1)
[*]Unmount the device
[*]exit gparted
[*]Click on install (the second icon down on left)
[*]Choose something else
[*]**In sure **to select where to install boot loader (in my instance /dev/sdb1)
[*]Check main partition (I chose ext4 and mount as root / )
[*]**Double check **selection for boot loader (installer has a tendency to 'wander')
[*]Before clicking install now **double check which device is selected** (in my case selection reverted to my internal drive /dev/sda)
[/LIST]

```
I had positive experience installing on both a flash drive (usb stick) and a usb hard drive. System boots quite a bit faster than booting a live dvd!

---

### Post by cariboo on 2013-03-30
> **pfeiffep said:**
> I'm posting this about and to RARING (daily 13.04) because that's the only experience that I can attest!

Over the past few days I've been reading about persistence, live dvd & usb sticks, grub2, plop, etc. There exists some confusion about persistence and live dvds using usb sticks. 
My experience is that a dvd CAN):P be made persistent by using a formatted usb stick. [I followed this guidline]("https://help.ubuntu.com/community/LiveCD/Persistence")

I also found that a full OS can be installed to a usb hard drive or usb stick following these steps:
I partitioned the usb stick prior to starting ... hind site you can do this step after booting in step #2```

[LIST=1]
[*]Boot a live dvd
[*]Select try Ubuntu
[*]Start gparted (it's  installed on live dvd)
[*]Identify the usb device (in my instance /dev/sdb1)
[*]Unmount the device
[*]exit gparted
[*]Click on install (the second icon down on left)
[*]Choose something else
[*]**In sure **to select where to install boot loader (in my instance /dev/sdb1)
[*]Check main partition (I chose ext4 and mount as root / )
[*]**Double check **selection for boot loader (installer has a tendency to 'wander')
[*]Before clicking install now **double check which device is selected** (in my case selection reverted to my internal drive /dev/sda)
[/LIST]

```
I had positive experience installing on both a flash drive (usb stick) and a usb hard drive. System boots quite a bit faster than booting a live dvd!

I had Xubuntu install on an 8GiB SD card, and I found, that it actually booted way slower than a regular install, or on a usb hdd/thumb drive.

---

### Post by pfeiffep on 2013-03-30
I totally agree that system is slower running full install on USB; but booting from full install from USB is faster than booting from live dvd.

I did notice that using a USB stick is significantly slower than using a USB hdd

I used the same install method, so neither is using a dedicated swap partition

After experimenting with full install on USB stick I came to the conclusion that operation is much too slow, also persistence in live USB stick is pretty slow also. 
My USB hdd installation is really functional!

---

### Post by Shaq901 on 2013-05-08
I see you've managed to create a full installation of Ubunutu on an external hard drive? I followed [this guide]("http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/") that is almost exactly the same as the steps you posted, but explaining the partitioning and excluding a "gparted" step. In the end, I successfully installed Ubuntu on my 750GB hard drive, but it seems unable to boot. I installed Ubuntu on my external hard drive with an additional USB stick that i used to boot. I was successfully able to boot my USB to install Ubuntu, but I am unable to boot from the external harddrive as it just goes to a black screen. Do I still need my initial USB stick I used to install Ubuntu on my hard drive? I thought I'd ask on this thread before messing with my BIOS settings.

---

### Post by C.S.Cameron on 2013-05-08
When you were in "Something else", (manual partitioning), did you make sure you chose the correct drives for bootloader installation?

Another possibility is corruption in the downloaded iso, an MD5SUM will confirm if the iso is ok.

In BIOS you need to select the hard drive with grub as the first hard drive.

---

### Post by jerrylamos on 2013-05-09
I've been installing ubuntu for some time on USB hard drives.  Currently working fine on a USB SSD on this Acer Aspire netbook, amd64 versions.  Also runs fine on a Compaq i386 versions.  Now my Acer Aspire 5253 15" notebook does have some problems, I think there's a bug in the 5252's USB bios code.  I put a 2.5" hard drive into a USB2 case, they're under $20 from Amazon, and away I go just doing a standard install.  BTW, I boot the .iso directly from the hard drive saves time and faster than DVD or pen drive.  I tried a USB3 case however none of my test pc's do USB3.

---


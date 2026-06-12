---
title: "Is Ubuntu LiveUSB a good option?"
date: 2008-09-03
forum: The Cafe
---

### Post by irrdev on 2008-09-03
I find myself working on many different computers each week. I currently transport all my documents on my USB stick around, but I still find that it is aggravating to keep adjusting to different computers. The Ubuntu LiveUSB option has always interested me, but I have always been a bit wary about trying it myself. I would therefore like to know about other users' experiences with LiveUSB and Ubuntu.

Is LiveUSB too slow, especially as the USB drive ages? Does the constant read/writing drastically wear down the USB stick? How long can I expect the USB drive to last, considering that I spend at least 3 hours a day on my computer? How does Ubuntu adjust to the different hardware setup (drivers, graphical cards, etc.) ? 

Also, could I access my documents on my LiveUSB drive from Windows without booting the LiveUSB itself? I read that a LiveUSB drive can be formatted in Fat32, but how would I do this?

Sorry for all the questions! Any answers or personal experiences with LiveUSBs would be greatly appreciated. Thanks in advance! :)

---

### Post by randcoop on 2008-09-03
I can offer a few answers/opinions, but don't have enough experience to answer all of them.  Also, I use Xubuntu on USB, which may be somewhat less demanding on the computer than Ubuntu.

> How does Ubuntu adjust to the different hardware setup (drivers, graphical cards, etc.) ? 

I think the answer is that it's as good as Ubuntu is with various hardware.  In my experience, that's pretty good.

> Also, could I access my documents on my LiveUSB drive from Windows without booting the LiveUSB itself? I read that a LiveUSB drive can be formatted in Fat32, but how would I do this?

If you follow the Pendrivelinux site, you'll actually format two partitions on your USB.  The boot partition will be Fat16.  The other partition will be a Linux ext2 system.  I would think that you could easily create a third partition that was FAT32.

I can't see any advantage to formatting a FAT32, however.  There is free software that can be downloaded to any Windows machine enabling it to read and write to a Linux partition.  Take a look here: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by arubislander on 2008-09-03
I've used a variety of Linux LiveUSB's and Ubuntu ranks in the top 2. But I've found that it is more of use as a promotional tool (i.e. to promote Linux) than for every day use. The expierience I've had with Ubuntu LiveUSB is that the extra partition(s) tend to get currupted after a while. I'm not sure if that is due to wear on the USB stick itself or faulty writes of the OS in this mode.

If you refrain from customizing the display for a particular hardware configuration, and work with what the Live installation detects and offers you should be able to move from computer to computer without much pain. But once you optimize your Desktop for one computer you're set for trouble on another one.

In the traditional setup you would have to boot into your LiveUSB distro to get at your documents, but I suppose you could add an additional partition to your USB stick and format that as Fat32... The boot partition will not work since that is mounted as ReadOnly.

---

### Post by clanky on 2008-09-03
One thing to remember if you are looking at this option because you have to access lots of computers is that not all computers support boot from USB.

---

### Post by Herman on 2008-09-03
> Is LiveUSB too slow, especially as the USB drive ages? I have tried out Ubuntu in a few different brands of USB flash memory sticks and most seem faster than hard drives but one brand I have is slower. (Very slow, like about two hours for an installation which normally should only take half an hour).
> Does the constant read/writing drastically wear down the USB stick? I don't know, I haven't worn out any of mine yet but I don't use mine very often either. 
> How long can I expect the USB drive to last, considering that I spend at least 3 hours a day on my computer? I think that will depend on what brand of flash memory you have and how new it is. This technology is advancing rapidly. Read up on what you are buying before you spend your money. Most flash memory sticks feature 'wear levelling', and most are made of NAND cells, which can be written to around a million times. 
The larger memory stick (in GB) you can get the better, since there will be more blocks for the wear levelling system to rotate.
> How does Ubuntu adjust to the different hardware setup (drivers, graphical cards, etc.) ? Hardy Heron uses the latest [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/"). I tried it in two or three different computers and it seems to take longer to boot in a different computer for the first time but it worked in the different computers I tried it in without me needing to do anything more than wait a minute.
> Also, could I access my documents on my LiveUSB drive from Windows without booting the LiveUSB itself? I read that a LiveUSB drive can be formatted in Fat32, but how would I do this?You would need to make a separate FAT32 (or NTFS) data partition.

If you buy a good brand of modern flash memory you should have satisfactory results, but you should still keep backups of your data the same as everyone does for hard disks.

Links:[EETimes Encyclopedia]("http://www.eetimes.com/encyclopedia/defineterm.jhtml?term=flashmemory") 
 [Flash and Hard Disk Comparison]("http://www.mattscomputertrends.com/flashvsharddisk.html")
[Slashdot | IBM Flash Memory Breaks 1 Million IOPS Barrier]("http://hardware.slashdot.org/article.pl?sid=08/08/29/1646251")

---

### Post by zwygart on 2008-09-03
Hi,

I am thinking about the same thing. I have at home a computer with XP and Ubuntu. But I use a lot of different computers and tought that an OS on USB would be helpfull. (Like FirefoxPortable takes bookmarks from one PC to other unlike IExplorer on the PCs). I found Puppy and it sounds interesting and want to try it. Ubuntu on USB to is interesting. My problem is how to say the MBR of the USB how to boot? Or is it done automatically? When i start the computer and check the boot choice by pressing ESC I see the USB key but it says it don't have bootable partition. How to correct this?

Thanks

---

### Post by irrdev on 2008-09-04
> **zwygart said:**
> Hi,

I am thinking about the same thing. I have at home a computer with XP and Ubuntu. But I use a lot of different computers and tought that an OS on USB would be helpfull. (Like FirefoxPortable takes bookmarks from one PC to other unlike IExplorer on the PCs). I found Puppy and it sounds interesting and want to try it. Ubuntu on USB to is interesting. My problem is how to say the MBR of the USB how to boot? Or is it done automatically? When i start the computer and check the boot choice by pressing ESC I see the USB key but it says it don't have bootable partition. How to correct this?

Thanks

If your USB isn't automatically booting, you will need to install the linux bootloader on the USB manually. To do so, read this article from the Ubuntu Wiki -> [https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Making%20the%20drive%20bootable](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Making%20the%20drive%20bootable)

Note: This step shouldn't be required with Hardy, as the LiveCD installer can install directly to the USB drive, and everything should be setup automatically. It may be worth checking this out, as manually setting up the linux bootloader is rather tedious.

---


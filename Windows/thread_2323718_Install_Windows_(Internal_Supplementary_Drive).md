---
title: "Install Windows (Internal Supplementary Drive)"
date: 2016-05-07
forum: Windows
---

### Post by anon24 on 2016-05-07
MSI GS70 Stealth

I have three SSD's and one SATA.

Ubuntu 16.04 is installed on SDA.

Windows is not installed anywhere on the PC.

Nor is there a recovery disc or anything of the sort.

Is it possible to install Windows on SDD* from here or would I have to uninstall Ubuntu, then install Windows, etc?

My goal is to have three systems:

SDA: Ubuntu 16.04 
SDB: Ubuntu Studio 16.04
SDD: Windows

---

### Post by yancek on 2016-05-07
If you have the windows installation DVD, you should be able to install it to any internal drive as long as it is not attached via usb.  You need to be able to identify which drive you want.  You indicate you want to install windows to sdb but at the bottom of the post you indicated sdd.  Do you want windows on a separate drive?  Are you using UEFI or MBR for Ubuntu?  Do you have Ubuntu Studio already installed.  If you are using UEFI/GPT, read the info at the link below before beginning. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by anon24 on 2016-05-07
UEFI is not installed on my PC. So, it has to be a DVD? I can't use an ISO on a thumb drive? 


Sorry about that, that was a typo when I typed SDB. I meant to say SDD. I went ahead and corrected that.

---

### Post by yancek on 2016-05-07
> So, it has to be a DVD? I can't use an ISO on a thumb drive? 

If you mean doing a loopback entry to boot the windows iso from a partition on your hard drive or a flash drive, no that won't work.  It doesn't work for most Linux distributions either although most Ubuntus will work.  Windows boot files are totally different than Linux and they are also proprietary and I can't think of any reason why any Linux developer would waste time doing this.  There might be some windows software to do this.  If you have a flash drive, you can use the instructions at the link below to put your windows extracted iso on either an ntfs formatted flash drive or partition on your current system and boot it from Grub to install.   I'd read through it a couple of times first to make sure it is understood but it does work. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by anon24 on 2016-05-07
I don't even really know what you're referring to with the Loopback entry. I'm not real literate when it comes to this stuff. Ohhh, were you thinking that I was wanting to run Windows from a USB? Noooooo, hahaha! 

I just want to be able to dual boot, or rather triple boot? I want to be able to go back and forth between Ubuntu, Ubuntu Studio and Windows.

I can install Windows onto one of my internal hard drives from a USB drive from what I'm understanding. I don't have a DVD drive in my laptop, which is why I'm wanting to use a USB drive. Thanks, I'll give this a try!

---

### Post by yancek on 2016-05-07
> I don't even really know what you're referring to with the Loopback entry.

A loopack entry in Grub can be used to boot 'some' Linux distributions directly from the iso file copied to a flash drive or from a partition on a hard drive but doesn't work with windows so it's irrelevant in your case as it doesn't work with windows. 

> 
I can install Windows onto one of my internal hard drives from a USB drive from what I'm understanding. 

Yes and the method I suggested in my last post works.  I used it myself about a week ago.  I'm sure there is some software method with windows software to do the same or similar but I'm not familiar with it.  Good luck with it.

---


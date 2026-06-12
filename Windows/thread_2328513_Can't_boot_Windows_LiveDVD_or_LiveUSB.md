---
title: "Can't boot Windows LiveDVD or LiveUSB"
date: 2016-06-21
forum: Windows
---

### Post by stamatiou on 2016-06-21
Lately I have been trying to install Windows on one of my two partitions without success.

Having tried with multiple .iso's (of the versions 7, 8 and 10) to create a LiveUSB using different USB sticks and a LiveDVD using different DVD disks, I suppose that the neither the .iso nor the installation media is the root of the problem.
More specifically, my problem is that after I have prepared the installation media, when I select it from the boot options menu, there is either a black screen or a "Missing operating system" message displayed. In both occasions, eventually Ubuntu is booted.
What I suspect is that there is some compatibility problem with UEFI/BIOS. I have turned off both "Fast Boot" and "Intel Smart Response Technology".
I have also concluded that Ubuntu is running on Legacy mode by running
```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```
and receiving
```
Legacy boot on HDD
```
Do you have any suggestions?
Thanks in advance.

---

### Post by yancek on 2016-06-21
There is no such thing as a windows "Live DVD".  Do you mean you are trying to put the windows iso file on a DVD or flash drive to be able to boot to install it?  If so, what software are you using to create the usb and how are you burning the DVD?  Did you get the windows iso from the microsoft site?  Did you do an md5 checksum to verify the download?  Have you tried setting the DVD to first boot priority in the BIOS?  Same for the usb installer.

---

### Post by stamatiou on 2016-06-22
> **yancek said:**
> There is no such thing as a windows "Live DVD".  Do you mean you are trying to put the windows iso file on a DVD or flash drive to be able to boot to install it?  If so, what software are you using to create the usb and how are you burning the DVD?  Did you get the windows iso from the microsoft site?  Did you do an md5 checksum to verify the download?  Have you tried setting the DVD to first boot priority in the BIOS?  Same for the usb installer.
Excuse me for the obscurity.
By the term LiveDVD and LiveUSB I mean a DVD and a USB respectively that contain the Windows installer. The software I used for the usb are the dd command, unetbootin, winusb (both through terminal and gui). For the DVD I used Brasero.
The source of the .iso is microsoft's site and the md5 checksum check does not yield any problem with the iso.
As for the boot priority, I am sure that it boots from the installation media since I have used both boot priority and boot selection to ensure so.

---

### Post by yancek on 2016-06-22
I've never used Brasero but, it should have an option to "burn as an image" or something similar to use to create a bootable DVD so make sure you've used that.

Unetbootin doesn't work for windows.  I've never used dd on a windows iso so??  Never used winusb either so no opinion on that.  Have you tried the DVD and usb on another computer?  I have used the instructions at the link below to boot the windows 10 installer from Grub on Ubuntu and it worked.  Might give that a try.


[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by buzzingrobot on 2016-06-22
I've burned a Win10 installation image from that Microsoft site to a USB stick with dd and booted it into the Windows installer.  So, yes, that's workable. 

I don't have an answer for you, I'm afraid.  But, the "missing operating system" is the BIOS saying it can't find a bootloader on the partition where it expects to find it. The BIOS settings for boot sequence -- the drives the BIOS looks at in sequence for a bootloader -- might be worth a look, as a guess.

---

### Post by C.S.Cameron on 2016-06-22
Microsoft makes a tool for creating an install USB that can be used to infect computers with Win 10.

[https://www.microsoft.com/en-ca/software-download/windows10](https://www.microsoft.com/en-ca/software-download/windows10)

---

### Post by sudodus on 2016-10-15
I feel kind of ashamed to offer a tool to infect computers ;-) but it seems many people want to install Windows from Ubuntu, so I added this feature to ***mkusb-nox version 11.1.2***. Now it can create boot drives (USB sticks and memory cards ...) that can boot the Windows installer.

It is still only available in the unstable PPA, because it is not tested much yet. Try it if you still need it. See these links,

[mkusb-nox 11.1.2: added feature: make USB install drive for Windows](https://ubuntuforums.org/showthread.php?t=1958073&page=22&p=13554330#post13554330)

[mkusb/v7](https://help.ubuntu.com/community/mkusb/v7)

mkusb-nox works in all current Ubuntu versions with Windows 7 - 10, but you have to cope with a command line interface :-)

---

### Post by ceemer on 2016-11-08
Hope you've solved your issue.
"Infect with Win 10"--I totally love this comment, by the way...

I've been struggling with a partly similar problem, and been advised by another forum guru that my obstacle to loading Windows is more properly a "Windows problem," not the fault of Linux. And, after many failed attempts to install Windows "through" my Linux OS, I begin to believe him. Linux will easily load in as a dual-boot alongside pre-installed Windows--but at all easily the other way around. 

Just as a suggestion...if you already possess the correct Windows install stuff, with COA. And system drivers, maybe it'd be easier to just grit your teeth and do a reformat and fresh install of Windows...THEN add your Linux alongside it.

Good luck.

---


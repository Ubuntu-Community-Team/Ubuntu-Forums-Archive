---
title: "Alternatives ways to create Windows USB?"
date: 2015-10-26
forum: Windows
---

### Post by remmas-sido on 2015-10-26
Hello guys 
what are some other ways to create Windows USB besides WinUSB? 
Thank you

---

### Post by howefield on 2015-10-26
Thread moved to the "*Windows*" forum.

---

### Post by remmas-sido on 2015-10-26
> **howefield said:**
> Thread moved to the "*Windows*" forum.

But I want to make a Windows USB from Ubuntu not from Windows.

---

### Post by yancek on 2015-10-26
> what are some other ways to create Windows USB besides WinUSB? 

The link below has an incredibly detailed, step by step tutorial on how to do this form Ubuntu.  Make sure you read through the tutorial entirely before beginning so you understand it.  If you get an error with the Disk Image mounter indiating the iso is too large, you can loop mount the iso before copying.

[http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by sudodus on 2016-10-15
Learning from the very good step by step tutorial the *[I]yancek*[/I] linked to in the previous post, I added a new feature in ***mkusb-nox***, so that it can create boot drives (USB sticks and memory cards ...) that can boot the Windows installer.

It is still only available in the unstable PPA, because it is not tested much yet. Try it if you still need it. See these links,

[mkusb-nox 11.1.2: added feature: make USB install drive for Windows](https://ubuntuforums.org/showthread.php?t=1958073&page=22&p=13554330#post13554330)

[mkusb/v7](https://help.ubuntu.com/community/mkusb/v7)

mkusb-nox works in all current Ubuntu versions with Windows 7 - 10, but you have to cope with a command line interface ;-)

---

### Post by C.S.Cameron on 2016-10-15
Windows XP can be run from a flash drive, very slow.
The only way to run later versions, is to stick the virtual machine on a thumb drive.
It can then be run on a Vbox host.
VirtualBox can also be run off a flash drive but, (my experience), to do so can disable vbox installed on the machine.
[http://www.howtogeek.com/188142/use-portable-virtualbox-to-take-virtual-machines-with-you-everywhere/](http://www.howtogeek.com/188142/use-portable-virtualbox-to-take-virtual-machines-with-you-everywhere/)
This is also very, very slow.

Edit:
If you just want to put the installer on flash drive, (Win 10), MS makes free "Media Creation Tool".

---

### Post by sudodus on 2016-10-15
I have Ubuntu 16.04.1 LTS (64-bit) installed in an SSD in an external box, that can be connected via both USB 3 and eSATA. It can boot in UEFI mode and BIOS mode so it is quite portable.

In this system I have VirtualBox and in Virtualbox I have Windows 10 :-)

The Ubuntu system works in several computers. Windows [in this virtual machine] is tested [and works] in computers with Intel i3 and i5 processors. I think it would be hard to run it with less than 4 GB RAM in the computer. I can use half of the RAM for the host system and half for the virtual machine.

---

### Post by C.S.Cameron on 2016-10-15
I have a Win 7 .VDI on an external HDD, with AutoCAD, Solidworks, CAESAR II, etc.
Plug it into my Ubuntu laptop, (that has a nearly full HDD), and run in VBox.
Can also run on my office Windows computer's VBox.
Just got a new 128GB flash drive to put it on as a back up drive while traveling.

Edit:
Should probably use mkusb to make a disk with huge Windows partition and put the VDI there, casper-rw only needs to be large enough for VBox, it makes sense to have VBox handy.

This would be a bootable self contained Windows flash drive powered by Ubuntu.

---

### Post by sudodus on 2016-10-16
I have never installed VirtualBox in a persistent live system. I'm looking forward to your results, C.S.Cameron :-)

---

### Post by C.S.Cameron on 2016-10-16
So far I have not been able to get VBox working on a 16.04 flash drive.
Works great with 14.04 flash drive though, not as slow as I recall.
(I guess I got to remember that the object is to run Windows and not to have the absolute latest edition of Ubuntu).
I will test on several machines and try 16.04.1.
mkusb works great

---

### Post by sudodus on 2016-10-16
Are you sure that you have run VBox in a persistent live host?

An installed system in a fast USB 3 pendrive should do the trick also with 16.04.1 LTS. It should work like my system in an external SSD.

---

### Post by sudodus on 2016-10-16
I was curious and tried to install VirtualBox in a persistent live system of Lubuntu 16.04.1 amd64. It works :-)

But if I remember correctly (from the previous installation), there was one extra thing I had to install: virtualbox-qt, maybe because I installed virtualbox with --no-install-recommends this time (to keep it small).

---

### Post by C.S.Cameron on 2016-10-17
I could not get vbox to install in 16.04 or 16.04.1 flash drive.
VBox 5.1.6.deb from virtualbox.org  is working out of the box with 14.04.3 except the hardware lock for several engineering programs does not seem to work.
At least AutoCAD is working acceptably, I always wanted a stand alone ACAD flash drive.
Yeh, I guess the USB3 flash drive is the reason it is faster than the last time I tried.

---

### Post by C.S.Cameron on 2016-10-17
Oops, double post.

---

### Post by sudodus on 2016-10-17
> **C.S.Cameron said:**
> I could not get vbox to install in 16.04 or 16.04.1 flash drive.
VBox 5.1.6.deb from virtualbox.org  is working out of the box with 14.04.3 except the hardware lock for several engineering programs does not seem to work.
At least AutoCAD is working acceptably, I always wanted a stand alone ACAD flash drive.
Yeh, I guess the USB3 flash drive is the reason it is faster than the last time I tried.

I made it simple and installed VirtualBox from the Ubuntu repositories (into 16.04.1). I think it will work for you too. (VirtualBox version 5.0.24_Ubuntu r108355 is in the repositories of 16.04).

---

### Post by C.S.Cameron on 2016-10-17
Have they ever got the version of VBox in the repositories able to access pen drives?
When booting from a mkusb 16.04 drive I am not able to install VBox from the Software Centre.

---

### Post by sudodus on 2016-10-17
Yes, after installing the 'Extension Pack', that you download from the VirtualBox web site.

I think 16.04.1 LTS is better than the original 16.04 LTS.

---

### Post by C.S.Cameron on 2016-10-17
I recall playing with vm's on a pendrive back in 2008.
The smallest O/S I could find that would run VBox was NimbleX, just a few KB.
sundar_ima added NimbleX to MultibootUSB, the menuentry for NimbleX can be found there
It worked on a pendrive but was too slow on USB2, (or was it USB1), to be practical.
USB3 looks like a whole new story.

Edit:
Looks to me like minimum footprint on the flash drive using Ubuntu 16.04.1 + VBox 5.1 is about 2GB,
1.4GB for O/S and 210MB for VB, 128GB-2GB leaves 126GB for another O/S and a moderate software collection.
Lots of RAM and USB3 help.

Sudodus is right, install VBox using Software Center.

---

### Post by C.S.Cameron on 2016-10-20
Procedure:
Obtain 128GB USB3 flash drive.
Use mkusb to create a persistent flash drive with 1% persistence.
Safely remove and replug flash drive.
Copy existing virtual machine image, (.vdi), to the "usbdata" partition on the flash drive.
Reboot into the USB
Connect to internet.
In Software & Updates, check "Software restricted by ..., etc.", then select "Updates" and ensure the machine will not will not automatically download or install updates.
In Software Center install VirtualBox,
From [www.virtualbox.org/wiki/downloads](www.virtualbox.org/wiki/downloads) download the extension pack.
Install the extension pack using VBox.
Run VBox and select New, when you get to Hard disk, select "Use an existing..." and choose the image in usbdata.
Boot the VM and install Guest Additions.
Join vboxusers group.

Results:
So far the drive is working in every computer I try, but slowly in computers without USB3 and/or less than 4GB RAM.
In a computer with lots of RAM some things almost seem faster, like orbiting complex rendered solids in AutoCAD.
AutoCAD 2013 & 2016, SolidWorks, Cosmos FEA, Staad, Autoplant, Rhino and SketchUp all work
Hilti Profis required a new serial number, and CAESAR II and CADWorx required re-installation of hardware locks.
Have had no luck connecting to a VPN.

---

### Post by sudodus on 2016-10-21
Thanks for sharing your experience, *C.S.Cameron* :-)

---


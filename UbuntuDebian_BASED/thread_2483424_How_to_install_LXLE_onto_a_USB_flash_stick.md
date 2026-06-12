---
title: "How to install LXLE onto a USB flash stick?"
date: 2023-01-29
forum: Ubuntu/Debian BASED
---

### Post by kuen2 on 2023-01-29
Please remove this post if it is inappropriate.  Thanks.
I am an ignorant to Ubuntu but want to learn LXLE and encounter many problems.  Unable to get information and/or assistance from other forums and/or supports, give it a try here.

Have many questions but the most urgent one is about how to install LXLE onto a USB flash stick.


My PC:
MB : G45T AM2 V:1.0
CPU: Intel Core2 Quad
RAM: DDR2 800 SDRAM 4G
PSU: Corsair RM650x
BIOS:American Megatrends V.02.16 
Flash stick, 2GB USB2 and 16GB USB3


Made an LXLE live bootable on a USB flash sticl five weeks ago. Tried to install it onto a 16GB flash stick three times, all failed.  Started all over again yesterday, downloaded LXLE focal 64bit ISO, made it a live bootable on a 2GB flash stick, ran it for many hours, and then tried to install it onto a 16GB USB flash stick. Failed again.


It failed the same way every time:
"encountered an error copying files to the hard disk
[Ermo 30] Read only file system: '/target/boot/vminus-5.0.4-113 generi'
This is often due to a faulty hard disk. It may help to check whether the hard disk is old and in need of replacement or to move the system to a cooler environment."


It seems that the LXLE installer tried to copy files to the hard disk.  There is no hard disk.


At the beginning of the installation, the installer found the 16GB USB flash stick.  And it seems that the installer was going install the OS onto the 16GB flash stick.  If an 8GB stick was found, the installer would say that the 8GB free space was not enough for the installation, it would need at least 8.6GB free space.


It seems that the installer knew, at the beginning, the installation was going to be onto a USB flsh stick. But, somehow, at the finishing of the installation, it tried to copy files to a hard drive.  


My questions:
1. Can LXLE focal be installed onto a USB flash stick?
2. How avoid the installer copying files to hard drive?


Thank you.

---

### Post by monkeybrain20122 on 2023-01-30
Yes it can be installed to the flask stick though it is probably going to be slow (an external hard disk would be a lot faster) It shouldn't try to write to the internal hard disk if you set the target properly in the installer. Check the drop down in the installer to make sure that it will install the bootloader in the flash stick instead of the internal hard disk. Some people suggest removing your internal hard disk first so you won't accidentally mess it up.

---

### Post by guiverc on 2023-01-30
LXLE is not Lubuntu, nor a[ *flavor* of Ubuntu]("https://ubuntu.com/desktop/flavours"). 

Lubuntu uses LXQt, having done so now for the last 9 releases which include all *supported* releases.

Lubuntu uses *calamares*, and reports the media to which it'll install in the final *summary* screen before the installation starts (see the second last picture in the latest [manual link]("https://manual.lubuntu.me/stable/1/1.3/installation.html") for example), thus you can see where its going to install to before you start. Don't proceed if you're not happy.

FYI:  the *manual* link I provided was the *stable* release, or 22.10; adjust for LTS release if required.

I realize you're asking about LXDE, but you've pasted in a Lubuntu section of the Ubuntu Forums, thus I'm answering here in what I consider an on-topic response (ie. talking about Lubuntu).

FYI:  In my experience, the `ubiquity` installer was easier to get to install the thumb-drive or *flash* media, but as Lubuntu only uses the `calamares` installer for all *supported* releases, I've limited myself to the on-topic Lubuntu products.  The ISO you download dictates the installer being used; and Lubuntu has historically used three different installers (*selected at download time when you grabbed the ISO*).

---

### Post by Impavidus on 2023-01-30
The installer doesn't care whether you install to an internal SSD, internal spinning hard drive, usb flash drive, spinning hard drive connected by usb, sd card or whatever. It just uses the phrase "hard drive" because that's what most people use. The phrase isn't adapted the the actual type of drive you use. Even if your drive is a superfluid neutronium device...

The error usually indicates a low-level I/O error on the storage device. USB flash drives don't last forever.

You mentioned something with a version number that appears a bit garbled, but could it be vmlinuz-5.4.0-113-generic? That indicates Ubuntu (or some flavour) release 20.04 LTS. It's not the latest LTS release and for much of the software not part of the main Ubuntu repositories (like the flavours, but LXLE isn't a flavour), it's only 3 months from end of life.

---

### Post by coffeecat on 2023-01-30
LXLE - *Thread moved to **Ubuntu/Debian based** sub-forum.*

---

### Post by sudodus on 2023-01-30
> **kuen2 said:**
> ...
It failed the same way every time:
"encountered an error copying files to the hard disk
[Ermo 30] Read only file system: '/target/boot/vminus-5.0.4-113 generi'
This is often due to a faulty hard disk. It may help to check whether the hard disk is old and in need of replacement or to move the system to a cooler environment."


It seems that the LXLE installer tried to copy files to the hard disk.  There is no hard disk.
...
My questions:
1. Can LXLE focal be installed onto a USB flash stick?
2. How avoid the installer copying files to hard drive?

Thank you.

I installed this 'focal' version of LXLE into a USB-connected drive (when booted from a pendrive with no internal drive connected. It worked for me.

I suggest that you try according the following steps:

- Please check with md5sum, that the download was good (that the iso file is not corrupted).

- **I noticed a pop up window during the installation, that asked for permission to unmount partitions on a drive (and I assume that it was about the target drive). I answered 'yes' to unmount those partitions. Maybe you misunderstood or did not dare answer 'yes', and the result was that your target drive was not available. So answer 'yes' to that question, if/when you get it**.

If still problems or other problems I suggest the following step(s):

- **Please refresh the target drive, the 16GB USB3 drive, by overwriting it with zeros**. You can do that with [mkusb](https://help.ubuntu.com/community/mkusb). It will make the drive more responsive.

- If still problems to install, in a second refreshing step, you can let mkusb make it a standard storage device (put a FAT32 partition on the drive).

Now chances should be better, that your installer will succeed.

[HR][/HR]
If still problems with LXLE, I suggest that you clone from an Ubuntu Server compressed image file. It is a very direct operation and likely to succeed. After booting into the installed Ubuntu Server you can install a desktop environment, for example one of the light-weight community versions Lubuntu, Ubuntu MATE or Xubuntu. See [this link](https://ubuntuforums.org/showthread.php?t=2474692) (read the whole thread with several posts).

I would recommend the jammy amd64 version (22.04.x LTS),

[cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/)

---

### Post by kuen2 on 2023-01-31
> **guiverc said:**
> LXLE is not Lubuntu, nor a[ *flavor* of Ubuntu]("https://ubuntu.com/desktop/flavours"). 

Lubuntu uses LXQt, having done so now for the last 9 releases which include all *supported* releases.

Lubuntu uses *calamares*, and reports the media to which it'll install in the final *summary* screen before the installation starts (see the second last picture in the latest [manual link]("https://manual.lubuntu.me/stable/1/1.3/installation.html") for example), thus you can see where its going to install to before you start. Don't proceed if you're not happy.

FYI:  the *manual* link I provided was the *stable* release, or 22.10; adjust for LTS release if required.

I realize you're asking about LXDE, but you've pasted in a Lubuntu section of the Ubuntu Forums, thus I'm answering here in what I consider an on-topic response (ie. talking about Lubuntu).

FYI:  In my experience, the `ubiquity` installer was easier to get to install the thumb-drive or *flash* media, but as Lubuntu only uses the `calamares` installer for all *supported* releases, I've limited myself to the on-topic Lubuntu products.  The ISO you download dictates the installer being used; and Lubuntu has historically used three different installers (*selected at download time when you grabbed the ISO*).


Thank you.


I know it is inappropriate to post LXLE issue here on an Ubuntu forum.  Just want to try my last luck here since I could not get help anywhere else.  


Do not know anything about Ubuntu or Lubuntu. Learnt from the internet that LXLE is based on Lubuntu or Xubuntu or both.  I may be wrong.  Excuse me if I am.

---

### Post by kuen2 on 2023-01-31
> **Impavidus said:**
> The installer doesn't care whether you install to an internal SSD, internal spinning hard drive, usb flash drive, spinning hard drive connected by usb, sd card or whatever. It just uses the phrase "hard drive" because that's what most people use. The phrase isn't adapted the the actual type of drive you use. Even if your drive is a superfluid neutronium device...

The error usually indicates a low-level I/O error on the storage device. USB flash drives don't last forever.

You mentioned something with a version number that appears a bit garbled, but could it be vmlinuz-5.4.0-113-generic? That indicates Ubuntu (or some flavour) release 20.04 LTS. It's not the latest LTS release and for much of the software not part of the main Ubuntu repositories (like the flavours, but LXLE isn't a flavour), it's only 3 months from end of life.

Thank you.


"The error usually indicates a low-level I/O error on the storage device."
Maybe a new flash stick will avoid this error.  I'll try.


"You mentioned something with a version number that appears a bit garbled, but could it be vmlinuz-5.4.0-113-generic?"
It is not barbled. I copied the message. "encountered an error copying files to the hard disk
[Ermo 30] Read only file system: '/target/boot/vminus-5.0.4-113 generi' "

---

### Post by kuen2 on 2023-01-31
> **sudodus said:**
> I installed this 'focal' version of LXLE into a USB-connected drive (when booted from a pendrive with no internal drive connected. It worked for me.

I suggest that you try according the following steps:

- Please check with md5sum, that the download was good (that the iso file is not corrupted).

- I noticed a pop up window during the installation, that asked for permission to unmount partitions on a drive (and I assume that it was about the target drive). I answered 'yes' to unmount those partitions. Maybe you misunderstood or did not dare answer 'yes', and the result was that your target drive was not available. So answer 'yes' to that question, if/when you get it.

If still problems or other problems I suggest the following step(s):

- Please refresh the target drive, the 16GB USB3 drive, by overwriting it with zeros. You can do that with [mkusb]("https://help.ubuntu.com/community/mkusb"). It will make the drive more responsive.

- If still problems to install, in a second refreshing step, you can let mkusb make it a standard storage device (put a FAT32 partition on the drive).

Now chances should be better, that your installer will succeed.

[HR][/HR]
If still problems with LXLE, I suggest that you clone from an Ubuntu Server compressed image file. It is a very direct operation and likely to succeed. After booting into the installed Ubuntu Server you can install a desktop environment, for example one of the light-weight community versions Lubuntu, Ubuntu MATE or Xubuntu. See [this link]("https://ubuntuforums.org/showthread.php?t=2474692") (read the whole thread with several posts).

I would recommend the jammy amd64 version (22.04.x LTS),

[cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/]("http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/")




Thank you.


"I installed this 'focal' version of LXLE into a USB-connected drive"
Is your USB-connected drive a hard drive, a hard drive mounted via USB port, like many external USB hard drives?


"booted from a pendrive"
Is this pendrive a live bootable?
Did you install LXLE from this live bootable pendrive?


"with no internal drive connected."
Do you mean that there is no hard drive inside the computer?


"Please check with md5sum, that the download was good (that the iso file is not corrupted)."
I do have some suspicions the downloaded ISO and the live LXLE on the pendrive.
<A> The ISO file was downloaded on a PC running Windows 10 and was running in a virtual mode. Windows defender could mistakingly corrupt the LXLE ISO file.
<B> The LXLE USB bootable on a flash pendrive was make by PowerISO on a PC running Windows 10.  Would this possibly corrupt the LXLE OS on the bootable flash pendrive?
<C> The LSLE live bootable was made by PowerISO which was run by Windows 10.  Would this cause any corruption to the LXLE OS on the bootable pendrive?
Could anyone of these factors corrupt the ISO file or LXLE bootable?

---

### Post by kuen2 on 2023-01-31
> **monkeybrain20122 said:**
> Yes it can be installed to the flask stick though it is probably going to be slow (an external hard disk would be a lot faster) It shouldn't try to write to the internal hard disk if you set the target properly in the installer. Check the drop down in the installer to make sure that it will install the bootloader in the flash stick instead of the internal hard disk. Some people suggest removing your internal hard disk first so you won't accidentally mess it up.

Thank you.

"Check the drop down in the installer..."
The installation is simple, only 7 steps.  There is no any drop down.  Almost everything is by default.  There is nothing to be changed or selected except for formatting the USB flash stick for installation.

"removing your internal hard disk first"
There is no hard drive, internal or external.  No any other drives.  Only a 2GB flash stick and a 16GB flash stick.

---

### Post by sudodus on 2023-01-31
> **kuen2 said:**
> Thank you.


"I installed this 'focal' version of LXLE into a USB-connected drive"
Is your USB-connected drive a hard drive, a hard drive mounted via USB port, like many external USB hard drives?

It's actually an SSD (connected via a USB-to-SATA-adapter). I use this configuration because it is faster than a simple pendrive, and according to my experience, will work in the same way (except speed).
> 

"booted from a pendrive"
Is this pendrive a live bootable?
Did you install LXLE from this live bootable pendrive?

Yes and yes :-)
> 


"with no internal drive connected."
Do you mean that there is no hard drive inside the computer?

Yes, in order to have a similar setup as yours.
> 


"Please check with md5sum, that the download was good (that the iso file is not corrupted)."
I do have some suspicions the downloaded ISO and the live LXLE on the pendrive.

You can check the iso file versus the md5 file  **[FONT=Courier New]LXLE-Focal-Release.iso.md5[/FONT]** (that you can get from the LXLE download page),
```

b9b252265cd79f84d459c7c3cacdf4ef  LXLE-Focal-Release.iso

```
In Windows you can use [md5summer](https://www.md5summer.org/) to check the md5sum.

In LXLE live (when booted from the installer drive) or some other Linux distro you can run
```

md5sum -c LXLE-Focal-Release.iso.md5

```
in the same directory as you have the iso file, and the result should be
```

LXLE-Focal-Release.iso: OK

```

> 
<A> The ISO file was downloaded on a PC running Windows 10 and was running in a virtual mode. Windows defender could mistakingly corrupt the LXLE ISO file.
<B> The LXLE USB bootable on a flash pendrive was make by PowerISO on a PC running Windows 10.  Would this possibly corrupt the LXLE OS on the bootable flash pendrive?

Maybe but probably not. I don't know the tool PowerISO. I use [Rufus](rufus.ie) for such purposes in Windows.
> 
<C> The LSLE live bootable was made by PowerISO which was run by Windows 10.  Would this cause any corruption to the LXLE OS on the bootable pendrive?
Could anyone of these factors corrupt the ISO file or LXLE bootable?
Many things can go wrong. I suggested workarounds for a couple of common problems in my previous post ([post #6](https://ubuntuforums.org/showthread.php?t=2483424&p=14128647#post14128647)).

---


---
title: "Is there a way to burn an .iso of Windows XP to a usb stick in Ubuntu?"
date: 2010-06-11
forum: The Cafe
---

### Post by PsychoDevon on 2010-06-11
There is a way to do it in Windows, but is there a way in Ubuntu?

---

### Post by sydbat on 2010-06-11
> **PsychoDevon said:**
> There is a way to do it in Windows, but is there a way in Ubuntu?Not sure of the legality of your question.

---

### Post by 98cwitr on 2010-06-11
try this

From Ubuntu Linux
The usb-creator utility can be installed using Synaptic Package Manager if not already present on your system. Some people have problems with usb-creator. You can also install and use UNetbootin to do the same thing.
Run usb-creator
Top pane, you will have to click "other", locate and select the ISO image
Plug the to-be-nuked USB stick into the computer, it should show up in the bottom pane titled "USB disk to use". (You may have to use GParted to format the USB Stick--I used 'ext3' as the format and it worked.)
Make sure you have the correct device selected before proceeding to create a USB startup disk!
There may be bugs during the formatting which will show up as two partitions when booting from the USB stick. Try selecting each of them and one should work. If not, restart the computer and try booting from the USB stick again.
If you get a DBus error with usb-creator, this bug report may be helpful: [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by FuturePilot on 2010-06-11
> **98cwitr said:**
> try this

From Ubuntu Linux
The usb-creator utility can be installed using Synaptic Package Manager if not already present on your system. Some people have problems with usb-creator. You can also install and use UNetbootin to do the same thing.
Run usb-creator
Top pane, you will have to click "other", locate and select the ISO image
Plug the to-be-nuked USB stick into the computer, it should show up in the bottom pane titled "USB disk to use". (You may have to use GParted to format the USB Stick--I used 'ext3' as the format and it worked.)
Make sure you have the correct device selected before proceeding to create a USB startup disk!
There may be bugs during the formatting which will show up as two partitions when booting from the USB stick. Try selecting each of them and one should work. If not, restart the computer and try booting from the USB stick again.
If you get a DBus error with usb-creator, this bug report may be helpful: [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I'm pretty sure neither USB-Creator or UNetBootin will work with an XP iso...

---

### Post by C.S.Cameron on 2010-06-11
What do you want, a bootable XP install disk or a Bootable XP O/S disk?

---

### Post by 98cwitr on 2010-06-11
...

---

### Post by PsychoDevon on 2010-06-11
> **C.S.Cameron said:**
> What do you want, a bootable XP install disk or a Bootable XP O/S disk?

I want to INSTALL Windows XP on my computer with my USB. So, I'm assuming that is the first one.

---

### Post by squilookle on 2010-06-11
I'm no expert on this and I may be very wrong, but I would be surprised if Microsoft had not put things in to prevent you from doing this, unless you have a netbook that shipped with xp, or something along those lines?

---

### Post by PsychoDevon on 2010-06-11
> **FuturePilot said:**
> I'm pretty sure neither USB-Creator or UNetBootin will work with an XP iso...

Also, UNetBootin does not work: I tried it awhile ago. I haven't tried USB-Creator yet, but I will today.

---

### Post by Dragonbite on 2010-06-11
```
dd if=/path/to/WindowsXP.iso of=/dev/sd* bs=4;sync
```

Of course the /dev/sd* will refer to your USB drive.

If it is not a .iso file yet, then can do the reverse:
```
dd if=/dev/cdrom0 of=~/Desktop/WindowsXP.iso
```

---

### Post by alphaniner on 2010-06-11
USB-creator depends on syslinux, so I doubt it would work either.

---

### Post by cariboo on 2010-06-11
The startup disk creator will only work with Ubuntu, any other distribution won't work.

---

### Post by C.S.Cameron on 2010-06-11
I figure you can do just about anything with dd so Dragonbite may be right.
It almost sounds too easy though.

---

### Post by C.S.Cameron on 2010-06-11
I tried: 
sudo dd if=/dev/cdrom of=/dev/sdb1
It copied all the XP install disk files over ok but...
The USB flash disk was not bootable.
In gparted the disk did not show a filesystem???

---

### Post by earthpigg on 2010-06-11
> **C.S.Cameron said:**
> I tried: 
sudo dd if=/dev/cdrom of=/dev/sdb1
It copied all the XP install disk files over ok but...
The USB flash disk was not bootable.
In gparted the disk did not show a filesystem???

*shrug* use gparted to flag it as bootable?

---

### Post by wilee-nilee on 2010-06-11
I have been able to have a bootable install of XP with the novicorp win to flash 0.6 beta, but only using the burned cd the iso wouldn't do it. This has to be done in a MS environment. If you want XP and only have Linux access use it in a virtual the iso will work fine.

---

### Post by C.S.Cameron on 2010-06-11
> *shrug* use gparted to flag it as bootable?

Yeh, I did that.
It was like it was trying to boot but could not find anything bootable.

I'm not that sure dd will clone a CD to USB.
I'd sure like to know the code if it did.

---

### Post by Dragonbite on 2010-06-12
> **C.S.Cameron said:**
> I tried: 
sudo dd if=/dev/cdrom of=/dev/sdb1
It copied all the XP install disk files over ok but...
The USB flash disk was not bootable.
In gparted the disk did not show a filesystem???
I don't know if this really matters, but I see you didn't include "bs=4M;sync".  I am not sure of the sync or how the bs actually modifies it but I believe it does make some difference.

The[_ Fedora page_]("http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo") didn't use "4", it used "bs=8M" and no "sync" on the end.  The "bs=4M;sync" I got from [_the openSUSE page_]("http://en.opensuse.org/Live_USB_stick").  Neither one of them were talking about Windows either.

Put the USB stick into the sytem
```
sudo fdisk -l
```
This will list all of the paritions on all of your disks

(assuming /dev/sdb1 is the USB drive)

/dev/sdb1 should have an asterisk (*****) under the Boot column, to the right of the "/dev/sdb1"  If not, then the disk is not set to boot.```
sudo fdisk /dev/sdb    #do not include the number, you are manipulating the WHOLE disk

m   #this will give you a list of commands
a   # toggle a bootable flag
1   #it will ask you for your partition number, if it is /dev/sdb1 then put "1"
w   #this will write out the changes.
``` I am fairly (but not completely) sure it will not effect the rest of the USB partition

---

### Post by C.S.Cameron on 2010-06-12
I have also tried adding the byte size = 4 sync option but did not find much difference.

I will fiddle with it some more later but am now trying to get vbox running in Puppy on the stick.

---

### Post by chris200x9 on 2010-06-12
probably won't work, just an idea could you maybe loop mount it and copy all the files over?

---

### Post by Frak on 2010-06-12
There's a proprietary Microsoft utility that they use internally that is able to make a flash-capable filesystem environment suitable for XP/Vista/7 installations, but like I said, it's internal use only. If you find another way, I'd be happy to hear it.

EDIT
Someone could go check out the MS Win7 USB creator and drag anything out if it if they can. Microsoft included a filesystem tool along with it.

---

### Post by K.Mandla on 2010-06-12
I was under the impression that the XP installer wouldn't work from USB anyway, without some serious acrobatics. That was a long time ago though, so it may be that some basement genius has gotten around that. 

You might do better to install XP to a small drive, mirror the drive with dd and then use that image to move the installation to elsewhere. Just an idea. ...

---


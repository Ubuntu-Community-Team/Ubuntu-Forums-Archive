---
title: "Ubuntu Gnome Remix"
date: 2012-10-21
forum: Ubuntu Development Version
---

### Post by Billxyzzy on 2012-10-21
This was a question left over from the last cycle so I thought I would bring it up again.
I have downloaded the beta's plus the latest release of ubuntu gnome remix.  As a privious poster stated I can't get DD to write a bootable ISO.  DD writes the files to disk ok but when I try to boot it there is no install.
And the disk is not recogonized as bootable.
This is a hard disk on a usb port.  It works fine for ubuntu installs as I have been using this method for the last couple of cycles.
Anyone got a workaround?

---

### Post by grahammechanical on 2012-10-23
Perhaps you have not seen this. It is very recent. The last edited date is 2012-10-23.

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10")

Regards.

---

### Post by mcellius on 2012-10-23
> **Billxyzzy said:**
> This was a question left over from the last cycle so I thought I would bring it up again.
I have downloaded the beta's plus the latest release of ubuntu gnome remix.  As a privious poster stated I can't get DD to write a bootable ISO.  DD writes the files to disk ok but when I try to boot it there is no install.
And the disk is not recogonized as bootable.
This is a hard disk on a usb port.  It works fine for ubuntu installs as I have been using this method for the last couple of cycles.
Anyone got a workaround?

I had the same symptoms, although I recognize that we might have different problems.

I had to use the Disks program to fix the problem: with the USB drive plugged in, I had to unmount it, then remove any partitions on it; then I formatted it for DOS/W95 and mounted it again (from Disks), then closed Disks.  I was then able to use Unetbootin - NOT Startup Disk Creator! - and it worked perfectly.

---

### Post by Billxyzzy on 2012-10-23
I am afraid that did not do what I expected.
The ISO was written to the wrong place.
It almost messed up my main drive.
Unetbootin does not do what I want at all.
What is strange is that Ubuntu ISO's work correctly and can be written with DD.   However this ISO
is just not correct.

---

### Post by GeorgeVita on 2012-10-25
> **Billxyzzy said:**
> ... I have downloaded the beta's plus the latest release of ubuntu gnome remix.  As a privious poster stated I can't get DD to write a bootable ISO.  DD writes the files to disk ok but when I try to boot it there is no install.
And the disk is not recogonized as bootable...
Anyone got a workaround?

**If you have Grub2 boot manager in your system, you can boot directly from .iso file without burning a CD.** 
Just copy the .iso into a USB memory (possibly works with your external Hard Disk) and try the following:

NOTE: you have to change .iso filename and/or drive/partition according to your system

- attach a USB memory
- copy the ubuntu-gnome-12.10-desktop-XYZ.iso into USB memory
- rename it to UGR.iso
(It would be easier to use a smaller filename as UGR.iso just to prevent any typing error)
- reboot
- when you see the Grub2 menu, press **C** for a command line
- find the name of the USB memory (mine was "hd1")
```
ls
```
- check the partition number/name ("hd1,1" is the same with "hd1,msdos1")
- set root directory to appropriate drive & partition (ex. hd1,1)
```
set root=(hd1,1)
```
- list all files to the new root and check for the existance of UGR.iso
```
ls /
```
- use loopback pointing to the iso file
```
loopback loop (hd1,1)/UGR.iso
```
- load kernel and supply boot parameters
```
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/UGR.iso quiet splash --
```
- load initial ramdisk to boot
```
initrd (loop)/casper/initrd.lz
```
- and finally ... BOOT it!
```
boot
```

I am writing this message via Ubuntu Gnome Remix beta which is fully functional (live mode). I did not test an installation while booted from .iso
Below is a photo of the "boot from iso procedure". Copy/edit/trim/upload of the photo plus this message done "on the fly" running the beta:
[[img]http://acomelectronics.com/GeorgeVita/UGRboot_sm.jpg[/img] (click for larger )]("http://acomelectronics.com/GeorgeVita/UGRboot.jpg")

---

### Post by Billxyzzy on 2012-10-25
George I have looked at what you have done.
It is interesting but does not do what I want.
(Install it on the disk of my choice)
If the file were directly bootable to the installation procedure then it would work like a 
CD/DVD and install.  I say again, I can use DD to write the ISO to my USB hard disk and boot it to install directly to a selected disk.  This is what Ubuntu does and works correctly.  The UGR iso does not have this capability.  This was solved at least two cycles ago by ubuntu for direct installation.
That is all I am trying to point out.

---

### Post by GeorgeVita on 2012-10-26
> **Billxyzzy said:**
> ... Install it on the disk of my choice ...
In my previous message I show you the "booting from .iso" procedure just in the case you did not knew it.
The idea is: use the .iso to boot and then install wherever you want it
DD is a basic powerful instruction which has a lot of switches and parameters to perform any copy/conversion BUT if you make a mistake you can delete anything in the target drive.

My philosophy is "try before, then suggest", so I just booted from the UGR .iso (using command line of Grub2), changed the size of my Ubuntu partition to a smaller one (with GParted), created a new 10GB partition for UGR and then installed it to my HD for a triple boot system. In parallel (at the same time) I am writing this note ...

As the installation has ended now, it asks for a reboot.
I will come back after restarting my system to edit this message from my UGR installation...

EDIT: everything went fine (as expected). Now running from the UGR installation.
Ubuntu is a great O.S. and will return to classical productive computing with the Gnome Remix!

---

### Post by Billxyzzy on 2012-10-26
George I am very well aware of the power of DD.
What I did not make clear is I use a separate disk for each installation so loss of data is not a problem.  During the install if I do not format the home partition I have all I want available again.
I have multiple disks and allocate each one to a different system. ( like 12) When testing I want as clear a system as I can get.  No extranious partitions to worry about.

---


---
title: "How do I get USB to work in VirtualBox 2.2.2"
date: 2009-05-22
forum: Virtualisation
---

### Post by Vignesh S on 2009-05-22
I am running VirtualBox 2.2.2 (the version that is supposed to support USB's) under Ubuntu 9.04 64-bit. The virtual machine is Windows XP SP1.

Since I want to transfer files over from my Ubuntu desktop to Windows XP, I need the USB to work so that I can transfer my files over on a USB stick, which is an Imation USB. However, what really stumps me is that the USB popup thingy doesn't appear in the VM, and is not visible in My Computer. Yet it seems to recognise my USB printer well enough. 

Maybe it stopped working after I went to Gedit and followed those intructions to enable USB support when it was intended for older versions of VirtualBox. I have also enabled my USB stick with the filter thingy in the settings of the Windows XP VM.

Got no idea what to do. Please help. I really want this VM to work so that I can actually use it. I am not quite an Ubuntu geek yet, but I might be there one day.

Oh by the way, a quick curious question. Are there any other virtualisation software other than VirtualBox and VirtualBox OSE (free or otherwise)?

---

### Post by dentharg on 2009-05-22
First, attach the stick ;)

Second, on status bar of VirtualBox you have an icon for USB devices. Click it and click on the name of USB stick; it should become visible to system inside and automounted.

I don't know if having Guest Additions is a must as I always install them.

---

### Post by Tux Aubrey on 2009-05-22
What dentharg said - but you should also be able to do it this way:

_Before_ you start the VM, in the VBox Console Window, select USB and work through the connection info. (see screenshot) That should make it automatic. Just note that the usb stick can only be available to the VM _or_ the host - not both at the same time.  Load up what you want to transfer to the VM before you start it.

And yes, VBoxGuestAdditions needs to installed in the VM.

With version 2.2.2 there's no need to do anything else (edit user groups etc for usb).

---

### Post by gharweeh on 2009-05-24
I just cant get USB to work on my windowsxp guest. There is no "usb" tab in my settings (ss). Got no idea what I am supposed to do. help please

---

### Post by roman_platonov on 2009-05-24
To enable full access to usb device you need make following steps:

1. add youself to group vboxusers
2. allow device to virtual box (Devices-usb- check device name)

i'm have some trouble with virtual box ose. Enstead of it a'm install virtualbox from aptitude. 

p.s. sorry for my english

---

### Post by Diamond.Dave on 2009-05-25
Do you *have* to use a USB to transfer?  Is it possible to carve out an NTFS or FAT partition on the hard drive, and mount/map to it from both my 9.04 host and a WinXP guest in Virtual Box?  Thanks to all!

---

### Post by itchanddino on 2009-05-25
Hello,
I'm having the same issues Vignesh S has.  I added lines to the mountdevsubfs.sh and mountkernfs.sh files, using the proper group ids.  I tweaked fstab, added myself the vboxusers groups and still no luck.  These tricks always worked for me in Hardy and Intrepid, but no luck with Jaunty.  Any thoughts?  Thanks!

---

### Post by roman_platonov on 2009-05-25
> **Diamond.Dave said:**
> Do you *have* to use a USB to transfer?  Is it possible to carve out an NTFS or FAT partition on the hard drive, and mount/map to it from both my 9.04 host and a WinXP guest in Virtual Box?  Thanks to all!
I'm think don't. You don't have access to any local devices, only devices connected throw the bus (usb, lan, shared folders). you can't get access to partition on you hdd.

---

### Post by gpstar on 2009-05-26
> **gharweeh said:**
> I just cant get USB to work on my windowsxp guest. There is no "usb" tab in my settings (ss). Got no idea what I am supposed to do. help please

the OSE version of Virtualbox doesn't have USB support. Download and install the non OSE version for USB support instead.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by MickSulley on 2009-06-03
I have spent months trying to get USB to work in virtualbox and I have just got it to work.  roman_platonov in this thread said that the user must be a member of the vboxusers group, once I had done that and rebooted the host system it works!  Note that you do need to reboot the host, not just the virtualbox.

I am running 2.2.4 in a Jaunty 64 bit host

Thank you roman_platonov!!!

---

### Post by oscarmeyer51 on 2009-06-03
You can get access to USB drives (and your local and networked drives) even though they show up as grayed out in the open source version of VirtualBox. How you ask?

Follow these directions:

1.    Install the VirtualBox Guest Additions per the instructions in the VirtualBox documentation.
2.    Once that install is complete and you have restarted the virtual guest, Select the Devices menu option.
3.    Select Shared Folders
4.    Select Transient Folders
5.    Select Add Folder (the small folder icon with the plus sign)
6.    Enter the Path of the USB device (it must be plugged in and recognized by your host system)
7.    Enter the Folder Name within the path you want to share with the guest system
8.    Choose Read-only or Make Permanent check boxes as you desire
9.    From your XP guest system, open up My Computer or Windows Explorer
10.   Select My Network Places
11.   Select Entire Network
12.   Select VirtualBox Shared Folders
13.   You should see the path you entered when you expand the VirtualBoxShared Folders. On my Ubuntu system, I can see all the drives under the /media folder. (I believe this is a bug, but it has no adverse effect for my needs).
14.   You can now select the specific folder that you want to share data with the guest system (and vice-versa).

FYI - This is also now in the VirtualBox documentation, well worth the read.

---

### Post by albinootje on 2009-06-03
> **Vignesh S said:**
> I am running VirtualBox 2.2.2 (the version that is supposed to support USB's) under Ubuntu 9.04 64-bit.

Please post the output of the following :
```

groups|grep vbox
dpkg -l|grep -i virtualbox

```
> 
Oh by the way, a quick curious question. Are there any other virtualisation software other than VirtualBox and VirtualBox OSE (free or otherwise)?

Qemu. [http://en.wikipedia.org/wiki/QEMU](http://en.wikipedia.org/wiki/QEMU)
Qemu and qemu-launcher are in the Ubuntu repositories, make sure you use the qemu kqemu module to speed things up.

See also : [http://www.phoronix.com/scan.php?page=news_item&px=NzEyNA](http://www.phoronix.com/scan.php?page=news_item&px=NzEyNA)

---


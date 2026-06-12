---
title: "VMWare USB"
date: 2007-11-03
forum: Virtualisation
---

### Post by adonikam on 2007-11-03
my phone (Cingular 2125 smartphone) doesn't appear under "USB Devices" in my vmware. This used to work in 6.10. Now i'm using 7.10.
Please help!
Thanks.
Chris

---

### Post by fjgaude on 2007-11-03
I think all you have to do is uncomment four lines in mountdevsubfs.sh file, like so:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Starting at line 42 uncomment these:

	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

Seems, for whatever reason, these weren't commented out in earlier versions of Ubuntu.Good luck, but let us know how you do.

---

### Post by jrpurvis on 2007-11-04
I updated to Ubuntu 7.10 and installed VMWare server today.  I have vmware server now running the VMs I had created previously.  I have been trying to get those VMs to see USB devices when I plug them into the host system.  So far I have not been successful.  I tried the patch suggested above as well as a suggestion I found elsewhere to add the line 'usb.generic.skipSetConfig = "TRUE" ' to the .vmx file for the VM.  

So far neither have worked.  When I check for removeable devices in the VM, none are listed.  On the host system, they are mounting and I can access with no problem.

SOLVED - - Guess I should have read the suggestions more closely.  After altering the file /etc/init.d/mountdevsubfs.sh as instructed above, I had to reboot the host.  That DOES allow usb devices such as thumb drives to be mounted on the VMs.

---

### Post by fjgaude on 2007-11-05
I have printers, scanners, UPS, all through USBs, works perfectly.

Glad to see you have it all up and running.

I don't know why those four lines were commented out in Gutsy, there weren't in Feisty as far as I can remember.

---

### Post by GuruX on 2007-11-05
Uncommenting solved it for me aswell. I had to reboot Ubuntu to get it going.

---

### Post by fjgaude on 2007-11-05
You likely didn't have to reboot but just restart the script:

```
sudo /etc/init.d/mountdevsubfs.sh restart
```

The more I use Linux the more I learn, starting with Redhat in 1996. <smile>

---

### Post by John9537 on 2007-11-09
This worked for me! Thanks :) It didnt work at first, even after a reboot so I added these two lines to the vmx file:

usb.present = "TRUE"
usb.generic.skipSetConfig = "TRUE"

I am not sure if one or the other would work on their own but it works now and I am not messing with it :) Thanks again!

John

---

### Post by ogee on 2007-11-21
John9537: Thanks for your tip. I had tried the patch above without luck then added your 2 lines, rebooted and then the VM saw the USB controller. The only odd thing is that to be able to see a flash drive I have to have it in a USB port before I power on the VM and then it will only see it as a USB 1.1 not 2.0. But at least I have it mostly working. Now to get the sound working :-)

---

### Post by uvdevnull on 2009-01-17
Those lines no longer exist in Intrepid's mountdevsubfs.sh file, so the suggestion above wasn't feasible and I didn't want to add all those lines because the file structure might have changed significantly since then.

However, I found this in VMWare's documentation on this topic, it's just a one-liner:

> **Using USB with a Linux Host**
On Linux hosts, VMware Server uses the USB device file system to connect to USB devices. 
In Linux systems that support USB, the USB device file system is usually /proc/bus/usb.
If your host operating system uses a different path to the USB device file system, run the following command as root to mount the file system to the expected location:
```
mount -t usbfs none /proc/bus/usb
```Do not attempt to add a USB drive’s device node (for example, /dev/sda) directory to the virtual machine as a hard disk. 

Worked for me :)

---


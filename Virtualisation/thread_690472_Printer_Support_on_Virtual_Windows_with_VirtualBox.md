---
title: "Printer Support on Virtual Windows with VirtualBox OSE"
date: 2008-02-07
forum: Virtualisation
---

### Post by lightnb on 2008-02-07
I'm running a virtual machine with Windows XP on Virtual Box OSE, on Kubuntu 7.10.

I have a printer that does not work (to the best of my knowledge and attempts to beat it into submission) on Linux. It works fine on windows.

Is there a way to use this printer from virtual box's Windows, even though it doesn't work with the host OS?

---

### Post by fjgaude on 2008-02-07
Sure, all you do once in Windows is to take the install disk that came with the printer and install the driver. Works just like it would in a host Windows. I have two printers working that way.

---

### Post by lightnb on 2008-02-07
I tried Installing the driver, but it still can't find the printer.

Do I have to turn on some sort of port passthrough in settings?

How can I verify that Windows "sees" the device?

---

### Post by fjgaude on 2008-02-07
Is it a USB printer? If so, go to Devices and click on the printer in question.

---

### Post by lightnb on 2008-02-07
> **fjgaude said:**
> Is it a USB printer? If so, go to Devices and click on the printer in question.

Yes, it is USB.

The KDE "add printer wizard" can see the printer attached. It gives the URI "usb://EPSON/Stylus%20Photo%20R320".

The printer doesn't show up in "device manager" in Windows.

---

### Post by fjgaude on 2008-02-07
Look for the Devices in some tab in VBox, not Windows.

---

### Post by lightnb on 2008-02-07
> **fjgaude said:**
> Look for the Devices in some tab in VBox, not Windows.

The devices tab has: shared folders, floppy, cdrom, network adapter, and "install guest additions".

---

### Post by fjgaude on 2008-02-07
Have you installed guest additions yet?

Also, have you done all the things in this post to setup VBox for USB useage?

[http://ubuntuforums.org/showthread.php?t=690713](http://ubuntuforums.org/showthread.php?t=690713)

Have a good time learning all the new things.

---

### Post by lightnb on 2008-02-10
> **fjgaude said:**
> Have you installed guest additions yet?

Also, have you done all the things in this post to setup VBox for USB useage?

[http://ubuntuforums.org/showthread.php?t=690713](http://ubuntuforums.org/showthread.php?t=690713)

Have a good time learning all the new things.

Yes, Guest additions are installed.

I've uncommented the lines:

```
mkdir -p /dev/bus/usb/.usbfs 
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644 
ln -s .usbfs/devices /dev/bus/usb/devices 
mount --rbind /dev/bus/usb /proc/bus/usb
```

in "/etc/init.d/mountdevsubfs.sh"

and changed 

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"
``` to MODE="0666" in "/etc/udev/rules.d/40-permissions.rules".

Then rebooted the host machine. Windows still doesn't see a printer.

How can I confirm the USB pass through is working?

---

### Post by fjgaude on 2008-02-10
In the VM where there a menu for Devices, do you see an USBs listed?

---

### Post by lightnb on 2008-02-12
> **fjgaude said:**
> In the VM where there a menu for Devices, do you see an USBs listed?

Negative. Do I need to install another package to make that work?

---

### Post by lightnb on 2008-02-12
I got it working! Apparently there's two versions of VirtualBox, one with USB support and one without.

Now that I've got the printer working with the windows side, is there a way for native linux apps to access the printer through the virtual machine? How?

---

### Post by fjgaude on 2008-02-12
Would you tell us which of the VBoxes have USB support and which don't?

I'm sure there is a way to hav Ubuntu use the printer that is setup in Windows but I've never done it, even tried to do it.

---

### Post by Sunforge on 2008-02-12
> **fjgaude said:**
> Would you tell us which of the VBoxes have USB support and which don't?

I'm sure there is a way to hav Ubuntu use the printer that is setup in Windows but I've never done it, even tried to do it.

The closed binary package has USB support, whilst the open package has USB support removed. 

Here's chapter and verse culled from Wikipedia:

[http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)


There are two versions of the VirtualBox software. The full VirtualBox package comes under a [proprietary]("http://en.wikipedia.org/wiki/Proprietary_software") license which allows using the software free-of-charge for personal and educational use and evaluation of the product.[[10]]("http://en.wikipedia.org/wiki/VirtualBox#_note-9") Licenses for commercial use of the full VirtualBox package can be purchased from innotek.
 A second version called the *VirtualBox Open Source Edition (OSE)* was released under the GPL, from which the following features are missing:[[11]]("http://en.wikipedia.org/wiki/VirtualBox#_note-10")



 [LIST]
[*]The built-in [Remote Desktop Protocol]("http://en.wikipedia.org/wiki/Remote_Desktop_Protocol") (RDP) server.
[*]USB support (see above) and the combination of running the RDP server with support of remote USB devices.
[*]The iSCSI support for virtual hard disks (see above).[/LIST]If you wish to download the closed version you can get it from here (the open source version is at the bottom of the page)

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by fjgaude on 2008-02-12
Thanks for the info... I used the closed version in parallel with vmware server for a number of weeks and decided to go with vmware, for its speed, features, maturity. All free... what a blessing.

---

### Post by Sunforge on 2008-02-13
Does VMWare Workstation have USB sharing? It's one feature that I find indispensible, mainly due to the fact that the Epson printer I have works very well under Windows and very oddly under Linux.

---

### Post by fjgaude on 2008-02-13
VMware Server sure has USB support. I use two printers, one is a Canon i9100, the other an Epson R220. and a scanner, all USBs. They work great under WinXP virtual.

I'm sure Workstation supports USB sharing.

---

### Post by Sunforge on 2008-02-13
Thanks for the information.

---

### Post by lightnb on 2008-02-14
So is there a way to share my printer from the virtual machine back to the host?

Or should I be switching to another virtual machine software program for that?

I have an Epson photo R320. Works great under Windows, but prints 50+ pages of garbage when you try to use it with Kubuntu.

---


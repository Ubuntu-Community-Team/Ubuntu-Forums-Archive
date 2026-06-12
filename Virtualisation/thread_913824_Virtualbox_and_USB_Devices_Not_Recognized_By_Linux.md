---
title: "Virtualbox and USB Devices Not Recognized By Linux"
date: 2008-09-08
forum: Virtualisation
---

### Post by tdrusk on 2008-09-08
I have a Line 6 Toneport GX which does not work in Linux. I installed VirtualBox and Windows XP on it. Windows XP does not recognize the Toneport either. I have installed the driver, but it just does not see the Toneport. 

What do I have to do to make it recognize this device?

---

### Post by Elfy on 2008-09-08
Which virtualbox do you have installed - afaik the version in the repos doesn't have usb support. If you have that installed - uninstall and install the version available here

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by cozmicharlie on 2008-09-08
You also may want to install version 2  - [http://tombuntu.com/index.php/2008/09/08/virtualbox-20-released/](http://tombuntu.com/index.php/2008/09/08/virtualbox-20-released/).

This also explains the problem with the version in the repos and adds to the info from tdrusk - [http://tombuntu.com/index.php/2008/08/06/upgrading-virtualbox-and-virtualizing-the-ubuntu-810-alphas/](http://tombuntu.com/index.php/2008/08/06/upgrading-virtualbox-and-virtualizing-the-ubuntu-810-alphas/)

---

### Post by AlanR8 on 2008-09-08
You could also try the fix below. Please note I don't take credit for it, It's something I picked up whilst Googling the USB issue.

USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:

[In Terminal] 
Code:
sudo gedit /etc/init.d/mountdevsubfs.sh
Inside, you'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Change it to look like this (uncomment out the region by deleting the "#'s"):
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
Save the changes, log out, and then log back in again for the changes to take place.

---

### Post by Elfy on 2008-09-08
> **cozmicharlie said:**
> You also may want to install version 2  - [http://tombuntu.com/index.php/2008/09/08/virtualbox-20-released/](http://tombuntu.com/index.php/2008/09/08/virtualbox-20-released/).

Which is what you get from the link I gave ;)

---

### Post by overdrank on 2008-09-08
Moved :)

---


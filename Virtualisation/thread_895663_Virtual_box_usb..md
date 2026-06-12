---
title: "Virtual box usb."
date: 2008-08-20
forum: Virtualisation
---

### Post by Dan6 on 2008-08-20
I'm probably the thousandth post on this, but I don't have time to lurk the forums very much. I am trying to configure usb2.0 in virtual box, I have got it as far as to recognize my devices but when I select them it says

Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 how do I fix this?

---

### Post by AClark on 2008-08-23
Assuming you are NOT using the OSE version from the repo.

**_#1 - I got this:_**

"By default USB support was disabled in virtualbox, so you&#8217;ll probably want to enable it. Otherwise you&#8217;ll get an error when you go into the &#8220;Settings&#8221; of your virtual machine. To correct this, you&#8217;ll need to edit the mountdevsubfs.sh file

sudo gedit /etc/init.d/mountdevsubfs.sh

Inside, you&#8217;ll see a block of code that looks like this

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Change it to look like this (uncomment out the region by deleting the &#8220;#&#8217;s&#8221;):

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Save the changes and exit.Now log out, and then log back in again for the changes to take place."

From here:
[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html)

**_#2 - Then this :_**
"I'm having some trouble with USB with VirtualBox. When I first installed virtual box, when I created a virtual machine, I received this error: Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).

I fixed with the solution from :
[http://yoten.blogspot.com/2007/06/vi...usb-error.html](http://yoten.blogspot.com/2007/06/vi...usb-error.html) by adding this to /etc/fstab

none /proc/bus/usb usbfs devgid=1001,devmode=666 0 0 

USB then became available for use."

From here:
[http://ubuntuforums.org/showthread.php?t=719074](http://ubuntuforums.org/showthread.php?t=719074)

**_#3 - And then from the VirtualBox Manual:_**
"  On Linux hosts, VirtualBox accesses USB devices on Linux through the usbfs file system. ***Therefore, the user executing VirtualBox needs read and write permission to the USB file system. Most distributions provide a group (e.g. usbusers) which the VirtualBox user needs to be added to.*** Also, VirtualBox can only proxy to virtual machines USB devices which are not claimed by a Linux host USB driver. Please refer to the Driver= entry in /proc/bus/usb/devices to see which devices are claimed."

There was no usbusers group in my Fiesty or my Hardy install so I added it and added myself to it.

Pay attention to the devgid= statement in /etc/fstab - it should be the id number of your usbusers group.

After I completed all three of these steps USB is working in all of my VBox installs.

I was getting very similar symptoms to yours just before I added the /etc/fstab line.

Good Luck - I hope this helps

---


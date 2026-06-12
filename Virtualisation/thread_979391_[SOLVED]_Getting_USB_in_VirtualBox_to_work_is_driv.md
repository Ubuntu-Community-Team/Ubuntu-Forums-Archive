---
title: "[SOLVED] Getting USB in VirtualBox to work is driving me insane!!! Please help!!!"
date: 2008-11-11
forum: Virtualisation
---

### Post by akelsall on 2008-11-11
I have been trying for the past week to get the USB to work inside VirtualBox. My host OS is Linux (Ubuntu 8.04.1) and the guest OS in WinXP.  I'm running VirtualBox v2.04. I'm pretty certain I downloaded this from Sun's website, so I believe I'm running the version that has USB support. Here's what I've tried so far:

1. edit /etc/init.d/mountdevsubfs.sh and uncommented the lines 
   below: 
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs          
        -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

2. Made sure I was added to the vboxusers and usbusers groups.

3. Added the following to /etc/udev/rules.d/40-permissions.rules 

    # USB devices (usbfs replacement)
   SUBSYSTEM=="usb_device",                    MODE="0664"

    # USBdevices (usbfs replacement)
    SUBSYSTEM=="usb_device", GROUP="usbusers", MODE="0664"


Here's partial output from the mount command:

$ mount | grep -i usb
procbususb on /proc/bus/usb type usbfs (rw)
usbfs on /proc/bus/usb type usbfs (rw,devgid=plugdev,devmode=664)

Output from groups command:

~$ groups
users adm cdrom floppy audio video plugdev scanner fuse lpadmin vboxusers usbfs usbusers

In VirtualBox itself, I have both checkboxes checked under USB (Enable USB Controller and Enable USB 2.0 (EHCI) Controller.

I've rebooted each time I made a change, and I've had NO luck getting the USB to work within WinXP (which is running as the Guest OS).

I feel like Peter in Office Space. "I gotta get out of here. I think I'm gonna lose it." hahaha  Please help me before I lose it. :lolflag:
](*,)](*,)

---

### Post by bumanie on 2008-11-11
[Follow this]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") -i think it still works this way. You need the proprietary 'free for home use' version, the OSE doesn't provide usb support.

---

### Post by Ocxic on 2008-11-11
you also have to add the USB device in the virtual machine settings.

---

### Post by akelsall on 2008-11-12
Ok, so can someone tell me how to add the USB driver to VBox, and how to determine which version of Vbox I have (when I click About..., all it tells me is it's version 2.9.4. If that's the wrong version, why do they even give the "appearance" that USBs are supported?).

I see a USB available on the Details tab, as well as within  the Windows virtual machine. Wouldn't you think for something this basic that Sun would automatically enable USB support?! ](*,)

Thanks for you suggestions and help,

Andy

---

### Post by tarps87 on 2008-11-12
The last version of virtualbox that didn't have USB support didn't have any menus or tab related to USB, since you have found it you probably are running the correct version

If USB support is enabled correctly there will be an option under devices on the menu bar of the guest machine, the USB device will have to be unmounted from the host machine which is why when you plug the device in it isn't automatically shown in the guest machine.
If this fails check the steps here:
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

### Post by akelsall on 2008-11-12
I was just looking on Sun's website and it appears that BOTH versions are at v2.0.4. So, how does one tell whether they have the OSE version, or the PUEL version? If you look at this link, you will see what I'm talking about:

     [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Here's what's displayed when I use help on my installed version:

/usr/bin$ VirtualBox --help
Sun xVM VirtualBox Graphical User Interface 2.0.4
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.



Thanks,

Andy

---

### Post by akelsall on 2008-11-13
Success!! I unmounted the USB from my Linux host (sudo umount  /proc/bus/usb), then launched WinXP within VirtualBox. Once WinXP was running, I clicked on **Devices | Mount CD/DVD ROM** and selected my flash drive (why they have a flash drive listed under CD/DVD is beyond me). After doing that, I could see and use my flash drive.

Thanks to everyone for their help (here, and other postings on this issue)!!

Andy

---


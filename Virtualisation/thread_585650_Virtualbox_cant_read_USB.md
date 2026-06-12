---
title: "Virtualbox cant read USB"
date: 2007-10-21
forum: Virtualisation
---

### Post by Pirate_Hunter on 2007-10-21
My issue is clearly stated above, I have installed Guest additions and virtualbox gives me the following error on setup:


```
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}


```

This is weird because Ubuntu 7.10 reads my attached usb devices without a problem yet VB tells me the host has the problem.

I would like if someone could tell me how to fix this problem please, i would be very grateful.

---

### Post by Buffalo Soldier on 2007-10-21
Lost the link to the original thread. I followed the instruction and add
```
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```
to **/etc/fstab** and restart.

---

### Post by Pirate_Hunter on 2007-10-21
^ - thanx that did the trick still its weird how it picks up the USB devices but it did so all good and now I can use my printer which means i wont fork out money to turboprint yet :)

Thanx again it is really appreciated ;D

---

### Post by kcy29581 on 2007-11-01
More info for you guys:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Basically, in the file /etc/init.d/mountdevsubfs.sh you need to edit the lines:

```
#
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```to look like this (removing four #'s):

```
#
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

```

Then follow the steps on the Virtualbox wiki:
 
 [http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)
 
 I know it say 7.04, but the steps apply to 7.10 as well.
 
 After this, once you have Windows running in Virtualbox, you can right-click on the USB icon in the bottom-right corner and select what USB device you want to activate. I usually ensure that any storage devices are unmounted in Ubuntu first, otherwise data loss may occur.

---


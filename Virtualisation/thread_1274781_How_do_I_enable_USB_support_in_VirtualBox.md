---
title: "How do I enable USB support in VirtualBox?"
date: 2009-09-24
forum: Virtualisation
---

### Post by Goveynetcom on 2009-09-24
I have used VirtualBox on Windows and now am using it on my Linux. So how do I enable USB support in virtual OS's? I have lots of files on my 4GB Flashdrive that I need to use and install on my virtual copy of WindowsXP. I'm stumped :-k...

---

### Post by tuxxy on 2009-09-24
I think that its still only able to do USB with the PUEL version which is available from VirtualBox homepage.  

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by Goveynetcom on 2009-09-24
2 for tuxxy...
Thanks, sort of, for the info. Too bad I don't have time tonight to work on it. 
Well thanks anyways.

---

### Post by VipX1 on 2009-09-26
I think you have to pay for the USB function to be enabled on your Virtualbox application. That's the one thing the free version does not have.:(

---

### Post by zupal1461 on 2009-09-26
nope... USB support is included with the free version... it's what i am using right now...

i am testing ubuntu before making a complete switch :) host OS is windows while guest OS is Ubuntu...

---

### Post by BunTai on 2009-09-26
open your terminal and type this :

    > sudo gedit /etc/init.d/mountdevsubfs.sh

your gedit application (text editor) will be like this:

>     #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

Change the script With this (copy dan replace)

> 
    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

Log Out & Log In Again Then Usb Can be use in your VB..

---


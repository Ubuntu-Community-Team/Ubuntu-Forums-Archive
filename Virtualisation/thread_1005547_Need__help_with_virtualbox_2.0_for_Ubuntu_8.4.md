---
title: "Need  help with virtualbox 2.0 for Ubuntu 8.4"
date: 2008-12-08
forum: Virtualisation
---

### Post by loveandequality on 2008-12-08
here is the problem yes i look all over more than 5 pages and more than a week now im going to rip my fingers away if i dont get this fix.


I keep getting this i dont know what to do::confused::confused:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}


im using the one that has USB support.

i think i need to do a terminal uninstalling but i dont know how to work terminal im new to any linux  so yea im dum.

please i need a Genius thanks.


SOLUTION HERE IN THIS WEBSITE:KS:[http://www.derekhildreth.com/blog/how-to-install-virtualbox-on-ubuntu-804lts-hardy-heron-tutorial/](http://www.derekhildreth.com/blog/how-to-install-virtualbox-on-ubuntu-804lts-hardy-heron-tutorial/)



Setup USB:

USB is disabled by default, so you’ll probably want to enable it.  Otherwise you’ll get an error when you go into the “Settings” of your virtual machine.  To  correct this, you’ll need to edit the mountdevsubfs.sh file:

[In Terminal] sudo gedit /etc/init.d/mountdevsubfs.sh

Inside, you’ll see a block of code that looks like this:

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount –rbind /dev/bus/usb /proc/bus/usb

Change it to look like this (uncomment out the region by deleting the “#’s”):

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount –rbind /dev/bus/usb /proc/bus/usb

Save the changes, log out, and then log back in again for the changes to take place.

---

### Post by howefield on 2008-12-08
[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by bodhi.zazen on 2008-12-08
> **loveandequality said:**
> here is the proble yes i look all over more than 5 pages and more than a week now im going to rip my fingers away if i dont get this fix.


I keep getting this i dont know what to do:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}


im using the one that has USB support.

i think i need to do a terminal uninstalling but i dont know how to work terminal im new to any linux  so yea im dum.

please i need a Genius.

The virtualization mega thread has a how to for enabling USB devices. The thread howefield linked to is an alternate method, although it is a little dated and you will need to read through the thread.

---

### Post by loveandequality on 2008-12-08
> **loveandequality said:**
> here is the problem yes i look all over more than 5 pages and more than a week now im going to rip my fingers away if i dont get this fix.


I keep getting this i dont know what to do:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}


im using the one that has USB support.

i think i need to do a terminal uninstalling but i dont know how to work terminal im new to any linux  so yea im dum.

please i need a Genius thanks.

thanks 4 all im going to try those suggestions :*

---

### Post by loveandequality on 2008-12-08
im going to dry up now i look around like you said nothing come up.

i seen some of ur post pretty good u are: [http://ubuntuforums.org/showthread.php?t=393582](http://ubuntuforums.org/showthread.php?t=393582)

but yea i have redowloaded IT like more than 10 times. I even try diferent versions idk what to do now. the whole thing works but the USB wich is the most important thing.

---

### Post by bodhi.zazen on 2008-12-09
> **loveandequality said:**
> im going to dry up now i look around like you said nothing come up.

i seen some of ur post pretty good u are: [http://ubuntuforums.org/showthread.php?t=393582](http://ubuntuforums.org/showthread.php?t=393582)

but yea i have redowloaded IT like more than 10 times. I even try diferent versions idk what to do now. the whole thing works but the USB wich is the most important thing.

From this thread : [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

Add this to /etc/fstab :

> [FONT=monospace]u[/FONT]sbfs   /proc/bus/usb   usbfs   auto,devmode=666   0   0

Then either remount or reboot.

---

### Post by dragos_iliescu_2005 on 2008-12-09
For using USB, you must to enable it first. Refer to the VirtualBox site about how to do that. In my case, I just copy and paste from the site, after reboot USB was enabled. The same with sharing folders. Pay attention to the Internet connection. Viruses are free to come on win virtual partition.

---


---
title: "Best free vitualzation app to run XP"
date: 2009-01-15
forum: Virtualisation
---

### Post by celticbhoy on 2009-01-15
I have VirtualBox installed onto which I have a copy of XP installed and working great. I find the lack of usb support a problem and would like to move to another app which will give me full usb support, and was wondering what the best of the free options were listing ease of use (setting up a virtual machine), and features.

Thnx for any suggestions ....

---

### Post by damis648 on 2009-01-15
Virtualbox has USB support, you just need the closed source version.
use
```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb-src http://download.virtualbox.org/virtualbox/debian intrepid non-free
```
and install the virtualbox-2.1 package.

EDIT: Also add
```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
to your fstab to make USB work.

---

### Post by celticbhoy on 2009-01-15
getting this :-

bash: deb: command not found

---

### Post by Therion on 2009-01-15
Those aren't command-line commands.  You need to add those lines to your /etc/apt/sources.list file so you can download the required files.

See this site:  [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by celticbhoy on 2009-01-15
Thanx I managed to sort it from another post - cheers anyway guys (or gals)

---

### Post by celticbhoy on 2009-01-15
Getting this when I try to start usb :-


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {f39438d7-abfd-409b-bc80-5f5291d92897}
Callee: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}

---

### Post by Therion on 2009-01-15
See this guide to installing and prepping VirtualBox:  
[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

The **Prepare booting your VM** section covers this error and how to fix it.


If you're running Intrepid, see here:
[http://www.pexperiences.com/2008/11/15/how-to-enable-usb-support-in-virtualbox-intrepid/](http://www.pexperiences.com/2008/11/15/how-to-enable-usb-support-in-virtualbox-intrepid/)

---

### Post by stefangr1 on 2009-01-15
You can also use vmware server. It has some extra features that vbox doesn't have (copy and paste between host and guest), and the newest version also has a web interface.

---

### Post by Karma_Police on 2009-01-16
Virtualbox has "Bidirectional" clipboard (and also "Host to guest" or "Guest to host").
As for web interface, it's more of a personal preference. Virtualbox also has CLI control.

---

### Post by stefangr1 on 2009-01-16
Ah, nice that they added a clipboard. The availability of it in vmware was actually the main reason for me to use it in stead of vbox a few years ago.

Does anyone btw. know how virtual disk performance of vbox compares with vmware?

---


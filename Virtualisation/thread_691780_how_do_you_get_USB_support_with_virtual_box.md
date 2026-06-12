---
title: "how do you get USB support with virtual box?"
date: 2008-02-09
forum: Virtualisation
---

### Post by TechDragon on 2008-02-09
how do you enable usb support with virtual box?

---

### Post by azimuth on 2008-02-09
There are 2 versions of Virtual Box. The OSE version that is avalable in the Ubuntu repositories and the Closed Source version. Read about them here [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by amingv on 2008-02-09
Perhaps this will help:
[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

Make a backup of any file you modify first.

---

### Post by jefferystone on 2008-02-09
I was getting this error:

 Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The
 service might be not installed on the host computer.

Added the following lines to /etc/fstab:

```
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

---------

This worked fine for me.  Taken from [[COLOR="Blue"]**Message #40 here.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=341740&page=4")

Sincerely,

Jeffery Stone

---

### Post by andriess on 2009-04-12
I found there is no need to create a special for usb users, so instead of using:

[INDENT]devgid=46[/INDENT]

I replaced the groupid (64) with the the existing group id of the vboxusers users group. To get the this id, type in:

[INDENT]grep vboxusers /etc/group[/INDENT]

On my machine this is "vboxusers:x:121:andries", eg. the group id is 121. This may be different on your machine :)

I'm runnig kubuntu 8.10

---

### Post by Louiezen on 2011-02-05
I don't know if this will help but give it a try, it works for me..

[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

---


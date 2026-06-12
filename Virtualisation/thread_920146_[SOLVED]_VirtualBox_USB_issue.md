---
title: "[SOLVED] VirtualBox USB issue"
date: 2008-09-15
forum: Virtualisation
---

### Post by pi.boy.travis on 2008-09-15
I can't seem to get USB working with VBox.  I'll attach a screenshot of the error message I get.

[ATTACH]85274[/ATTACH]

I've searched for packages named virtual box usb, but no avail.

Any ideas?

Thanks!

---

### Post by Pro-reason on 2008-09-15
Are you definitely using the proprietary version and not the VirtualBox from the Ubuntu repos?

---

### Post by mikewhatever on 2008-09-15
This worked for me:
> USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

/etc/init.d/mountdevsubfs.sh start

From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user. 

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

### Post by bumanie on 2008-09-15
Suspect you may be using the ose version from the repo's. To get usb function, you need to get the proprietary version (free for home use) from sun/innotek and then [follow this]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html")

---

### Post by pi.boy.travis on 2008-09-18
All set.  Thanks!

---


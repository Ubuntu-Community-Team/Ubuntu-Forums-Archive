---
title: "Virtualbox error dialogue - what now?"
date: 2007-12-09
forum: Virtualisation
---

### Post by zeller on 2007-12-09
I am getting the following error dialog (attached) and I don't know what it means or how to fix it. Can anyone tell me what steps I need to take?

---

### Post by rodo-&gt;dave on 2007-12-10
USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. 

Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). 

Then execute /etc/init.d/mountdevsubfs.sh start

From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user. 

Found this on: [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

### Post by zeller on 2007-12-10
Ok, I think I found a way around this.

[Go Here](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585) to solve this. From what I read it may work for other specific virtualization software too.

---

### Post by zeller on 2007-12-10
Is there any reason why using Virtualbox might just abruptly shut my laptop off? There is no shutdown process, it just instantly turns off during installation of XP. :(

---


---
title: "Help with Virtual Box"
date: 2010-07-28
forum: Virtualisation
---

### Post by arashiko28 on 2010-07-28
I have recently installed windows XP on virtualbox hoping to be able to update my Ipaq, now I have the same problem as in Ubuntu, just pass power to charge battery, but the OS does not recognize it.
I already installed the guest additions and restarted, yet nothing, on the USB interface, I have nothing!

Please, help! I need to reinstall some software urgently!

---

### Post by alastair on 2010-07-28
What version of VBox exactly? Does it support USB pass-through?

---

### Post by dustinmarlowe56 on 2010-07-28
i had almost the same issue. try runnning it as root [sudo virtualbox] 

whenever i do that it actually does allow me to connect usb devices to the vb

---

### Post by howefield on 2010-07-28
1. Download PUEL version from virtualbox.org website.
2. Add your user to the vboxusers group.
3. Enable USB support in the settings for you VM
4. Create a filter for your USB device.

Download the manual from 

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Section 3.10 deals with USB support.

---

### Post by howefield on 2010-07-28
> **dustinmarlowe56 said:**
> try runnning it as root [sudo virtualbox]

Usually better to run a graphical application with gksudo rather than sudo. But in this case, it probably isn't necessary or even advisable.

---

### Post by arashiko28 on 2010-07-28
It's the latest version, installed today. I got to make it recognize a working USB port, where I had the Ipaq connected, but can't mark it.
It's already registered...

Now I get an error message, but I already installed DKMS...

Also get a message about running: etc/init.d/vboxdrv setup, but It's not found...

---

### Post by arashiko28 on 2010-07-29
Ok, at least I got it to be recognized on the USB ports, now that I have this, what do I do?

> ~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 006 Device 002: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC[/COLOR]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b105 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by arashiko28 on 2010-07-29
Ok, so this is what I got so far.. not much, how do I get to check mark the device???
Please, don't let this thread to die, I have found a lot of people trying to fix this issue...:(

---

### Post by Meow27 on 2010-07-29
> **arashiko28 said:**
> 

Now I get an error message, but I already installed DKMS...

Also get a message about running: etc/init.d/vboxdrv setup, but It's not found...

i solve this problem by taking the same binary i installed virtualbox from, and reinstall.


as for the USB problem, try doing what i did 
[http://news.softpedia.com/news/How-t...t-111715.shtml](http://news.softpedia.com/news/How-t...t-111715.shtml)

also could you paste in a png or jpg next time?

---


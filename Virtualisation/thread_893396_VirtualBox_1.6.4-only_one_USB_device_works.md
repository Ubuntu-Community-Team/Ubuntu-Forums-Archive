---
title: "VirtualBox 1.6.4-only one USB device works"
date: 2008-08-18
forum: Virtualisation
---

### Post by Kokesh on 2008-08-18
I am running VBox 1.6.4 on Hardy Heron 32bit. I had all my USB devices working under VB, but now all the devices are greyed out in Machine menu, except the first one, Photosmart 7260, which I can use from XP guest system without any problems. No device filters, tried USB 2.0 ON/OFF in virtual machine's settings. Strange, isn't it?

Any suggestions?

---

### Post by cold_fu5ion on 2008-08-20
Hi,

I was just having this same problem. Here's where I found the solution:

[http://linuxchronicles.wordpress.com/2008/05/28/ubuntu-got-usb-in-virtualbox-160/](http://linuxchronicles.wordpress.com/2008/05/28/ubuntu-got-usb-in-virtualbox-160/)

I followed those instructions, rebooted and virtualbox would let me select my USB devices.
In order to use them, I had to go into XP's (XP is my guest) device manager and select install device driver for the USB controller.

Hope that helps.

---

### Post by Kokesh on 2008-08-20
GREAT! Thanks, works like a charm!

---


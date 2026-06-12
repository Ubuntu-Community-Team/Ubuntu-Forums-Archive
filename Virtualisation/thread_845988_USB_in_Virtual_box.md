---
title: "USB in Virtual box"
date: 2008-07-01
forum: Virtualisation
---

### Post by Deicist on 2008-07-01
Yes I know there's hundreds of threads devoted to this subject, however I've read all of those and followed numerous guides and I still can't get my USB devices working in Virtualbox (the commercial version, not OSE)

I've followed the guide [Here](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html) to no avail, I've added myself to the vboxusers and usbfs groups, changed lines in fstab and /etc/udev/rules.d/40-permissions.rules and nothing seems to make a difference.  Whenever I try to attach my device I get his error message:

```

Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

```

Anyone got any ideas?

---

### Post by xaris106 on 2008-07-12
could be a bit late but have you checked that you have enabled usb from the virtual machine settings?(in main VM window >settings>usb)
also try reinstall guest addons

---

### Post by fjf on 2008-07-13
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---


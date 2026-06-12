---
title: "[SOLVED] vbox ubuntu 8.10 into XP"
date: 2008-11-05
forum: Virtualisation
---

### Post by wahoobob on 2008-11-05
I am trying to put 8.10 into my wife's computer using virtual box.  Does anyone have a straight forward how to on this?  I keep getting small (640x480) screen and the instruction to change to 32 bit.  Just trying to convert her....

---

### Post by Coreigh on 2008-11-05
You want to run Ubuntu from inside Win XP? Isn't that what Wubi is for? Or am I mistaken/confused about Wubi?

---

### Post by StefAndrew on 2008-11-05
You have to install the guest additions to allow it to get a better resolution.  On the VBox window, after starting up Ubuntu in it, click on install Guest Additions.  This will put a CD in the drive in the virtual machine.  You will likely getting an autorun error message, just hit cancel.  Open up the command line and try this out:

```

cd /media/cdrom
sudo ./VBoxLinuxAdditions-x86.run

```

Type in your password, then it will run the installation and tell you to reboot once it's done.  After it reboots, it should automatically update to a better resolution for you.  Also, this is case sensitive, so make sure you catch the capital letters.

Let me know how that works for you.

---


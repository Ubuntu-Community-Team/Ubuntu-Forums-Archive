---
title: "webcam wont work"
date: 2009-07-19
forum: Ubuntu Studio
---

### Post by kingaj on 2009-07-19
i have a webcam that wont work in skype and cannot find a driver for it in hardware drivers. what should i do

---

### Post by mocha on 2009-08-07
Well, you need to check the output of dmesg, look for some message about the cam.  Also look at the output of lsusb (assuming it's a usb device), try a google search for the 8 digit number that you get.  You'll probably have to track down a hacked driver and compile a module.  It's not hard if someone has created a driver.  It's usually just a simple "make && make install" and then edit /etc/modules and add the name of the module to the end of the file so it loads on boot.  Use a simple program like camstream for testing.

---

### Post by reve99 on 2009-12-18
didn't get it?

---


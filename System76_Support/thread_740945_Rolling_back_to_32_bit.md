---
title: "Rolling back to 32 bit"
date: 2008-03-31
forum: System76 Support
---

### Post by darkknight045 on 2008-03-31
I have been debating re-installing Ubuntu on my Gazelle, the 64-bit version has been problematic for me.  My question is as follows:  Does the System76 Update support 32-bit ubuntu, and also how would I reinstall Envy and the System76 Update should I attempt this?

---

### Post by thomasaaron on 2008-03-31
If you have one of the newer Gazelles (i.e. the current line-up) we don't really support 32-bit on it anymore. 64-bit is much better.

The System76 driver will run on 32-bit, though, and fix the sound, etc... However, it may not be as much help with suspend and hibernate.

With older Gazelles running Ubuntu up to Gutsy, the driver should support 32-bit just fine.

Also, you do not need to install Envy. Just install Ubuntu, install and run the system76 driver, and you should be fine.

To install the driver:

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.1.7.deb](http://planet76.com/repositories/system76-driver-2.1.7.deb)
sudo dpkg -i system76-driver-2.1.7.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer.

---


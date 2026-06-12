---
title: "Introduction to Virtualization class"
date: 2007-11-02
forum: Virtualisation
---

### Post by mohnkern on 2007-11-02
I'm offering an introduction to virtualization class next month at the [MLC]("http://learning.mohnkern.com").  This class will cover the basics of installing VirtualBox and Vmware on an Ubuntu machine, and creating your first vm.

If you've been interested in exploring virtualization, but didn't know where to start, this is a class where you can get your feet wet.

The class is free.

[http://learning.mohnkern.com](http://learning.mohnkern.com)

---

### Post by 52rockwell on 2007-11-02
Hi,
I justgot virtualbox going today,XP on Gutsey. 
Can you tell me what I need to add to my
/proc/bus/usb/
folder to get my vm to see my usb key? I would appreciate the help.

  I have followed the instructions in the user FAQ:
USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

/etc/init.d/mountdevsubfs.sh start

From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user.

    but I still cant see my usb key in my virualbox.

---


---
title: "Accessing windows, usb, from linux guest in VirtualBox windows host?"
date: 2014-01-12
forum: Virtualisation
---

### Post by AussieGuy on 2014-01-12
I am spending six months in a position at an institution which has very strict IT policies, and the only way I can legitimately run linux is as a virtual machine in VirtualBox running under Windows 7 Enterprise.  So far so good: I can download and install everything I like, and the linux experience is seamless, if sometimes a little slow.  Nothing I can't live with, though.

However - one thing I haven't been able to work out is how to move files between linux and windows, or to access an external USB disk from linux.  USB is indeed enabled in the virtual machine settings, but when I insert a USB key, nothing happens (at least, nothing in linux).  I'm sure it's very simple, but as this is my first foray into the delights of virtualiztion, I'm completely stumped.

Any advice would be very welcome!

---

### Post by TheFu on 2014-01-13
Virtual Machines should be almost as fast as native, if only 1 VM is running, sparse vHDD allocation is avoided, a full core is allocated to the VM, at least a Core2Duo CPU is being used and 1G of RAM is provided for both the VM and the hostOS. If you aren't seeing that level of performance, please review [this article]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox") for tuning settings. As long as the workload is NOT using high end graphics, 90+% of native performance should be expected. When running full screen, I forget I'm inside a VM. It is THAT fast.

Is the "extension pak" properly installed?  This is mandatory for USB access to work.

In many companies, USB ports are disabled. Do your ports work from windows with the same USB devices? Not disabled in the BIOS?  Also, not every type of USB device is supported.  Try a few different flash drives, please.

If you just want to see the contents of a flash drive, I wouldn't expect this to auto-open.  Does the device get seen according to **dmesg**?  If so, then just mount the device manually.  If the flash drive is not seen by dmesg, then the OS doesn't see it and nothing can be done until that aspect is corrected.  If Windows "grabs" the USB device before Vbox can pass it through, you'll need to fix that. Only 1 OS can hold the USB connection at a time.

BTW virtualbox has a great online manual. The USB section: [https://www.virtualbox.org/manual/ch03.html#idp55342960](https://www.virtualbox.org/manual/ch03.html#idp55342960)

You've probably tried all these things, so if any issues shown in the log files can be posted, that should help figure out the root cause. Please post those wrapped in "code" tags. Thanks.

---

### Post by AussieGuy on 2014-01-13
What I did in the end was use Windows to access the usb drive files.  Then I set up a shared folder in the virtual machine settings, and mounted it with "mount -t vboxsf".  So I ended up with the files I wanted; it was a two step process (usb -> windows -> linux).

Actually the speed settings are mainly due to my maxing out RAM (having too many hungry applications open, and then compiling a few packages from source code.)

---


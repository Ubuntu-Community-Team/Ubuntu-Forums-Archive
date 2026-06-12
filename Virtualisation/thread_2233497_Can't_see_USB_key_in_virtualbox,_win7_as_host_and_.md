---
title: "Can't see USB key in virtualbox, win7 as host and ubuntu as vitrual machine."
date: 2014-07-08
forum: Virtualisation
---

### Post by orangerdd on 2014-07-08
I searched in the forum but can only find issues of ubuntu as host and windows as guest. 

However, I am on the opposite. I'm using win7 and install an ubuntu 14.04 in virtualbox 4.3.10.

I have already set USB controller and added usb filter in virtualbox settings. When enable my SanDisk 32GB usb drive for virtual machine, it disappears form win7 and should have appeared in Ubuntu. However I can't find any sign of this drive in ubuntu.

Can someone help me?

---

### Post by TheFu on 2014-07-09
Which forums did you search?  The virtualbox.org forums will be full of that setup and solutions.

I ran vbox the same way for a few years.  Sounds like you are doing everything correctly.  What do the log files say? Check both in linux and Windows.
Depending on your clientOS settings, you may need to manually mount the storage after it is seen.  Check **dmesg** for that.

Only 1 machine (real or VM) can have control of a USB device at a time, so if the hostOS doesn't have the USB device, then a VM probably does.  Have you taken the USB device from inside the VM using the vbox menu? Do this while the VM is running. That will only make it available to the OS to see - it doesn't mount it, unless your settings do that automatically.

Also - [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB) may be of help, though I didn't read it.

---

### Post by SeijiSensei on 2014-07-09
Did you install the Extension Pack?  You need that to use USB devices.  Install it in both the host and guest.

---

### Post by TheFu on 2014-07-09
> **SeijiSensei said:**
> Did you install the Extension Pack?  You need that to use USB devices.  Install it in both the host and guest.

No need to install the pack on the Windows HostOS. Guest extensions are only needed inside the clientOS.  Of course, be certain to read the license - it isn't GPL like the rest of virtualbox.

---

### Post by SeijiSensei on 2014-07-09
I believe VirtualBox requires the Extensions to be installed on both sides to enable the bidirectional clipboard between host and guest.  I could be wrong though.

---

### Post by orangerdd on 2014-07-09
> **SeijiSensei said:**
> I believe VirtualBox requires the Extensions to be installed on both sides to enable the bidirectional clipboard between host and guest.  I could be wrong though.

I have installed Vbox extension already and it functioned well.

However I found another interesting thing. I have another 4GB usb drive which works properly. When I insert this 4GB usb stick, ubuntu recognized it immediately and was fully functional.

So that means what? Control chip of SanDisk drive? Or capacity too large?

---

### Post by TheFu on 2014-07-09
There is a checkbox in the VM settings to enable clipboard support. No guest additions to install on the hostOS-side.

---

### Post by SeijiSensei on 2014-07-09
Thanks for setting me straight on this.  I recall thinking that installing what used to be called the "Guest Extensions" on the host made no sense.  I installed the Extensions on both sides anyway just in case.

---


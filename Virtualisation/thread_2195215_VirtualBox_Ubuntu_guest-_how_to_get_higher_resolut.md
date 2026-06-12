---
title: "VirtualBox Ubuntu guest- how to get higher resolution full screen? Windows 7 host"
date: 2013-12-22
forum: Virtualisation
---

### Post by matthewkirsch1 on 2013-12-22
I'm setting up an Ubuntu VM in my Windows 7 installation. I have an i7 processor, a dedicated laptop graphics card with 256MB video memory, and 6 GB RAM. I've allocated 128 MB video memory to the VM. 

How can increase the VM's fullscreen resolution? Right now it's capped at 1024x768. My laptop screen is 1368x768(?).

---

### Post by QIII on 2013-12-22
While in the guest OS, have you installed the VirtualBox Guest Additions?

---

### Post by andrew.46 on 2014-01-14
> **matthewkirsch1 said:**
> I've allocated 128 MB video memory to the VM. 

It will not fix your issue I suspect but you can actually allocate more video memory by altering the memory allocated to 'Display VRAMSize' in the xml file that controls the VM. Not sure what a safe upper limit is but I have allocated 256megs quite successfully. Q111's suggestion would point to a solution though...

**Edit**: Mind you [the manual suggests]("http://www.virtualbox.org/manual/ch03.html#settings-display") that an increase may very well be useful:

```

Video memory size

   This sets the size of the memory provided by the virtual graphics card available to the guest, in MB. 
As with the main memory, the specified amount will be allocated from the host's resident memory. 
Based on the amount of video memory, higher resolutions and color depths may be available.

```

---

### Post by joe_beasley on 2014-01-14
Install the guest additions, and then you should be able to stretch the window to fill the full screen.

---


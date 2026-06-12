---
title: "Virtualbox USB read errors"
date: 2008-02-02
forum: Virtualisation
---

### Post by sportman1280 on 2008-02-02
I have the USB working on Virtualbox, however i receive I/O errors when i try to access the drive in windows.  Im not sure where to start troubleshooting on this, but theres got to be a good starting point...

---

### Post by Hmarroqu on 2008-02-03
hmmm, what did you do when you installed the vmachine?

I followed this dude..[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)
..worked out well.

---

### Post by sportman1280 on 2008-02-03
i have it installed right i think because of the fact that i can print and scan with my usb printer/scanner....  One note is that im running vista.  would that be causing the issues?

---

### Post by Hmarroqu on 2008-02-03
not sure about vista being the issue... did you do the following in the installation: >  1. Create a group called usbusers 
  2. Add yourself to this group 
  3. Edit the file /etc/udev/rules.d/40-permissions.rules (for this, you must have administrative privileges) 
 [INDENT]  3.1 Search for the following lines 
 # USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                    MODE="0664"
[/INDENT] [INDENT]  3.2 Change them to the following 
 # USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", GROUP="usbusers", MODE="0664"
[/INDENT]

---

### Post by Hmarroqu on 2008-02-03
hmm. I think i misunderstood your initial post....do you mean the drive as in the virtual harddrive or which one?....usb works i get that....

---

### Post by sportman1280 on 2008-02-03
USB works... halfway.  when i put a flash drive in. the drivers load.  it shows up as a device in windows.  i double click on the drive and i get an I/O error. it wont open my flash drive :(.

---

### Post by Hmarroqu on 2008-02-03
look in Device Manager to see if there are any Listed USB Ports shown as not working or needing an updated driver.

may be a driver issue with the virtual machine?

---


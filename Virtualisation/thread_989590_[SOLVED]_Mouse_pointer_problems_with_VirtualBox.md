---
title: "[SOLVED] Mouse pointer problems with VirtualBox"
date: 2008-11-21
forum: Virtualisation
---

### Post by J03y on 2008-11-21
Hello, I have a problem trying to get the mouse pointer to work on VirtualBox. Every time I click on the VirtualBox window, a message pops up saying: 

'You have clicked the mouse inside the Virtual Machine display or pressed the host key. This will cause the Virtual Machine to capture the host mouse pointer (only if the mouse pointer integration is not currently supported by the guest OS) and the keyboard, which will make them unavailable to other applications running on your host machine'. 

How do I get the mouse pointer work with VirtualBox?

---

### Post by bodhi.zazen on 2008-11-21
That is normal functioning. If you wish mouse integration you need to install the virtualbox guest additions.

See the mega sticky at the top, "Guest enhancements"

---

### Post by Anencephalic on 2009-01-28
This is not solved for me.

I also get the capture dialog window but, whether I click "Capture" or "Cancel", my mouse doesn't get captured.  As J03y posted, the dialog pops up *every* time I click in the window, not just the first time.  

This isn't a guest enhancements issue because I can't get into the VM console to install the OS.  I get the impression that guest enhancements does for VirtualBox what VMtools does for VMware.  Those must be installed after the OS gets installed.  How can I get the guest OS to see my mouse so I can install it?

By the way, my keyboard gets captured.  This is only an issue with the mouse.  I can only get so far into the OS installation process without a mouse though.

My host OS is Ubuntu 8.04 Desktop.  My kernel is 2.6.24-16-generic.  I am using VirtualBox Graphical User Interface Version 1.5.6_OSE.  My guest OS is Ubuntu 8.04 Desktop.

Thanks.

---

### Post by Anencephalic on 2009-02-02
I accidentally solved it.  If you check "Do not show this dialog again" (or whatever it actually says), then click in the guest OS console window, your mouse gets captured.

It seems that this is a bug since the keyboard gets captured immediately after clicking "Capture", but the mouse doesn't until you check the above mentioned box.

---


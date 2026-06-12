---
title: "Seamless Windows XP resolution issues"
date: 2010-09-15
forum: Virtualisation
---

### Post by Darkness Des on 2010-09-15
As per forum rules/guidelines, I would say I'm an intermediate/advanced user. On to the actual problem.
Because I recently got into some work with doing some graphic design (among other things), and I wish to use Paint.NET and several other windows-only programs within Ubuntu. So, I tried setting up a (not so) seamless desktop. My resolution is 1366x768, and I need to set my Windows desktop 1366x702 (dock and panel subtracted) to make it fit. The problem here is that I can't get it to go over 1300x660. Any suggestions on how to fix this?

---

### Post by TheFu on 2010-09-17
If you are using VirtualBox (seamless mode assumption), then just install the guest additions into Windows and grab the window border to resize it.

I doubt you need to do this, but for non-standard screen resolutions that are not controlled by VirtualBox, you'll need to manually edit the x-org config file. Mine is in /etc/X11/xorg.conf - google for the specific settings and stanzas that you'll want in that file. Newer Ubuntu releases don't really require this unless you are doing something more complex, like strange screen resolutions, 2+ monitors that the GUI tools don't handle or rotated screens. The file may not even exist on most Ubuntus, but if it does, it should be honored by X11.

---

### Post by Darkness Des on 2010-09-17
Yes, I am using Virtual Box but I do have Guest Additions installed. My problem is not with Ubuntu failing to recognize my screen resolution - it does that without a problem - but with XP. Editing xorg.conf doesn't control the resolution of a Virtual machine, to the extent of my knowledge. Here is an example in a screenshot of what I'm talking about.

---

### Post by slooksterpsv on 2010-09-17
You can have your panels hide with the buttons, that way it'll give you the full resolution. Right click on the panel, go to properties -> show hide buttons

EDIT: 1360x768 is the largest I could get mine to go in seamless mode by doing the above.

---

### Post by Darkness Des on 2010-09-18
Ah, I'll guess I'll just have to live the six pixels every now and then when I want Windows running. Thank you!

---


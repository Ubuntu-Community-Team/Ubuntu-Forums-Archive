---
title: "VMware player in Gutsy."
date: 2007-11-13
forum: Virtualisation
---

### Post by ascus4 on 2007-11-13
I just installed VMware player 2.x in Gutsy.  It tells me that it cannot find my cd rom which contains my WinXP installation disk.

It returns error:
cdrom.iso does not exist. and therefore cannot be connected as a cd-rom image.  Virtual device ide1:0 will start disconnected.

My config file (template-windows.vmx) states:
ide0:0.filename = 20GB.vmdk
ide0:0.filename = cdrom.iso

I realize that I am trying to use an install CD, not an iso file to install WinXP.  What would I change the filename = cdrom.iso to in order to get this to work?

Thanks in advance.

EDIT:  Changing it to cdrom0 did not help.

---

### Post by j.bunce on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

May help...

---

### Post by ascus4 on 2007-11-13
I'll give that a shot tonight.  
Thanks.

It appears as though VMware is installed and running.  It just says that it can't find ant bootable files, even though I have a bootable CD in the drive.

---

### Post by fjgaude on 2007-11-13
Try a <ctrl>-C from the keyboard.

---


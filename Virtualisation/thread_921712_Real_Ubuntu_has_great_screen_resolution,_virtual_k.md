---
title: "Real Ubuntu has great screen resolution, virtual kubuntu doesn't"
date: 2008-09-16
forum: Virtualisation
---

### Post by fiddler616 on 2008-09-16
Well, the title really says it all.
To expand: My 'real' installation of Ubuntu had support for my...1280x1024? (Or close to that) screen resolution.
A virtual Kubuntu (using VirtualBox) only lets me go up to 800x600.
Why?

---

### Post by howefield on 2008-09-16
Installing guest additions for your guest system should improve the video resolution.

---

### Post by fiddler616 on 2008-09-16
> **howefield said:**
> Installing guest additions for your guest system should improve the video resolution.
Which is accomplished...how?

---

### Post by howefield on 2008-09-16
Load up your virtual machine, choose the Devices menu and select install guest additions.

---

### Post by mexlinux on 2008-09-16
I have kubuntu intrepid in virtualbox, I have already installed the guest additions, I can see improvements like mouse focus, but no changes in maximum possible screen resolution...

---

### Post by Peter Frank on 2008-09-16
I once had this problem, and solved it by editing the screen resolution in "/etc/X11/xorg.conf" in the virtual Linux system and rebooting it.

---

### Post by mexlinux on 2008-09-23
This one worked:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=620828&page=2]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=620828&page=2")

---


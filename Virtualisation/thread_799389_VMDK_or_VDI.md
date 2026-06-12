---
title: "VMDK or VDI?"
date: 2008-05-19
forum: Virtualisation
---

### Post by hamhock on 2008-05-19
I will be installing win2k as guest - should I use VDI or VMDK?

I also want to enable win2k to access a NTFS partition.  Should I use VDI or VMDK for this "slave drive."

I'm mainly concerned if there is a noticeable speed difference.

---

### Post by abhiroopb on 2008-05-19
as far as I know VDI is used by virtualbox and VMDK by VMware, so its more a choice between the two programs. I personally prefer virtualbox, its easy to install, supports USB, and its a lot faster than VMWare.

---

### Post by hamhock on 2008-05-19
> **abhiroopb said:**
> as far as I know VDI is used by virtualbox and VMDK by VMware, so its more a choice between the two programs. I personally prefer virtualbox, its easy to install, supports USB, and its a lot faster than VMWare.

actually VMDK is for virtualbox as well - just not sure which one I should use for both the primary and slave IDE's in virtualbox.  here is one person's experience with both VDI and VMDK on virtualbox:

[http://ubuntuforums.org/archive/index.php/t-662018.html](http://ubuntuforums.org/archive/index.php/t-662018.html)

---

### Post by abhiroopb on 2008-05-19
Thanks for clarifying. Still VDI is the one created by default (or at least was for me), so I'd recommend sticking to that!

---


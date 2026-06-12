---
title: "Upgraded kernel now vbox will not start"
date: 2009-03-03
forum: Virtualisation
---

### Post by wildmanne39 on 2009-03-03
Hi everyone, Can some one please tell me how to fix vbox I upgraded my kernel and now I get an error that says I need to reset up my kernel can anyone tell me how to do that, please be exact as possible I am still learning. Thanks to everyone in advance, I really appreciate any help concerning this matter.

---

### Post by edwardLS on 2009-03-03
I am not sure that this will help you fix your kernel now, but I have used VirtualBox and have installed/upgraded my kernel with no problem.  I "believe" this is because I followed the instruction in the VirtualBox User's Manuel section 2.3.2 "The VirtualBox kernel module".

I did this on my first try with VB, and I have had no problems.  I wish I could tell you more, but I am rather new to this Virtualization stuff.

Good Luck.

---

### Post by bunnyhugh on 2009-03-03
> **wildmanne39 said:**
> Hi everyone, Can some one please tell me how to fix vbox I upgraded my kernel and now I get an error that says I need to reset up my kernel can anyone tell me how to do that, please be exact as possible I am still learning. Thanks to everyone in advance, I really appreciate any help concerning this matter.

All you need to do is the following "sudo /etc/init.d/vboxdrv setup" and this should fix the issue. You can find out more here [http://download.virtualbox.org/virtualbox/2.1.4/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.4/UserManual.pdf)

Regards

---

### Post by wildmanne39 on 2009-03-03
Hi, thank you for your suggestion I really appreciate it.

---

### Post by wildmanne39 on 2009-03-03
Hi thank you it fixed my problem so quick and easy and cant believe it.

---


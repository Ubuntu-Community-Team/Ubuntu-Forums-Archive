---
title: "Ubuntu 14.04 server, BootitBM boot manager and VMWorkstation install issue"
date: 2016-03-12
forum: Virtualisation
---

### Post by gpsmikey on 2016-03-12
Greetings all - ran into an issue attempting to install Ubuntu 14.04 LTS server (64) on VMWorkstation 10 after installing Terabyte Unlimited's boot manager BootitBM.  Finally found one solution that I thought I would also post here in the hopes it helps someone else who runs into this issue.  Their KB article #279 "Linux Installation Notes: Ubuntu" covers what I was trying to do basically (although they start with the GUI version).  In the KB article, they indicate that at a minimum, you need 2 partitions for the Linux install - one for the root file system (Ext4) and one for swap.  I attempted to follow the instructions and the install went well up until it came to installing GRUB at which point the installer indicated it wanted to put it in the MBR (which would have overwritten my existing boot manager) - I selected "No" and then got the screen to choose where to install it.  I tried /dev/sda2 (which is where the root file system was) and the install failed.  Tried a number of variations, none worked.  If I let Ubuntu have the whole disk, I noticed that it created a separate /boot partition of about 600 megs.  After seeing another person comment about having a problem where a boot partition was not created, I decided to give that a try and created 3 partitions in addition to the 8 meg partition my boot manager was using.  A /boot partition, / , and swap.  Then tried the install again - this time when I got to where it wanted to install GRUB in the MBR and I selected "No" and selected the partition I had created as /boot (about 200 megs), GRUB was installed correctly and now all is well and I can boot Ubuntu from the boot manager as I wanted to do.  Since this requires doing things a bit different than what was documented in the KB article I thought I would provide the details here.  Hope it helps someone else.

mikey

---

### Post by MAFoElffen on 2016-03-15
Call me confused. If you were using BootIt Bare Metal as your primary boot manager (that is what you said), then why did you need to install Grub2? Did you intend on ... and was your goal to chain load multiple boot managers from each other?? Since it boots Windows and Linux, I'm wondering why you didn't just boot from it directly.

Meaing, you would have only needed to install grub2 if you didn't have any other boot manager at all... Therefore, my confusion.

---


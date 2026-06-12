---
title: "VM does not reboot after installing Ubuntu GNOME"
date: 2014-02-25
forum: Ubuntu Development Version
---

### Post by amjjawad on 2014-02-25
Hi,

This is Oracle Virtual Box version: 4.3.6
I tried to install Ubuntu GNOME Trusty Tahr i386 - 20140225 - [http://iso.qa.ubuntu.com/qatracker/milestones/312/builds](http://iso.qa.ubuntu.com/qatracker/milestones/312/builds)

After installing, the VM does not reboot. Yes, even if I press 'Enter', nothing happens.

[ATTACH=CONFIG]250666[/ATTACH]

I shut it down, start again and got black screen. Shut it down for the 2nd time and turn it on and it worked.

Anyone else having the same issue?

Thank you!

---

### Post by Doug S on 2014-02-26
Yes, on occasion I have had similar issues after a fresh install on a VM, and not just this 14.04 cycle, also the previous cycle. I don't use virtual box, I use kvm / qemu.

---

### Post by amjjawad on 2014-02-26
Hi and thanks for posting :)

> **Doug S said:**
> Yes, on occasion I have had similar issues after a fresh install on a VM, and not just this 14.04 cycle, also the previous cycle. I don't use virtual box, I use kvm / qemu.

Two different VMs on the same laptop and same version of Oracle VirtualBox, one is not rebooting after the installation is done and the other one is rebooting normally.

The one that does not reboot is i386 image.
The one that did reboot is amd64 image.

Testing Ubuntu GNOME Trusty Tahr 20140226

[ATTACH=CONFIG]250697[/ATTACH] 


It is hard to tell whether this is a VM related issue or the ISO itself.

This is not new issue by the way. And many users reported that with real hardware as well so I guess it is ISO related, I mean something wrong with the image itself but I can't tell what exactly.

---


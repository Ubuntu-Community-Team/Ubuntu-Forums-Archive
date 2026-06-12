---
title: "Help with UEFI install Windows 7 inside Virtualbox"
date: 2014-02-03
forum: Virtualisation
---

### Post by waterwheel2 on 2014-02-03
I'm new to ubunut, hoping someone is able to assist me with the required steps.  I've done a bunch of reading and at this point I'm just overwhelmed.

I have a new acer computer.  I burned win7 to recovery DVD's.  Then I installed Ubuntu, wiping out all the partitions.  Installed virtualbox.  Now when I install win7 (64bit) using virtualbox, I get a message saying I must have uefi turned on.  

My reading indicates that it's because I should have retrospectively installed ubuntu using efi.  Some further reading indicates that I can install a efi partiiton using boot-repair.  Tried that, I can 't get boot-repair to do much of anything without unmounting, and I can't seem to unmount partiions.

I guess I could reinstall ubuntu using efi, bot the instructions on that seem a bit nebulous and I would prefer to not reinstall ubuntu (got my email setup, scanner working etc).

What I'd like to do is (I think) repair my current Ubuntu install so that it has whatever's necessary for EFI, then continue the win7 installation process.  

Can anyone give me a shove in the right direction please or even better, babysit me through this :) ?

---

### Post by oldfred on 2014-02-03
Boot-Repair will not create partitions. It will repair an install and can convert a BIOS install to UEFI if you originally installed with gpt partitioning and have an efi partition.
Do not know about Virtual Box but post link to BootInfo report from Boot-Repair to see how you have installed.
It may just be what settings you have in UEFI/BIOS?

Windows 7 DVD normally default to BIOS installs. You have to convert to flash drive and add some things.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by bashiergui on 2014-02-03
Are you trying to install Windows 7 in a virtual machine using the recovery discs? That won't work. You need an installation disc. You could order one from the computer manufacturer (samsung, lenovo, whatever) for a fee. You can probably use the license key you have from the full disk install, but I'm no lawyer.

---

### Post by bashiergui on 2014-02-03
I'm a little confused by your (waterwheel2's) description. I don't think anything is wrong with the Ubuntu host installation. The problem is you're not using the right kind of installation disc to install Windows. 

Is that how you're reading this oldfred?

---

### Post by oldfred on 2014-02-03
I have never installed Windows 7, want to try vitual box but have not gotten around to it.

---


---
title: "VirtualBox Freezing Issues"
date: 2008-03-09
forum: Virtualisation
---

### Post by Theros123 on 2008-03-09
Okay...this is REALLY FRUSTRATING especially when it was working for hours beforehand.

So basically, I installed Virtualbox using the terminal/using apt-get.  That worked.  The problem comes whenever trying to run a Virtualized OS (XP in this case).  It worked before, and I had XP running with a bunch of other programs (like photoshop)...but now even with reinstalling XP, VirtualBox just freezes after 10 seconds...  The real only way to stop it is to do a hard reboot by holding down the power button.  I don't get this!?  It was working before, including the Seamless mode.  I also added the vbox user group, fixed the USB settings, etc.  And it worked before, so I can't find any reason to why it doesn't work now.

Anyone have any ideas?  And now, after like freezing for 5 minutes, Vbox will terminate the Virtual OS install and says it was Aborted...?

Thanks,
Eric Huang

---

### Post by Theros123 on 2008-03-09
bump?  Anyone?

---

### Post by PmDematagoda on 2008-03-09
This thread has been moved to the Virtualisation section.

---

### Post by Theros123 on 2008-03-09
That's weird... I just tried installing XP again with VMWare Server now...and the EXACT same freezing issued occurred when XP is formatting?  Maybe its my CD?  But, it worked earlier?

OMG...I just tried another XP cd and it failed in the EXACT same way.  It must be Ubuntu?  Man...I guess I'l have to reinstall it YET again.  Damn it.

---

### Post by fjgaude on 2008-03-09
Could it be that your hard drive is failing? Or even memory?

---

### Post by Theros123 on 2008-03-09
I hope not.  I reinstalled Ubuntu, and now its working though,

---

### Post by fjgaude on 2008-03-09
Well, you might do a fsck on the drive to see if anything comes up. Do this from a  LiveCD using Gparted in the System Adminestration menus.

Also run the memory test while you using the LiveCD.

---

### Post by pravinbravi on 2008-10-27
Try this

[http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround](http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround)

and also a reading of this should help

[http://forums.virtualbox.org/viewtopic.php?t=2521](http://forums.virtualbox.org/viewtopic.php?t=2521)

Turn off ACPI, a trade off.

---


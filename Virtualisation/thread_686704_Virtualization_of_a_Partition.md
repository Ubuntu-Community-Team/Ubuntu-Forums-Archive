---
title: "Virtualization of a Partition"
date: 2008-02-03
forum: Virtualisation
---

### Post by saxofoner on 2008-02-03
I'm trying to run my windows partition in VMWare or VirtualBox.  I have followed multiple tutorials today, and I have gotten both VMWare and Vbox up to the point where it tries to boot Windows XP.  However, rather than booting, windows says:
```
A disk read error occurred
Press Ctrl+Alt+Delete to restart 
```
Now, pressing ctrl alt delete at this point does nothing, and I can't blame the software since they both do it.

This is a Thinkpad T61P, with a SATA hard drive.  In the bios I can switch between AHCI and Compatibility modes.  Neither works.  

Does anybody have any ideas?  I'm willing to try anything.  Infact, I tried running "fixmbr" from the recovery console through the virtual machine off the xp install disk.  That rendered my windows partition(s) useless until I did it again from the actual xp machine, rather than VBox.  

So that was fail.  Halp plz.

---

### Post by GooblyWoobly on 2008-02-26
Also on the same boat. Please help.

---

### Post by bodhi.zazen on 2008-02-26
This is IMO in Beta and can cause significant problems / data loss so be careful.

See the sticky at the top of this forum.

---

### Post by ittayd on 2008-03-17
Same problems here. The sticky didn't help. I tried creating the disk by using some partitions, by using whole disk, by setting it as scsi and ide. Nothing helps. I always get a "disk read error".

I have thinkpad t61 with sata disk and windows xp sp2

---

### Post by saxofoner on 2008-05-15
So uh... no progress on anybody's part?

---

### Post by evets on 2008-05-16
Try this How To on VB's site.

[http://www.virtualbox.org/wiki/Migrate_Windows]("http://www.virtualbox.org/wiki/Migrate_Windows")

Please post back your successes or failures. Thanks

---

### Post by rrhoglund on 2008-05-20
Hi everyone..I have have t61p running hardy and windows xp.  I have also tried to get this to work and get the read disk error (with virtualbox and vmware).  I also tried modifying my hal.dll by using the following tutorial.

[http://www.vmware.com/support/gsx25/doc/disks_dual-boot_acpi_gsx.html](http://www.vmware.com/support/gsx25/doc/disks_dual-boot_acpi_gsx.html)

Same problem.  Any ideas?

---

### Post by Sand Lee on 2008-05-20
Have you tried this tutorial yet? [Boot an existing XP (Physical HD) install with VirtualBox ]("http://ubuntuforums.org/showthread.php?t=769883")
If it didn't work please let me know any errors you received.

---


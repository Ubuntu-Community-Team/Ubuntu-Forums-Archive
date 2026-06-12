---
title: "Scanning/mounting virtualbox vdi in Ubuntu?"
date: 2009-03-03
forum: Virtualisation
---

### Post by smilinggeek on 2009-03-03
This has probably been answered somewhere, but searching hasn't found it.

Is there a tool somewhere that allows antivirus running on Ubuntu 8.10 to scan a .vdi virtualbox disk from the outside? This would be instead of running the antivirus from inside the virtual machine, and would allow scanning while the virtual machine is shut down.

Is there some way, perhaps, to mount a .vdi as a local disk under Ubuntu, sort of like a disk image, without starting the virtual machine?

Running VirtualBox-OSE 2.0 under Ubuntu 8.10 with WinXPPro guest OS.

---

### Post by Zack McCool on 2009-03-03
No.  A Virtual Machine is just like a physical machine.  Er, only virtual.  

The OS has no access to the inside of that vdi file.  

Your best bet is to limit the VM's access to the internet.  If it is going to be connected, though, install AV on the guest.  An AV written for Windows is more likely to have current definitions, anyhow...

---

### Post by konqueror7 on 2009-03-03
you can try setting them up as a network, and share all the folders of your guest and scan those folders from your host...but it would be troublesome...:KS

---

### Post by samichx on 2009-03-12
No, VDI files can be mounted - they do not represent the machine they represent the disk used by the machine and as we all know disks can be mounted.

There used to be a nifty tool I used to mount weird files... I'll post it as soon as I remember what it is and get it to work with VDI.

I know this is a user forum and not a developer forum, but maybe if we kept the "We can do anything" attitude better things can be done.

EDIT:
Ok, so mounting is a it trickier because the filesystem is encased in what I'll call "VDI Padding" but long and complicated methods for mounting exist so check out these resources:

Przemoc Method(Fixed Size Only): 
[http://wiki.przemoc.net/tips/linux#mounting_partition_from_vdi_fixed-size_image](http://wiki.przemoc.net/tips/linux#mounting_partition_from_vdi_fixed-size_image)
Also Found Here:
[http://ubuntuforums.org/showthread.php?t=871367](http://ubuntuforums.org/showthread.php?t=871367)

If that's not good enough I invite others to ask Przemoc for permission to automate his system as either a nautilus script or application.

---


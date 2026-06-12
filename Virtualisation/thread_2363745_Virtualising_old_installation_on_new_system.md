---
title: "Virtualising old installation on new system"
date: 2017-06-14
forum: Virtualisation
---

### Post by dwlamb on 2017-06-14
Recently I acquired a new system that is powerful enough to support a 64-bit version of Kubuntu.  While I am almost complete in the transition of updating the install from a 32-bit machine, I still want to keep the old 32-bit install around in case I find something I need and want to migrate settings.

Is it feasible or advisable to create a virtual machine of the old 32-bit version?

My plan is
[LIST=1]
[*]Remove software and associated home files from the 32-bit machine as much as possible to reduce Gb's
[*]Create a Clonezilla image
[*]create a VirtualBox machine on the 64-bit system
[*]restore the Clonezilla image to the virtual machine
[*]Re-purpose or junk the 32-bit computer to get it off my desk
[/LIST]

Are there parts of a Linux install that are dependent on the hardware of an actual PC that may not be present on a VirtualBox?

Has anyone else tried this and have input to offer?

Thanks

---

### Post by deadflowr on 2017-06-14
Moved to* Virtualization*

---

### Post by TheFu on 2017-06-30
SATA/RAID drivers and GPU drivers need to be removed if they are specific to the old hardware.

Besides that, it should work.

---

### Post by lammert-nijhof on 2017-07-01
Your virtual machine definitions should be as close to your old HW as possible. Only use the standard Linux drivers and remove any propriety drivers. I would consider to take any video card out and try to move to the integrated graphics before cloning the machine.

---


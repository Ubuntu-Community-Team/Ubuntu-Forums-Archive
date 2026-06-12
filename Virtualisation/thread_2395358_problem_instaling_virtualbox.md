---
title: "problem instaling virtualbox"
date: 2018-06-30
forum: Virtualisation
---

### Post by mlloyd on 2018-06-30
I'm trying to install VirtualBox on Xubuntu 18.04, and have not yet been able to.

I'm using a terminal command:

sudo apt install virtualbox

It ran awhile and got to a point where it seemed to be creating a "secure boot key" and writing it to disk. It seemed to get stuck in the middle of that with a progress indicator saying 83%. It never got past that. I let it run for 10 hours and nothing more happened.

VBox was in the menu but it was not completely installed. I tried again and got:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

The output from that command:

```
Setting up virtualbox-dkms (5.2.10-dfsg-6) ...
Removing old virtualbox-5.2.10 DKMS files...

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.2.10
Kernel:  4.15.0-23-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 5.2.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-5.2.10 DKMS files...
Building for 4.15.0-23-generic
Building initial module for 4.15.0-23-generic
```

(nothing more happened, even after 8 hours)

On this machine, I am not able to install anything, of get updates. Any attempt gives the same result (above). Is there anything I can do to get VBox, or at least have the installer/updater usable?

---

### Post by deadflowr on 2018-06-30
Similar issue here:
[https://ubuntuforums.org/showthread.php?t=2393436]("https://ubuntuforums.org/showthread.php?t=2393436")

---


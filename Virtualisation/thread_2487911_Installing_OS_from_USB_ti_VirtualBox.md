---
title: "Installing OS from USB ti VirtualBox"
date: 2023-06-17
forum: Virtualisation
---

### Post by lwalper on 2023-06-17
Without an optical drive, how would one install an OS from a bootable USB stick to Virtualbox. It only lists floppy, CD/DVD, and HDD as bootable sources -- no USB.

---

### Post by sudodus on 2023-06-17
VirtualBox is smart enough to 'see' an iso file (a normal file in the host operating system) as a DVD disk, and you can install from it (and/or run a live session).

---

### Post by ajgreeny on 2023-06-18
As sudodus says, you do not need to do anything with the .iso file you presumably already have somewhere on disk; in the VBox manager window simply point to that .iso file and use it to install the VM.

---

### Post by lwalper on 2023-06-18
OK, so I am installing TrueNAS. The iso file is recognized and installs without any problem -- I suppose. Then, when prompted to remove the install medium and reboot -- there is no "install disk" to remove and the reboot process returns to the installer iso. No joy. So, shut down the VM, go to setup, remove the virtual optical disc, reboot, and the VM now tells me that there is no bootable medium and it doesn't look like the OS actually got installed. I've watched a few VM install OS vids which don't seem to mention this little issue.

---

### Post by ajgreeny on 2023-06-18
> **lwalper said:**
> OK, so I am installing TrueNAS. The iso file is recognized and installs without any problem -- I suppose. Then, when prompted to remove the install medium and reboot -- there is no "install disk" to remove and the reboot process returns to the installer iso. No joy. So, shut down the VM, go to setup, remove the virtual optical disc, reboot, and the VM now tells me that there is no bootable medium and it doesn't look like the OS actually got installed. I've watched a few VM install OS vids which don't seem to mention this little issue.
You say it installs without problem, but did you actually install it or just run it as a live system? 
It sounds as if that may be what you did but I don't know TrueNAS at all.

---

### Post by lwalper on 2023-06-18
Have now created a new VM and attempted install of Ubuntu. The initial install dialog pops up, but when attempting to install the OS it hangs and won't proceed with the install. The Ubuntu site recommends installing Virtualbox version 7, but the installed version from the repositories is v 6.1. I have uninstalled v 6.1. Since I have, in the past, been warned against downloading/installing software from sources other than the repositories for fear of entering dependency hell, I am hesitant to install v 7.

---

### Post by lwalper on 2023-06-18
> **ajgreeny said:**
> You say it installs without problem, but did you actually install it or just run it as a live system? 
It sounds as if that may be what you did but I don't know TrueNAS at all.

That's a good question?? I don't know. It's probably got nothing to do with TrueNAS because the VM just goes back to the install iso at reboot.

It's a new machine with no other software installed so I just deleted everything and did a fresh Ubuntu install, then Virtual box from the repositories with no new news and NO JOY. The VM fails to install any OS.

---

### Post by lwalper on 2023-06-18
Progress -- have started out with a fresh install of TrueNAS (without U buntu or Virtualbox) and it's working! Yay!! I guess this thread is finished.

---


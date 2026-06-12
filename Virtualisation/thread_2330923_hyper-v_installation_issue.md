---
title: "hyper-v installation issue"
date: 2016-07-16
forum: Virtualisation
---

### Post by kaleidosc0pe on 2016-07-16
Helloo!! i'm new to the forums, and have VERY LIMITED experience with Ubuntu.

Anyway, i attempted to install 16.04 on Hyper-V, and after the install goes through it just shows a screen that says something like "please remove installation media then press enter"
So i attempt to "remove the installation media" by changing some Hyper-V boot settings for the Ubuntu Machine, but when i hit enter nothing happens.

So then i turn off the VM and restart, and it asks me to provide the password to unlock the drive, but i cannot type into the machine.

That is where I am stuck. 

Thanks for help!!

---

### Post by deadflowr on 2016-07-16
Moved to ***Virtualisation***

---

### Post by MAFoElffen on 2016-07-17
On a physical machine, you would open the optical drive bay, remove the CD Disk and select the <Enter> key.

On a virtual, you just eject the iso, Select <Enter> and let the VM Guest reboot.

On you saying that after the VM goes through a reboot cycle that you can type anything in the VM Guest... You do realize that you have to click on the screen of the VM's desktop, for the desktop or console to get focus and start taking keyboard/mouse input right? Cause after it powers down, a VM Guest loses focus and returns control of user input (keyboard and mouse) to the host.

---


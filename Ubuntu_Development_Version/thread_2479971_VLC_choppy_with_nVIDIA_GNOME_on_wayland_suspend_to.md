---
title: "VLC choppy with nVIDIA GNOME on wayland suspend to RAM setting"
date: 2022-10-14
forum: Ubuntu Development Version
---

### Post by bert.ram.aerts on 2022-10-14
I have Ubuntu 22.10 x86_64 with nVIDIA driver 520.56.06 from the PPA for Canonical Kernel Team.
Gnome on Wayland works fine and VLC playback is OK.
But suspend to RAM does not work, unless I make the file
```
etc/modprobe.d$ cat nvidia-power-management.conf
options nvidia NVreg_PreserveVideoMemoryAllocations=1
```
After reboot in Gnome on Wayland and successful resume from suspend to RAM, VLC is choppy.
This is not specific for this New Feature Branch Version of nVIDIA but this was also the case in Ubuntu 22.04 with older driver.
Is there another way to get resume from suspend to RAM working?

---

### Post by bert.ram.aerts on 2022-10-16
I think I solved it by adding the temporary space
```
bert@legion5ubuntu:~$ cat /etc/modprobe.d/nvidia-power-management.conf 
# needed for Gnome on Wayland to correctly resume from suspend to RAM
options nvidia NVreg_PreserveVideoMemoryAllocations=1 NVreg_TemporaryFilePath=/var/tmp
```

---


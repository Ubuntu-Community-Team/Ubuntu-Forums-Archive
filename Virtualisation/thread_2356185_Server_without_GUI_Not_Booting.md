---
title: "Server without GUI Not Booting"
date: 2017-03-20
forum: Virtualisation
---

### Post by f0rgiven on 2017-03-20
Ubuntu 16.04 LTS as a hyper-v VM guest. The server VM did not get shutdown cleanly and now will not boot at all. After connecting to the VM using hyper-v manager and starting the ubuntu VM, the screen stays black. I have restarted the physical server and the VM multiple times. Is there a keystone to boot ubuntu server in safe mode or to see the console logs? Without 1 of these, not sure how to get this VM up and running. Secure boot is NOT enabled. Never see GRUB....

---

### Post by TheFu on 2017-03-20
Boot from alternate media, run fsck on each of the partitions (don't bother with swap).
Try to reboot.  If it doesn't work, report back here and I'll have more steps.  Please be exact on the results. EXACT.

---

### Post by f0rgiven on 2017-03-20
I booted from the boot-repair iso and that did not even boot. Yes, I made the iso the first boot device. So then I booted from the ubuntu installation media. Walked through recover a broken system and ran fsck /dev/sda2. Came back as clean. Sda2 is NOT the EFI partition or the swap partition.

---

### Post by TheFu on 2017-03-20
What about sda1 and sda3, 4, 5, 6, 7?

Anyway, seems that grub was corrupted.  Boot from alternate media, request to rescue the system, pick the correct / partition to mount as root. Then run **grub-install /dev/sda** followed by **update-grub**.

If you have UEFI, I don't know what you need to do or if those commands will work. No UEFI used here. Sorry.  There is an **Ubuntu UEFI** page somewhere that might help.

You can review the prior boot-log files from this shell too.

---

### Post by lisati on 2017-03-20
*Thread moved to **Virtualisation**.*

---

### Post by f0rgiven on 2017-03-21
Sda1 is the "system/EFI" partition. Sda2 is "/" install. Sda3 is swap. I assume grub is installed by default on the "/" partition? This is UEFI. Given it is UEFI, should I even attempt grub-install /dev/sda followed by update-grub?

---

### Post by TheFu on 2017-03-22
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) - but if you are running inside a VM, don't use UEFI. Use BIOS.  The good stuff about UEFI is related to real hardware, not virtual hardware.

---


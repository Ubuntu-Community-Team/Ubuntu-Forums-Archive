---
title: "Qemu issues with grub2 on a pendrive"
date: 2014-04-18
forum: Virtualisation
---

### Post by hadriman on 2014-04-18
I am having some issues while using qemu to test my bootable pendrive (used to boot various live isos) :

Qemu remembers my /boot/grub.cfg file between reboots of the vm (either by killing the window or shuting down the guest system) making the testing process quite inefficient as I have to reboot the host to try a modified grub configuration.

Here is the command I use to launch qemu : 
```
sudo qemu-system-x86_64 -enable-kvm -m 1212 -hda /dev/sdb
```

What should I do to get qemu to reload my grub.cfg file each time ?

---

### Post by hadriman on 2014-04-18
Turns out I found my answer : 
In order for qemu to work properly (meaning in this case using the newest config file), you have to unmount all partitions of the selected drive

---


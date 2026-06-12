---
title: "Change 20.04 kernel"
date: 2021-04-16
forum: Virtualisation
---

### Post by khagberg on 2021-04-16
I hope someone can help me here. 

I installed 20.04 in a kvm guest. I used the kvm kernel to do this thinking it was tweaked for kvm guests. It is not. I would like to convert the machine to use the generic kernel but am having problems. I tried iinstall the kernel and modules and then booting to the kernel but the system just reboots.

Thanks

---

### Post by ajgreeny on 2021-04-16
I was not even aware there was a KVM kernel; where did you find that and how do you install it?

Make sure you have the **linux-generic** package installed and that should pull in the most recent kernel package for you, currently 5.4.0-72.

What numbered version do you have installed? 
You should be able to see that from command ***ls /boot | grep vmlinuz***.

[COLOR="#FF0000"]EDIT[/COLOR]:
I was using ArcoLinux when I posted last time so had no way to search kernel availability in Ubuntu but have since booted to Ubuntu so I now where the KVM  version came from, therefore no need to answer that part of my post.

However the rest of it still stands; install linux-generic package along with the dependencies then remove any of the kernel-kvm packages that you currently have, perhaps easiest done using g synaptic where you can search for packages by name using search term kvm.

I currently run several of the Ubuntu family of OSs in KVM/QEMU, all using the standard kernels and generally find no problems at all with any of them, even the as yet unreleased 21.04.

---

### Post by khagberg on 2021-04-19
Images can be found here [https://cloud-images.ubuntu.com/focal/current/](https://cloud-images.ubuntu.com/focal/current/)


I installed the linux-generic but it doesnt boot to the new kernel. When i go into the grub menu and select the appropriate kernel it starts to boot then goes back to grub menu. I can boot into the generic kernel recovery mode. I then removed the kvm kernels and all related headers, images and modules. When i reboot it started to boot the generic kernel then reboot on its own. The second time it did boot.

Thanks

---

### Post by DuckHook on 2021-04-19
*Thread moved to **Virtualisation** as the more appropriate forum.*

---


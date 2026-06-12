---
title: "no cdrom access in virtual win98"
date: 2008-01-09
forum: Virtualisation
---

### Post by manchu99 on 2008-01-09
I'm running a virtualized win98 via qemu-kvm. installed win98 from cd of course but when i started it from the image on my hd after install, win98 will not read from my cdrom drive even when it is mounted in linux. When executing qemu-kvm, bash tells me /dev/kvm can't be found and kvm support will be disabled. when i try to install the kvm intel modules i get: "FATAL: Error inserting kvm_intel (/lib/modules/2.6.18.8.tex5/kernel/drivers/kvm/kvm-intel.ko.gz): Operation not supported" but after the OS install, i installed a piece of software on it from the cdrom drive. i exited the virtual machine and the next time i loaded it up.. no cdrom support.

---

### Post by manchu99 on 2008-01-09
well problem solved. appearently i can't run KVM as my bios won't support it. but it does run qemu.. what the difference is i don't know.. but appearently i have to specify the location of the cdrom drive when i boot qemu. win98 now loads and my cdrom reads cd's. thanks anyways

---

### Post by insane_alien on 2008-01-10
only certain processors have the instruction sets KVM uses. qemu doesn't require these but works slower when not using them.

---


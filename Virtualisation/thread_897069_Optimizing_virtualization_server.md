---
title: "Optimizing virtualization server"
date: 2008-08-21
forum: Virtualisation
---

### Post by thegnark on 2008-08-21
Hello,

I was wonder if there are any good tips/tutorials for optimizing a headless Ubuntu Server \that serves as a VirtualBox virtual server.

I've turned off AppArmor as recommended in several places. Is there anything else I could disable to help optimize things?

---

### Post by gtdaqua on 2008-08-22
For any kind of virtualization, tuning the kernel and the filesystem would help a lot.

The VMs can be stored in XFS filesystems if they are one single large file. Mount the VM filesystems with "noatime" option in the fstab file. This will eliminate non-productive writes to that file system.

You can try to minimize the use of swap there by maxing the performance -> try to optimize the /etc/sysctlf.conf and add these values at discretion:
```

vm.swappiness=0
vm.overcommit_memory=1
vm.dirty_background_ratio=5
vm.dirty_ratio=10
vm.dirty_expire_centisecs=1000
dev.rtc.max-user-freq=1024

```

Somekernel parameters also could help. Edit /boot/grub/menu.lst file and consider between "elevator=noop" or "elevator=deadline". I use elevator=deadline for Host OS and "elevator=noop" for Guest OS.

```

# kopt=root=/dev/hda2 ro **elevator=deadline**    
...
...
kernel          /boot/vmlinuz.....  ro **elevator=deadline**

```

Then read through the VM software's manual to see how you can tweak the VMs within.

---


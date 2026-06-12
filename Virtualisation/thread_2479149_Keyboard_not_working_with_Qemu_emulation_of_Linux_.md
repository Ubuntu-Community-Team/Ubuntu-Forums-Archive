---
title: "Keyboard not working with Qemu emulation of Linux 5.19.8 kernel?"
date: 2022-09-15
forum: Virtualisation
---

### Post by Watchintv on 2022-09-15
I have built a custom kernel (5.19.8) and have tried running it with Qemu. I am able to launch a busybox shell, however the keyboard is not working.

I thought I had done this in the past and did not need any additional parameters, but could be wrong.

The command I am running is:
qemu-system-x86_64 -kernel '../Downloads/linux-5.19.8/arch/x86_64/boot/bzImage' -initrd '../obj/initramfs-busybox-x86.cpio.gz' -m 512M -append "init=bin/sh"

Any advice?

---

### Post by MAFoElffen on 2022-09-20
My suggestion to try:
```

qemu-system-x86_64 -kernel  '../Downloads/linux-5.19.8/arch/x86_64/boot/bzImage' -initrd  '../obj/initramfs-busybox-x86.cpio.gz' -m 512M -append "init=bin/sh" -serial stdio -device usb-kdb

```

---


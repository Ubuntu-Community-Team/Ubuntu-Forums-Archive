---
title: "[SOLVED] How to copy kernel from one machine to another?"
date: 2008-06-14
forum: Server Platforms
---

### Post by SJI on 2008-06-14
Hello everyone,

I've been experimenting with different compilations on kernel on a machine here and I've arrived at a configuration that I find useful.

Compiling the kernel takes an age on the machine, so rather than having the source on another machine and having to recompile again for that machine is there a simple way to copy the new kernel configuration from one machine to another?

Many thanks,

Stephen

---

### Post by pdwerryhouse on 2008-06-15
Are you building the kernel as a .deb file? If so, just copy that .deb across to the new machine and then install it with dpkg.

If not, then you'll need to copy the following files:

/boot/vmlinuz-[version number]
/boot/initrd.img-[version number]

...and the entire directory tree under:

/lib/modules/[version-number]/

then you'll need to modify /boot/grub/menu.lst on the new server to boot the new kernel.

But I really recommend building your kernel as a deb file. Install the *kernel-package* package, and then use *make-kpkg* to build your kernels. Once you've tried this, you'll never go back to the old method for compiling kernels :)

---

### Post by SJI on 2008-07-18
> **pdwerryhouse said:**
> 
If not, then you'll need to copy the following files:

/boot/vmlinuz-[version number]
/boot/initrd.img-[version number]

...and the entire directory tree under:

/lib/modules/[version-number]/

That's what I was after.

> **pdwerryhouse said:**
> 
then you'll need to modify /boot/grub/menu.lst on the new server to boot the new kernel.

This machine doesn't utilise grub or any sort of boot menu, so no trouble there.

Many thanks

Stephen

---


---
title: "Correct instructions on adding a custom kernel"
date: 2024-04-12
forum: Ubuntu Dev Link Forum
---

### Post by anadon3 on 2024-04-12
I have some kernel debugging to start on for another piece of work.  Ubuntu as a distro as been fighting me on this.  I have the kernel configured and built.  I am at the step of building the initramfs and will need Ubuntu specific steps for inclusion into GRUB.

My primary requirement is that I must use a stock kernel branch.  I'll distro-hop to Arch tomorrow if need be, but I'd like to avoid that extra effort.

I have searched a few times and read over the following:

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
[https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide](https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide)
[https://wiki.ubuntu.com/Initramfs](https://wiki.ubuntu.com/Initramfs)
[https://wiki.archlinux.org/title/Kernel/Traditional_compilation](https://wiki.archlinux.org/title/Kernel/Traditional_compilation)

---

### Post by hyperlinxe on 2024-04-12
That is automatic when you use make install
(or even if you're trying to install it as a .deb package and let apt manage your kernel, the same is true.)

the initramfs is updated, and grub is updated, after the kernel is installed to /boot

It's actually so rare for distributions to modify how grub works that I can only think of one. For debian/ubuntu they have the special update-grub command that is a shorthand for grub2-mkconfig -o /boot/grub and for arch linux you can install that command from the aur, with yay -s update-grub or manually.

---


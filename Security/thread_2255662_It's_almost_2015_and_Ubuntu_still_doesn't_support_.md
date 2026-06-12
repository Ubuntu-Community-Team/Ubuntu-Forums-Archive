---
title: "It's almost 2015 and Ubuntu still doesn't support encrypted /boot"
date: 2014-12-06
forum: Security
---

### Post by fowlslegs2 on 2014-12-06
There is a widespread misconception that an encrypted boot partition is not a possibility in Linux (unless it is on a separate disk). GRUB has a module called cryptomount which makes this possible. The GRUB image is stored on your BIOS boot partition, while your kernels are safe from *meaningful* tampering.

So GRUB can open your encrypted /boot and pass control to your initramfs. The process of setting GRUB up to do this is very simple and distribution agnostic (see the instructions on editing /etc/default/grub and installing it here [http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/](http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/)). I have set this up for Ubuntu, but that has only put me half-way to booting from an encrypted /boot.

With Arch, which uses mkinitcpio, it's very easy to generate an initramfs image that correctly boots from a fully encrypted LVM over LUKS system (I'm personally using a 500M /boot and 20G / on an encrypted LVM partition). You simply add the hooks "lvm2" and "encrypt" to the "HOOKS" line of /etc/mkinitcpio.conf (order matters, but it's described on the Arch Wiki where to place them).

With mkinitramfs, I'm not quite sure what to do with this. My understanding is that hooks from /usr/share/initramfs-tools/hooks are automatically put in the initramfs image when `update-initramfs` is run. There I saw a cryptroot modules, that seems like it determines if your root is encrypted and then adds the necessary code to your initramfs if it is. A lot of the scripts were pretty lengthy there and I didn't put a particular lot of time reading them. I tried adding the modules dm_crypt, sha512, and aes to /etc/initramfs-tools/modules as is described in some of the Ubuntu documentation, then regenerating this file, but each time I boot the initramfs runs, but fails to ultimately boot the kernel.

If it is not clear, I know next to nothing about mkinitramfs. I was hoping a developer or a clever user might see this and be interested in figuring out how to add the right hooks/modules to boot the kernel. Since mkinitcpio has it figured out, we can copy from them if we don't already have the hooks/ tools necessary for doing so. You can check out the code here [https://projects.archlinux.org/mkinitcpio.git/tree/](https://projects.archlinux.org/mkinitcpio.git/tree/). Such a hook, if necessary, might also borrow from the existing cryptroot hook.

Without an encrypted boot, it's easy to replace your kernel with an identical one, except with, say, a keylogger bundled in. This is a huge security issue.

Arch supports encrypted boot. Windows does too. It's time for Ubuntu catch up.

---

### Post by TheFu on 2014-12-07
You lost me at:

> **fowlslegs2 said:**
> The GRUB image is stored on your BIOS boot partition.

Exactly what is this BIOS boot partition, of which you speak?
I don't have any EFI systems, BTW.

---

### Post by fowlslegs2 on 2014-12-07
[http://en.wikipedia.org/wiki/BIOS_boot_partition](http://en.wikipedia.org/wiki/BIOS_boot_partition)

I have a UEFI system which I boot in legacy mode. GRUB may support encrypted boot from UEFI, but I knew it worked for sure with legacy boot, so to save time not having to possibly repartition and reinstall I just chose to run it that way.

---


---
title: "Zorin grub-boot issues on system with UEFI32 / ATOM-64"
date: 2024-07-28
forum: Ubuntu/Debian BASED
---

### Post by verkurkie on 2024-07-28
Hi all - I apologize up front for yet another "nvram locked" post 8-[
Even after a lot of searching, reading, and trying over and over again, I am stuck with my little device that *will* let me install Linux but *won't* let me boot into it :(

here's a link to one of my many boot-repair attempts: [https://paste.ubuntu.com/p/jNCyDzGgnG/](https://paste.ubuntu.com/p/jNCyDzGgnG/)

I have tried so many things and feel like I'm ever so close! Here's where I'm at right now:
- encountered the dreaded "nvram locked" messages during and after installation (not just Zorin but LM, Feren and others all end up with the same issue)
- my device boots into the `grub>` prompt
- followed this post: [https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux:](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux:)
  - i can boot into my Zorin installation following the "Booting from grub>" steps
  - after booting, i can run `update-grub` successfully in a terminal (as root)
  - i can't run `grub-install /dev/mmcblk1` successfully -> the error is related to there not being a "i386-efi" folder
  - tried `grub-install` with `--no-nvram`, `--target=i386-pc`, etc. but no luck...

info:
- system has a 32-bit UEFI (Secure Boot=disabled) with 64-bit Intel Atom and a 32GB eMMC "disk" (it's a PIPO X8 Android/Windows dual-boot tablet device)
- created a GPT partition table with a 300MB, fat32 partition with boot and esp flags, the remainder is ext4 Linux filesystem

Hoping that the experts here can help me!

-thanks

---

### Post by oldfred on 2024-07-28
Not sure if Boot-Repair, grub or modprobe are wrong. This is not where efivars is:
> modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-35-generic

Boot-Repair or a chroot needs this:
mount -t efivarfs efivarfs /sys/firmware/efi/efivars
then mount shows:
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)

A few systems have UEFI settings that prevent changes. Check that also.

You only show Zorin, not Ubuntu?
Do not know that distribution.

You only have 64 bit UEFI boot files in ESP. But I do not think you would even get grub? if 32 bit?
The 32 bit UEFI boot file is bootia32.efi  which you do not show.

---

### Post by verkurkie on 2024-07-29
@oldfred - thanks for the response!
> A few systems have UEFI settings that prevent changes. Check that also.
I'm not sure how/where I can check that ... the firmware/BIOS screen is not very helpful when it comes to explaining the settings...
> You only show Zorin, not Ubuntu?
Yes, this particular boot-repair was done after an attempt to install [Zorin OS]("https://zorin.com/os/") v17 which is based on Ubuntu 22.04 LTS - note: I run into the *exact* same issues with Linux Mint and Feren OS which I believe are also Ubuntu based. Guess I could try Ubuntu itself... :-k
> You only have 64 bit UEFI boot files in ESP. But I do not think you would even get grub? if 32 bit?
The 32 bit UEFI boot file is bootia32.efi  which you do not show.

When I boot into Live CD, I get the grub menu and i can press 'c' to go to the "grub>" prompt - from there i can boot into Zorin OS (using "linux (hd1,2)/boot/vmlinuz-..." and "initrd (hd1,2)/boot/initrd-..." and "boot" commands) but I'm not sure if that means anything

I do think that the problem is related to the 32-bit UEFI boot files and getting installed properly...

Since my post, I have tried the suggestion from this post: [https://forums.linuxmint.com/viewtopic.php?p=1065977#p1065977](https://forums.linuxmint.com/viewtopic.php?p=1065977#p1065977) but i get stuck on "[COLOR=#333333][FONT=&amp]install grub-efi-ia32 with the synaptic package manager" because synaptic package manager tells me that "grub-efi-ia32" is broken ...

Just hoping that I'm missing something simple somewhere ... just don't know what it could be - i.e. uninstalling something first? some kinda setting in the BIOS?

/thanks again![/FONT][/COLOR]

---

### Post by oldfred on 2024-07-29
Moved to Other OS since not Official flavor of Ubuntu.

Some that do not get Boot-Repair to work do a full chroot.
But if locked NVRAM issue also mount efivars as shown above. Examples below do not show that extra mount command.

UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---


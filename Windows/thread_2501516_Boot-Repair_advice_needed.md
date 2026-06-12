---
title: "Boot-Repair advice needed"
date: 2024-10-11
forum: Windows
---

### Post by keylimejunkie on 2024-10-11
Hello

I hope a kind stranger can help me get to the position where I once again can choose Windows 10 or Linux when switching on.

This is how I got myself in a pickle:


[LIST]
[*]had a Win10 machine
[*]installed Debian as a dual boot (with its GRUB loader), then decided I didn't like it
[*]researched how to replace the Linux partitions with Ubuntu
[*]created an Ubuntu 24.10 USB stick to boot from
[*]followed instructions about manually deleting the Debian partitions then installing Ubuntu to new space
[/LIST]

However, the Ubuntu installation failed. Restarting takes me to the GRUB Rescue screen, where all the remaining partitions are described as '[FONT=courier new]unknown filesystem[/FONT]'

I therefore came to [Ubuntu's community boot-repair]("https://help.ubuntu.com/community/Boot-Repair") feature, was able to install it from my live USB stick, and got the output that is now copied to Ubuntu Pastebin:
[INDENT]

[/INDENT]
[INDENT][https://paste.ubuntu.com/p/czY7hVkKF5/](https://paste.ubuntu.com/p/czY7hVkKF5/)
[/INDENT]


What should my next steps be?
TIA.

---

### Post by tea for one on 2024-10-11
You have Windows 10 installed in old-fashioned legacy mode.
Do you know if your PC is UEFI compatible?

---

### Post by keylimejunkie on 2024-10-11
Afraid I don’t know.

Suspect not, as it’s an old Panasonic CF-19 that I only got Win10 functional on by maxing out the RAM & installing an SSD.

---

### Post by tea for one on 2024-10-12
As you do not have Ubuntu installed, boot-repair will not be any use at the moment.
First of all, I suggest that you have a look for Windows tools to try and repair the legacy Windows boot manager.
Then, if successful, start a new thread to install a suitable flavour of the Ubuntu family as dual boot.
Or, perhaps consider an Ubuntu version instead of Windows?

---

### Post by oldfred on 2024-10-12
Boot-Repair can fix your BIOS Windows boot. One of the very few Windows fixes it can do. It installs the syslinux boot loader that works like Windows boot loader. If you want Windows boot loader, you need Windows repairs.
You have grub installed to MBR of your drive and with only one MBR, only one system can boot.

Grub then can boot working Windows that is not hibernated nor needs chkdsk with a full install, but not just the part of grub in MBR. But if Windows has issues, you have to temporarily restore a Windows boot loader to MBR, boot Windows & make fixes, then restore grub to dual boot. Best to always have Windows repair/recovery flash drive & Ubuntu live installer to make fixes.

Since older system, Ubuntu may be too much system. It really now is for newer systems with more RAM, faster drives and newer hardware in general.
I could not get Ubuntu to install to my old 2006 Core-duo Intel based system. Server & lightweight gui did work. But when I tried Kubuntu it also worked which surprised me as it is more of a mid-weight flavor.

You probably need a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by tea for one on 2024-10-12
> **oldfred said:**
> Boot-Repair can fix your BIOS Windows boot. One of the very few Windows fixes it can do. It installs the syslinux boot loader that works like Windows boot loader.
Hello oldfred
I didn't realise that boot-repair could fix old style Windows legacy single OS boot.
Hopefully, I haven't unintentionally misled keylimejunkie too much................?

---


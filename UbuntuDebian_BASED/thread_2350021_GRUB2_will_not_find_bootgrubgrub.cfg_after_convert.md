---
title: "GRUB2 will not find /boot/grub/grub.cfg after converting to UEFI and GPT"
date: 2017-01-20
forum: Ubuntu/Debian BASED
---

### Post by bdw on 2017-01-20
I recently built a new system and used Clonezilla to clone my hard drives over from the old hard drives to the new ones.  Both hard drives are 1TB.  /dev/sda has Windows 10 and /dev/sdb has Ubuntu (actually Neon).    I converted both hard drives to GPT from MBR after [reading this tutorial]("http://www.rojtberg.net/1032/converting-a-ubuntu-and-windows-dual-boot-installation-to-uefi/").  I was able to create a UEFI partition on /dev/sda1 and installed the Windows 10 boot manager courtesy of [this article]("http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx") from Microsoft Technet.  The Windows boot manager works just fine and will boot Windows 10.

I reinstalled GRUB 2 it copied the needed files to the UEFI partition on /boot/efi mounted on /dev/sda1.  However, when I booted I got the GRUB command line because GRUB cannot find grub.cfg.  I ran the following command:

```
grub> search -f /boot
```

The result:

```
(HD3,GPT1)
```

The GRUB configuration file seems to set the root to (HD1,GPT1) but not (HD3,GPT1).  I'm able to boot Ubuntu/Neon manually by using the following commands:

```
set prefix=(hd3,gpt1)/boot/grub
set root=(hd3,gpt1)
linux /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot
```

Ubuntu/Neon then boots and starts up normally.  I ran "update-grub" and rebooted.  I still got the GRUB command line.  Purging and reinstalling GRUB2 did not resolve the issue.  I then booted into Boot-Repair to see if it would correct the boot issue.  It did not.

I've attached the boot-repair diagnostic output which is in a ZIP archive: [ATTACH]273285[/ATTACH].

I'm at a loss as how to configure GRUB2 to boot linux from (HD3,GPT1).  What did I miss?  I've been searching the forums and via Google for a solution but I've not found a working solution.

Many thanks,
Brian

---

### Post by oldfred on 2017-01-20
Moved to Debian Based since Neon.

There is a small 3 line grub.cfg in /EFI/ubuntu or you neon in the ESP.
That has to refer to the UUID & partition where the full grub.cfg is.

The other option is to use Boot-Repair and just do a full uninstall/reinstall of all of grub which then sets up correctly.

It is three lines in Ubuntu but can be just one, but that does not use UUID, so if device changes then it will not work.

 In efi partition's folder /EFI/ubuntu add another grub config to tell UEFI where to find grub.cfg with just this one line
configfile (hd0,gpt7)/boot/grub/grub.cfg 

Standard configfile grub.cfg
   search.fs_uuid Your-uuid-here root hd0,gpt8
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

---


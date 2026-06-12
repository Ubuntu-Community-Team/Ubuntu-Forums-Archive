---
title: "Installing on a SATA rive when unsupported by BIOS"
date: 2008-06-11
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-06-11
Sorry for clogging up the forums with the same issue but I seem to have be getting a lot of conflicting info.

Basically my BIOS wont boot from SATA drive which us pkugged into a PCI controller.

It's detected once something more advanced as a BIOS ( i.e. an os / installer ). 

Here's the solutions I've narrowed it down to:

- Install all partitions on Ubuntu but /boot on IDE drive. 
When doing this I receive this error:

```
An error was returned while trying to install the kernel into the target system.

Kernel Package: 'linux server'.

Check /var/log/syslog or see virtual console 4 for details.
```

- Using a super grub disc

- Installing all to SATA drive, boot to live cd and issuing command to install Grub to MBR of IDE drive.

I really don't know what to do and have been on this for days. It's gotta be possible, common sense tells me that someone with the skills could write a program that boots then points to the SATA drive and boots that kernel. Although I guess in effect this is just a bootloader. 
Whenever I try and make a dedicated /boot partition the installer fails as above.
Any ideas on what to do about this please? 

Thanks a lot in advance,
Gareth

edit: heres my previous posts on this subject [here]("http://ubuntuforums.org/showthread.php?t=824017") and [here]("http://ubuntuforums.org/showthread.php?t=824800")

---

### Post by garethsimpsonuk on 2008-06-11
bump

---

### Post by garethsimpsonuk on 2008-06-11
Ok here's my menu.lst and my fdisk -l. I've edited the default kernel from hd to sd

o.k. I tried to save and it wouldn't save 'didn't have appropiate permissions' so I gksudo nautilus and when I go to the grub there's only one file 'device.map'. All the menu.lst etc. have gone.

can anyone help me with this?

---

### Post by garethsimpsonuk on 2008-06-11
ok im prepared to pay someone to fix this cos it's been days and days of my free time since I started on this and I haven't managed to sort it

---

### Post by ginjabunny on 2008-06-11
I would have thought that if the bios won't boot from a disk on a pci sata card then you will have to put the /boot on a drive that it will boot from, so you could try putting an ide drive in and when you install then setup /boot on the ide drive and all the other partitions on the sata, I don't know if it will work but it sounds like it should.

Maybe booting from a floppy/cd/usb would work but I don't know how you would create one, I vaguely remember an early version of Mandrake or Redhat used to let you create a bootable floppy but that was in the days before sata.

---

### Post by garethsimpsonuk on 2008-06-11
yea thats what I'm trying to do but when I install just the boot on the IDE I get an error about not being able to install to the SATA. when I boot a live CD I got to menu.lst and it's pointing to HD1, I tried editing it to point to SD1 ( the root partition ) and it wont let me save. When I try gksudo nautilus and browse to the grub folder in boot, it only has 1 file in. the rest have disappeared! i'm really stumped. If there's anyone in SW england I will give them an athlon xp2000+ box that goes for 30 / 40 quid on ebay to fix this for me. Thanks

---

### Post by ginjabunny on 2008-06-12
So can you install a complete system with just the IDE drive? 
If so then disconnect it and install just to the SATA.
If you then plug back in the IDE can you boot from that then edit the /boot files to try and get it to point to the SATA?

If that doesn't work I'd give up, I sounds like it should work but for some reason it won't, a couple of things you could try.

1) bios update
2) smart boot manager, [http://sourceforge.net/projects/btmgr](http://sourceforge.net/projects/btmgr) (but not sure if it detects disks on cards) or similar
3) wingrub (but may require windows)
4) last resort - get another mobo

not much help really

---


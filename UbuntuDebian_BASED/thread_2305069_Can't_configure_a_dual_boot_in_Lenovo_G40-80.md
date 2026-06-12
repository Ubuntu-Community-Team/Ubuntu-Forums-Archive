---
title: "Can't configure a dual boot in Lenovo G40-80"
date: 2015-12-02
forum: Ubuntu/Debian BASED
---

### Post by Squiter on 2015-12-02
Hey guys I'm trying to make a dual boot in my lenovo, but I can't make grub works at all!

I already tried to use boot-repair three times with  no success, all the times the grub start with a simple grub bash (GNU GRUB version 2.02-beta2-9). I already enter in windows and change the Window bootloader using the `bcedit /set {bootmgr} path \EFI\grub\shimx64.efi` but don't work too.

Someone can help me?

This is the output of my boot-repair: [URL="http://paste2.org/BI0yJts1"]http://paste2.org/BI0yJts1
[/URL]

---

### Post by oldfred on 2015-12-02
Moved to other Ubuntu/Debian, since Elementary.
Not sure what differences Elementary has compared to Elementary.
It looks like your standard UEFI entry is /EFI/grub where in Ubuntu it is /EFI/ubuntu.

Script at top does not show any boot files in sda2, but later does show mount and list of files. Not sure if an issue or not mounting it.

You have in original efibootmgr list, two Windows UEFI boot entries. One the real Windows efi file and the other shim or secure boot grub version. Two entries with same description may be an issue.
Many vendors now have modified UEFI to use description as part of boot and only valid description is Windows. That is specifically not allowed in UEFI spec. But there are many work arounds. 
The BCDedit is one of the work arounds and often works as it is a one time reboot from Windows. UEFI does have a one time reboot and them must not for most system check description.

The other main work around is the UEFI default drive boot which requires /EFI/Boot/bootx64.efi. Often the bootx64.efi is just a copy of Windows bootmgfw.efi, but we can make it a copy of shimx64.efi and then a hard drive UEFI entry or fallback entry works to boot.

I would remove the duplicate Windows entry just to avoid confusion. It may work if you select it from one time boot key like f10 or f12, check manual. You can test if it works before deleting if desired.

       Check entry is there.
sudo efibootmgr -v 

   Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

Script shows 0000 as Windows with bootmgfw.efi or correct Windows. And 0003 as Windows using shimx64.efi. It used to be a work around to rename shim to bootmgfw.efi, and it would work for a short time or until Windows did an update. Or grub updated and verison of shim was wrong. So that option is not recommended any more.

More details on work arounds in link in my signature.

      
 Lenovo rename files
[URL="http://ubuntuforums.org/showthread.php?t=2302170"]http://ubuntuforums.org/showthread.php?t=2302170
[/URL]
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

[URL="http://ubuntuforums.org/showthread.php?t=2302170"]
[/URL]

---

### Post by Squiter on 2015-12-02
Oh man, sorry for post this in wrong place.

Sorry but I don't understand very well what I need to do.

First I need to delete te duplicated entry right? But what is the one to delete?! 0000 or 0003?
And after that, what is the second step?

And thanks for all the links, I'll start to read then now! :)

---

### Post by Squiter on 2015-12-02
Just for let the problem more detailed let me explain some things.

Runnig ```
sudo efibootmgr -v
``` I get this:

```
elementary@elementary:~$ sudo efibootmgr -vBootCurrent: 0005
Timeout: 0 seconds
BootOrder: 2001,0006,0000,0003,2003,0004,2002
Boot0000* Windows Boot Manager    HD(2,1f4800,82000,ebd793d8-bde3-4fc6-9893-9f07725a6f25)File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* EFI Network 0 for IPv4 (64-1C-67-78-47-87)     ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(641c67784787,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0002* EFI Network 0 for IPv6 (64-1C-67-78-47-87)     ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(641c67784787,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0003* Windows Boot Manager    HD(2,1f4800,82000,ebd793d8-bde3-4fc6-9893-9f07725a6f25)File(\EFI\grub\shimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...jF...............
Boot0004* Lenovo Recovery System    HD(3,276800,1f4000,28231963-7ae5-48a4-84e2-e66158411df3)File(\EFI\Microsoft\Boot\LrsBootMgr.efi)RC
Boot0005* EFI USB Device (SanDisk Cruzer Blade)    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,20,ee8be0,00000000)RC
Boot0006* grub    HD(2,1f4800,82000,ebd793d8-bde3-4fc6-9893-9f07725a6f25)File(\EFI\grub\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

```

I can set my primary boot in my BIOS cofiguration, when I set grub (0006) or the Windows (0003) I get the same problem, the grub shows me a bash.

When I choose Windows at 0000 I get the windows initialization.

So, I think the problem is with GRUB, that perhaps was not installed corretly? I do not know.

---


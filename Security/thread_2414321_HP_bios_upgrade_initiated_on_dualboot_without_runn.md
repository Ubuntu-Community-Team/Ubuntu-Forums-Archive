---
title: "HP bios upgrade initiated on dualboot without running Windows"
date: 2019-03-08
forum: Security
---

### Post by Bartje on 2019-03-08
I've got a weird, scary situation where my laptop, HP Pavilion started a bios upgrade after a reboot from ubuntu, after which the grub boot-loader had become overruled by the windows boot loader, hence making Ubuntu unreachable. Luckily I found an easy way to get back to grub. But this scenario does make it unreliable. 

Why do I post it here in 'security', well, because as far as I know, HP-support, which probably started the bios upgrade, is a Windows tool which obviously is not installed on Ubuntu, which in turn should not be able to initiate a bios-update when windows is not running. 

It is a dual-boot, win 10 and ubuntu, so my question is, is there some background windows process going on while running ubuntu? How can I disable the automatic bios updates if it's not triggered by HP-Support? 
I'm a musician, want to use my laptop in live shows, but when unexpectedly a bios update starts when booting up, and my ubuntu becomes unreachable, it's of not much use. On top of that it is in my opinion a security issue, because I, or the operating system are clearly not in control of the machine when this happens.

thanks,
Bart

---

### Post by oldfred on 2019-03-08
Linux is starting to support UEFI updates.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
But it only shows a few HP systems, so far.

HP  typically has a lot of .efi boot files in the ESP - efi system partition. But not sure what would trigger a UEFI/BIOS update.
I would think you have to start the update from within UEFI.

Do you still have /EFI/Microsoft folder in ESP? And would system somehow default to that before starting grub?
Post this:
sudo efibootmgr -v

Some have posted that using efibootmgr (which grub uses) to reset boot order, does not stick with HP. But if UEFI is updated, then changing order in UEFI does stick and Ubuntu can be default.

---

### Post by Frogs Hair on 2019-03-08
If your HP device is still within the factory support period there will be driver updates of various kinds until that ends. You may have something like the HP support assistant on your system which checks for software from HP.

---

### Post by Bartje on 2019-03-18
Sorry for the late reply, another PC has issues, trying to fix that one too now between my several jobs :-/ . 

In the mean time I had a 'mokmanager not found' issue after installing the nvidia proprietary drivers. I want to use my HDMI port (still doesn't work, and before the summer the nvidia card caused a black screen after login, so I was forced to only use the intel graphics, but those are different issues, nvidia now works, but still no HDMI)  
I got the mokmanager solved after running the onboard HP "system check"-system. After checking (no changes were made) it switched to the windows boot manager again.
This time I had to change the efi boot order in the BIOS settings.

Here is the output of efibootmgr -v:
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,3001,0000,2001,2002,2004
Boot0000* Windows Boot Manager	HD(1,GPT,41877807-eeac-4f2d-833b-2f2f204f7447,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* ubuntu	HD(1,GPT,41877807-eeac-4f2d-833b-2f2f204f7447,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0002* Windows Boot Manager	HD(1,GPT,41877807-eeac-4f2d-833b-2f2f204f7447,0x800,0x82000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3001* Internal Hard Disk or Solid State Disk	RC

Reading this there seem to be two windows boot managers... :-|

grtz,
Bart

---

### Post by oldfred on 2019-03-18
One of your Windows entries is really Windows using bootmgfw.efi and the other is using grubx64.efi.

      ```
 Boot0000* Windows Boot Manager HD(1,GPT,41877807-eeac-4f2d-833b-2f2f204f7447,0x800,0x82000)/File(\EFI\Microsoft\Boot\[COLOR=#ff0000]bootmgfw.efi[/COLOR])RC 

   Boot0002* Windows Boot Manager HD(1,GPT,41877807-eeac-4f2d-833b-2f2f204f7447,0x800,0x82000)/File(\EFI\ubuntu\[COLOR=#ff0000]grubx64.ef[/COLOR]i)WINDOWS.........x...B .C.D.O.B.J.E.C.T.=.{ 


```

Years ago one of the work arounds for HP was to use grub or shim with Windows description. HP internally has UEFI use description as part of UEFI boot and only valid description is "Windows Boot Manager". But Windows update usually overwrote that entry. We then found the hard drive entry worked, so stopped creating the Windows description one.

Many with HP and UEFI update, say it works so HP may have removed that description limit. It was a violation of UEFI spec that says not to use description as part of boot. They also say that using efibootmgr to change boot order does not seem to work, but using HP's UEFI will let you change boot order.

See
man efibootmgr

You can delete the old Windows entry using grub.
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

---


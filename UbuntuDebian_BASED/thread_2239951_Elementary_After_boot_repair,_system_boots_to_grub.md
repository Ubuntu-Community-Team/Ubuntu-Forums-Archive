---
title: "Elementary: After boot repair, system boots to grub terminal"
date: 2014-08-16
forum: Ubuntu/Debian BASED
---

### Post by gabrielgonc on 2014-08-16
Hello. 


I tried installing Elementary OS along with win8 on a Toshiba Satellite L850D-12Q notebook. I turned off secure boot and fast boot, and then installed the system. It then started booting directly to Elementary, no grub, no nothing, so I ran boot repair, and it started booting directly to grub terminal. I am relatively used to linux, but I have no clue what to do with it. :p

my bootinfo url:
[[COLOR=#1155cc][FONT=Arial]_[http://paste2.org/hDCwXJa6](http://paste2.org/hDCwXJa6)_[/FONT][/COLOR]]("http://paste2.org/hDCwXJa6")

Can someone help me, please?

---

### Post by yancek on 2014-08-16
You are using GPT/UEFI partitioning and appear to have the correct files on the EFI partition.  Interesting that it shows the Lilo bootloader in the master boot record as I don't believe Ubuntu has ever used it.  What exactly do you see when you boot, blinking cursor, prompt?

---

### Post by LostFarmer on 2014-08-16
from your bootrepair line 1115:> Boot0003* elementary    HD(2,e1800,82000,db56feb1-f82d-11e1-8394-8124b7db5fc3)File(**EFIelementaryshimx64.efi**)

Boot0004* Windows Boot Manager    HD(2,e1800,82000,db56feb1-f82d-11e1-8394-8124b7db5fc3)File(**EFIMicrosoftBootbootmgfw.efi)WINDOWS**
The entries list are not correct.

Boot into your live cd/usb linux in EFI mode.  in a terminal run " sudo efibootmgr -v" , if what is displayed is the same that is in bold above run below commands. Should look (/EFI/elementry/shimx64.efi), notice the '**/'**.

```
sudo efibootmgr -c -d /dev/sda -p 2 -w -L elementary -l /EFI/elementary/shimx64.efi
sudo efibootmgr -c -d /dev/sda -p 2 -w -L Windows Boot Manager -l /EFI/Microsoft/Boot/bootmgfw.efi 
```

You can run "efibootmgr -?" to see just what the command options are doing.

---

### Post by oldfred on 2014-08-16
But Boot-Repair ran the 'buggy' UEFI fix, which may cause issues. It was the first work around and originally the only one, but now other work arounds seem to be better.

This is the real Windows boot file, but with the configuration you have, you can only get to it from grub menu. Standard UEFI entry to Windows really is a grub or shim file.
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

The rename is required for those vendors that violate UEFI standard and modify it to only boot Windows. Sony & HP maybe others.
If you can directly boot Linux from UEFI menu you do not need any of the work arounds. Usually Toshiba's have worked but maybe Microsoft gave them a bigger discount if the corrupt UEFI and only boot Windows.

---

### Post by gabrielgonc on 2014-08-17
> **yancek said:**
> You are using GPT/UEFI partitioning and appear to have the correct files on the EFI partition.  Interesting that it shows the Lilo bootloader in the master boot record as I don't believe Ubuntu has ever used it.  What exactly do you see when you boot, blinking cursor, prompt?
I see a screen that says:Minimal bash-like line editing is supported. [I]
grub[/I]> *blinking cursor*
> **LostFarmer said:**
> from your bootrepair line 1115:
The entries list are not correct.

Boot into your live cd/usb linux in EFI mode.  in a terminal run " sudo  efibootmgr -v" , if what is displayed is the same that is in bold above  run below commands. Should look (/EFI/elementry/shimx64.efi), notice the  '**/'**.

```
sudo efibootmgr -c -d /dev/sda -p 2 -w -L elementary -l /EFI/elementary/shimx64.efi
sudo efibootmgr -c -d /dev/sda -p 2 -w -L Windows Boot Manager -l /EFI/Microsoft/Boot/bootmgfw.efi 
```

You can run "efibootmgr -?" to see just what the command options are doing.

In fact, I tried to put lilo on a prior attempt to fix the problem. :/
> **oldfred said:**
> But Boot-Repair ran the 'buggy' UEFI fix, which may cause issues. It was the first work around and originally the only one, but now other work arounds seem to be better.

This is the real Windows boot file, but with the configuration you have, you can only get to it from grub menu. Standard UEFI entry to Windows really is a grub or shim file.
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

The rename is required for those vendors that violate UEFI standard and modify it to only boot Windows. Sony & HP maybe others.
If you can directly boot Linux from UEFI menu you do not need any of the work arounds. Usually Toshiba's have worked but maybe Microsoft gave them a bigger discount if the corrupt UEFI and only boot Windows.I'll try that now, thanks a lot. :)
BRB with the results.

EDIT: retried boot repair checking the "Restore EFI backups" box, and clicked no for "WinEFI detected, do you want to backup and rename the files?" (in my first attempt, yesterday, I had clicked yes). Now I can boot windows again (but only if go to boot options by pressing f12 when turning on the notebook), but no success with grub.

I'll retry now answering yes to "WinEFI detected, do you want to backup and rename the files?".

---

### Post by LostFarmer on 2014-08-17
Boot hdd and select linux, at the grub prompt, type in "   configfile  (hd0,gpt6)/boot/grub/grub.cfg    "  press enter,  does it boot into linux ? if not , do you get the grub menu ?

---

### Post by gabrielgonc on 2014-08-17
> **LostFarmer said:**
> Boot hdd and select linux, at the grub prompt, type in "   configfile  (hd0,gpt6)/boot/grub/grub.cfg    "  press enter,  does it boot into linux ? if not , do you get the grub menu ?
I get: 
error: file name required

EDIT: Reinstalled elementary. now it boots straight into Elementary, no grub. To boot windows I still have to go to boot options. :/
I'm afraid to run boot-repair and ruin it again, but I must make grub work because it's my fiancée's computer, I'm using it for a college class.

---

### Post by sotiris2 on 2014-08-17
why not simply 
```
sudo update-grub
```Does this not work?

---

### Post by gabrielgonc on 2014-08-17
> **sotiris2 said:**
> why not simply 
```
sudo update-grub
```Does this not work?

nope. :/

EDIT:
went to bios, set boot from UEFI to CSM, and it stopped booting. went then back to UEFI and now it is the opposite of before: now it boots straight to windows, and I can't boot elementary at all, not even in the boot options. :/

---

### Post by sotiris2 on 2014-08-17
Don't change that. Changing from Uefi to bios (which is what csm is an allegory for) is certain to stop uefi OSes from booting. Wish I had a multiboot uefi system but mine is purely Ubuntu and my dualbox is Bios.

---

### Post by gabrielgonc on 2014-08-17
> **sotiris2 said:**
> Don't change that. Changing from Uefi to bios (which is what csm is an allegory for) is certain to stop uefi OSes from booting. Wish I had a multiboot uefi system but mine is purely Ubuntu and my dualbox is Bios.

I ended up noticing the bad idea... hehehe... gonna try boot repair once again, now that it is booting only windows. Should I select yes for "WinEFI detected, do you want to backup and rename the files?" again?

---

### Post by oldfred on 2014-08-17
Moved to Other OS since Elementary.

When you reinstalled did you reinstall in UEFI mode? Otherwise stay with UEFI. The two modes are not really compatible and if Elementary is in BIOS mode you could only boot it from UEFI/BIOS menu. But Windows will only work in UEFI mode.

Do not run the 'buggy' UEFI fix or the rename in Boot-Repair. That is renaming the Windows file, so you can then only boot Windows from grub menu. 
 Always say no until proven that you only can boot Windows entry from UEFI menu. And now some other work arounds may be better.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.


Post a new link to the info report from Boot-Repair.

---

### Post by gabrielgonc on 2014-08-17
Again I'm getting the grub bash, but now for both systems. :/

boot-repair report:
[http://paste2.org/65XUwyCD](http://paste2.org/65XUwyCD)

---

### Post by oldfred on 2014-08-17
You still show this file, I do not know if left over from before & Boot-Repair has returned original Windows file to be bootmfgw.efi or not.
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

You need bootmfgw.efi to be the original Windows file to directly boot Windows from UEFI menu or one time boot key, often f12 but varies by vendor.

Then you need to have grub or shim bootable from UEFI menu, or if one of the systems that will not boot anything but Windows like HP or Sony then you need a work around. But grub has to work with Boot-Repairs rename of Windows boot file to bkpbootmgfw.efi can only be booted from grub. System is booting bootmmgfw.efi which really is grub or shim.
Do you have secure boot on?
I know that most HP & Sony need work arounds, but others with Toshiba's have been able to boot.

Have you done a full backup of Windows? If system is critical and you have not made a backup, you are living on the edge. Also best to make a Windows repair CD or flash drive as sometimes you have to run Windows repairs and cannot get into the repair console booting Windows with f8.

      
 line 1066, you must keep saying no, go back and run the undo of the rename, so you can boot Windows.
WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

I do not see issue with grub? From live CD/flash drive. Unmount partition if already mounted. This copies a grub boot file to the system default boot and the cat lists the contents of the grub.cfg in your efi partition, it should be just 3 lines with a configfile reference to the real grub.cfg in your install.

 sudo mount -t vfat /dev/sda2 /mnt
sudo cp /mnt/EFI/elementary/grubx64.efi /mnt/EFI/Boot/bootx64.efi
cat /mnt/EFI/elementary/grub.cfg

---

### Post by gabrielgonc on 2014-08-17
> **oldfred said:**
> You still show this file, I do not know if left over from before & Boot-Repair has returned original Windows file to be bootmfgw.efi or not.
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

You need bootmfgw.efi to be the original Windows file to directly boot Windows from UEFI menu or one time boot key, often f12 but varies by vendor.

Then you need to have grub or shim bootable from UEFI menu, or if one of the systems that will not boot anything but Windows like HP or Sony then you need a work around. But grub has to work with Boot-Repairs rename of Windows boot file to bkpbootmgfw.efi can only be booted from grub. System is booting bootmmgfw.efi which really is grub or shim.
Do you have secure boot on?
I know that most HP & Sony need work arounds, but others with Toshiba's have been able to boot.

Have you done a full backup of Windows? If system is critical and you have not made a backup, you are living on the edge. Also best to make a Windows repair CD or flash drive as sometimes you have to run Windows repairs and cannot get into the repair console booting Windows with f8.

      
 line 1066, you must keep saying no, go back and run the undo of the rename, so you can boot Windows.
WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

I do not see issue with grub? From live CD/flash drive. Unmount partition if already mounted. This copies a grub boot file to the system default boot and the cat lists the contents of the grub.cfg in your efi partition, it should be just 3 lines with a configfile reference to the real grub.cfg in your install.

 sudo mount -t vfat /dev/sda2 /mnt
sudo cp /mnt/EFI/elementary/grubx64.efi /mnt/EFI/Boot/bootx64.efi
cat /mnt/EFI/elementary/grub.cfgwow, you got me really worried with the livin on the edge part. tried many time yes and no to "Do you want to activate [Backup and rename Windows EFI files]?" and "restore backup EFI files". currently, the one that at least made windows work through boot options is check "restore backup EFI files" and no to "...activate...". current report: [http://paste2.org/5tAgsy6E](http://paste2.org/5tAgsy6E)

I'll try the solutions you proposed a bit later, because fiancée is needing the notebook right now. i gotta arrange some backup, as well... hehehe

thanks a lot guys, very soon I'll report the situation again.

---

### Post by oldfred on 2014-08-17
There is a major bug in the installer on reinstalls, where it says it will overwrite Ubuntu but erases entire drive. And users make mistakes during installs and erase drive. And hard drives just fail. Always have a current version repairCD or flash drive or in the case of Linux a live installer for repairs. 

I am a old time belt & suspenders (not really) but have multiple flash drives with install and repair ISO, a full Ubuntu install and a Windows repair tool. But then Microcenter has a store nearby and at counter has flash drives and every time I go to store they are cheaper and larger, so I buy another one. :)

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs - Multiple similar examples
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Stinger on 2014-08-18
Hi all
In case you haven't noticed it, elementary OS Freya has a UEFI bug: ["Unable to boot via UEFI into installed freya system"]("https://bugs.launchpad.net/elementaryos/+bug/1355698")
The bug is targeted for Freya beta2.

---

### Post by gabrielgonc on 2014-08-20
> **Stinger said:**
> Hi all
In case you haven't noticed it, elementary OS Freya has a UEFI bug: ["Unable to boot via UEFI into installed freya system"]("https://bugs.launchpad.net/elementaryos/+bug/1355698")
The bug is targeted for Freya beta2.

Unfortunatelly, I was trying with luna. Does it have the same bug?

---

### Post by Stinger on 2014-08-21
> **gabrielgonc said:**
> Unfortunatelly, I was trying with luna. Does it have the same bug?

No, but AFAIK Luna is not able to handle UEFI because it has the original base of Precise with the old 3.2 kernel.
You could consider trying the [unstable ElementaryOS build from 2014-04-01]("http://sourceforge.net/projects/elementaryos/files/unstable/"), it's still Luna but it has the Saucy LTS Enablement Stack build in.
It has "kernel 3.11.0-19-generic" and should be able to handle UEFI, but I haven't tried it on a pc with UEFI myself, so I can't promise you anything.

Officially I can't recommend that you install it, because it's an 'unstable version' but what you do is completely up to you ;)
Try it live first to see if it works and remember to do backup.

---

### Post by gabrielgonc on 2014-08-23
Hey, guys! just checking in to say that i DID IT! used freya, in fact, and the only thing different this time is that I successfully ran boot-repair from live cd after removen the word "linux" at the end of the grub install command. :)

thanks again for your help. You guys rock!

---


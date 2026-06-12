---
title: "Unable to boot into Windows 10 after dual installing ubuntu 20"
date: 2020-07-24
forum: Windows
---

### Post by d4bidrp0 on 2020-07-24
Hello, I hope someone can help me, 

I'm trying to **dual boo**t my new pc with windows 10 (pre-installed) and Ubuntu 20. 
Windows was left in the sda3 partition while ubuntu was installed in a new partition sda4.
After installing ubuntu, windows is not booting anymore.
In the grub and boot menu I only see Ubuntu and Windows Boot Manager options (Not Windows 10) 
and booting into WinBootMang lead to the windows blue screen error. 

I already tried **update-grub** from ubuntu - [B]not fixing the problem
[/B]
**boot-repair **is neither fixing the problem, **grub-update **shows: 

====================== sda4/boot/grub/grub.cfg (filtered) ======================
Ubuntu   607c4eec-a1e1-4988-abf0-5f61f5669f53
Ubuntu, with Linux 5.4.0-42-generic   607c4eec-a1e1-4988-abf0-5f61f5669f53
Ubuntu, with Linux 5.4.0-26-generic   607c4eec-a1e1-4988-abf0-5f61f5669f53
Windows Boot Manager (on sda1)   osprober-efi-3099-BBDE
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

but some pieces of the report gives me hope since somehow is detecting windows in sda3 partition:
================================ 2 OS detected =================================
OS#1:   The OS now in use - Ubuntu 20.04 LTS CurrentSession on sda4
OS#2:   Windows 10 on sda3

Additional info: Not pretty sure if windows was UEFI or BIOS but ubuntu is installed as UEFI. 
I also tried this thread [https://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader/504360#504360](https://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader/504360#504360)
for fixing windows boot loader but still not working. 

I also attached the boot-info report for detailed information. 

I hope to get some help for fixing the problem :) :) :) :D 
Thanks beforehand to anyone trying to help.

---

### Post by CelticWarrior on 2020-09-02
> [COLOR=#000000]In the grub and boot menu I only see Ubuntu and Windows Boot Manager options (Not Windows 10)[/COLOR]

If you have only Windows 10 installed then "Windows bootloader manager" is the bootloader for Windows 10. If you have more than one Windows installed, of the same or different version, "Windows booloader manager" will be the same for all of then, users have to select which one after booting "Windows..." frfom the Grub menu.

> [COLOR=#000000]and booting into WinBootMang lead to the windows blue screen error.[/COLOR]

Grub only boots working Windows, period.

---

### Post by oldfred on 2020-09-02
Can you directly boot Windows from UEFI boot menu?

Grub only boots working Windows.
And that also means Windows fast start up must be off and Windows cannot need chkdsk.
You may be able to boot Windows from UEFI boot menu and turn off fast start up or make other repairs.

Boot-Repair does not fix Windows issues. It is for Linux issues and the main fix it does is reinstall grub2 or update grub menu.
You need to have a Windows repair flash drive.

---


---
title: "Cannot boot into Windows 8.1 after removing Ubuntu 16.10"
date: 2016-11-07
forum: Windows
---

### Post by aaroncam on 2016-11-07
Ok so I have basically tried everything else on the internet I was dual booting windows 8.1 pro and ubuntu 16.10 
, And I'm not sure what to do. My computer boots up into the ubuntu rescue mode and I cannot get passé day it. When I place my repair USB stick it I have tried to use the following commands already 

bootrec.exe /fixboot

bootrec.exe /fixmbr

bootrec.exe /rebuild bcd

and I'm baffaled as I have no idea what to do. I want to retain windows in my system.

Oh the reason its like that is because I deleted the ubuntu partition by the way.

---

### Post by jimmyvh on 2016-11-08
Seems you want to get back your original windows bootloader. Microsoft describes the following steps to do so:

[COLOR=#333333][FONT=&amp]1. Boot from the Windows USB stick or DVD. If prompted, press any key to start Windows from the installation disc. [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]2. Choose your language and click Next. [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]3. Click Repair Your Computer and then select the operating system you want to repair. [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]4. Select Command Prompt and try the following commands (a single command might work, or you may need to use multiple commands depending on the exact problem): [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]bootrec /fixMBR [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]bootrec /fixBoot [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]bootrec /rebuildBCD [/FONT][/COLOR]

---

### Post by oldfred on 2016-11-08
UEFI or BIOS?
BIOS the bootrec fixes should reinstall a Windows boot loader to the MBR overwriting the grub boot loader in MBR.
If UEFI, you just need to in UEFI change default to Windows entry and/or choose from one time boot key the Windows UEFI entry.

If you deleted Ubuntu, you should also then remove the /EFI/ubuntu folder in the ESP - efi system partition and remove the ubuntu entries in the UEFI NVRAM remembered settings.
       Uninstall Ubuntu from menu, Really UEFI boot menu 
[URL="http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu"]http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu
[/URL]
 Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/) 

[URL="http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu"]
[/URL]

---

### Post by aaroncam on 2016-11-08
So should I Reinstall ubuntu and fix it from there? The windows repair drive is not working properly, with the bootrec, ect.

Oh my computer has a bios. It's a dell vostro 200 but it still does not work with the fix boot,fix mbr

---

### Post by oldfred on 2016-11-08
You can only do minor fixes of Windows from Linux.

If BIOS you need to just run Windows repairs. 
Sometimes you have to run chkdsk 3 or more times until no errors.

---

### Post by aaroncam on 2016-11-08
I have tried the boorec commands around 15ish times all 3 of them and I'm still getting the grub rescue errors.

And where to I run chkdsk?

---

### Post by oldfred on 2016-11-08
Since all Windows issues moved to Windows sub-forum.

If you have run this from Windows repair disk then you cannot be booting grub in BIOS boot mode.
[COLOR=#333333][FONT=&amp]bootrec /fixMBR 

[https://technet.microsoft.com/en-us/library/cc730714.aspx](https://technet.microsoft.com/en-us/library/cc730714.aspx)
[/FONT][/COLOR]        chkdsk c: /b
/b includes /r 

Above is all Windows command prompt/terminal commands, not Linux.
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

So we know where you are at, from Ubuntu live installer:

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by aaroncam on 2016-11-08
I'm sorry I'm still a little lost, could you give me a step by step of what you want me to do? Thanks. For all the help.

---

### Post by oldfred on 2016-11-08
From Ubuntu live installer run Boot-Repair's summary report just to confirm what you configuration is.
It can only do minor Windows repairs but will at least show partitions, boot loaders & possibly issues.

Otherwise running Windows repairs from a Windows repair disk should work.

---


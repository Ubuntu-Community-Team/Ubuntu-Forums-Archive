---
title: "Boot Straight To WINDOWS 10 (No GRUB)"
date: 2016-11-28
forum: Ubuntu/Debian BASED
---

### Post by zakwanzen on 2016-11-28
Hi. First of all, thanks for taking your time to read this thread! 

I had formatted my laptop and install Windows 10 followed by Elementary OS.

But whenever i open my laptop, it straight boot to Windows 10. No GRUB screen appear. 

I had try these following solutions:
1. Run live USB Boot Repair ISO and click "Recommended Repair"
2. Run the following command in Windows 10:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
bcdedit /set {bootmgr} path \EFI\ubuntu\grub64.efi

But those solution does not working.
Here is the link of pastebin (i got it from doing solution 1):
[http://paste.ubuntu.com/23550676/](http://paste.ubuntu.com/23550676/)

---

### Post by oldfred on 2016-11-28
From f12 UEFI boot menu can you boot ubuntu entry?

You have a BIOS boot syslinux in the gpt protective MBR for Windows BIOS boot. You can ignore that, and never should use it, as it never will work anyway. With UEFI/gpt Windows only boots in UEFI mode anyway.

Some systems only boot by description. That is now allowed by UEFI spec. And of course only valid description is "Windows Boot Manager". But many work arounds.
Most common work around is to use the fallback or hard drive entry (not ubuntu entry) will still can be set as default. Before you had to manually copy files, but Boot-Repair does the copy of shimx64.efi to bootx64.efi if in advanced mode you check use standard efi file.

You may still have to add an UEFI hard drive entry with efibootmgr.
       You can add your hard drive entry to boot fallback file:
sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'
sdX is drive, Y is efi partition 

      
 Toshiba Satellite - turned Secure boot off in Boot-Repair update
[URL="http://ubuntuforums.org/showthread.php?t=2317643"]http://ubuntuforums.org/showthread.php?t=2317643
[/URL]
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 


Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---

### Post by zakwanzen on 2016-11-29
I try F12 to see whether Elementary in the boot entry. There is none.

So i must run the sudo command you give me through live USB Elementary OS?

---

### Post by oldfred on 2016-11-29
If you have run Boot-Repair to get shimx64.efi copied to bootx64.efi, then you can use the efibootmgr command to add an entry to your UEFI boot menu to boot from bootx64.efi.

---

### Post by spectatorx on 2016-12-08
You may need to set it in uefi/bios settings to boot with ElementaryOS boot entry.

---


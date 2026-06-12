---
title: "Dual boot ubuntu - Windows 10: windows won't load"
date: 2021-04-26
forum: Windows
---

### Post by glanzarini on 2021-04-26
Hi guys. 

I'am new to the forum (and to ubuntu as well!) so please bear with me.


I have a lenovo laptop with a dual boot windows 10 - ubuntu configuration. At first everything worked fine with both OS but now windows won't load. After I select windows boot from the GRUB menu, windows returns a blue screen error (BAD SYSTEM CONFIG INFO). If I try to recover the system with the windows automatic repair tool, it doesn't work.

I tried running boot-repair from ubuntu and this is the log file:

[http://paste.ubuntu.com/p/2GmMGzg7mj/](http://paste.ubuntu.com/p/2GmMGzg7mj/)

Following the instructions I found online I also tried from windows prompt with this command:

bootrec /rebuildbcd

but all i get is:

Total identified Windows installations: 0

If I try to fix that, I get stuck because I can't find a c:/boot directory on my pc.

I need help from someone with more experience, because I think I am really out of my depth here!

Thanks for your help.

G

---

### Post by yancek on 2021-04-26
If it was working, what changes were made just prior to the failure?

Boot repair shows you have windows code in the MBR plus 2 EFI partitions.  Was this an upgrade from windows 7?  You have 2 EFI partitions (sda2 and sda3) and you should only have one.

Your EFI output shows Boot00002 as the windows boot (line 107 in boot repair).  If you access the BIOS firmware on boot, are you able to boot windows from that selection?   I don't know what LrsBootmgr.efi is (on sda3), never seen that before.  Also, do you have Legacy/CSM boot enabled?  If so disable it and try booting windows from the BIOS,

---

### Post by glanzarini on 2021-04-26
Hi Yancek and thanks for your reply!

I will try to answer your questions as best as I can.

I do not recall any changes just before Windows stopped working. Maybe it was an automatic windows update? 

Yes, my windows 10 is an upgrade from a previous version, but I'm not sure if it was 7 or another release.

I already disabled Legacy but it didn't help.

In my bios I can't find where to choose which partition to boot from.

Thanks.

---

### Post by oldfred on 2021-04-26
The error seems to be from trying to boot in Legacy/CSM/BIOS boot mode using the Windows boot loader in MBR.
Installing that BIOS/MBR boot loader was an error, but it should not matter as long as you never boot in Legacy mode.

I have seen some Lenovo's that have a second FAT32 partition with Lenovo's system repair files.
The UEFI entry for recovery 0007 uses that second FAT32 as boot.
Normally systems should have only one ESP - efi system partition. But once an UEFI entry is made to boot a FAT32 partition using its GUID, then it seems like it may work, even if another partition is then made the ESP.

---

### Post by glanzarini on 2021-04-26
Hi Oldfred

thanks for your help. I have to admit I didn't understand much of your reply! I told you I'm a newbie! :D

What are the next steps I should take?

Thanks again.

G

---

### Post by oldfred on 2021-04-26
Are you sure you have disabled Legacy boot?

On my Asus motherboard system, I have 3 boot modes, UEFI (only), CSM, & UEFI or CSM. And UEFI has two modes, UEFI Secure Boot on, or off.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
But it only boots in UEFI mode with UEFI only setting.

---

### Post by glanzarini on 2021-04-27
Yep, I am sure Legacy boot is disabled.

Please help!

---

### Post by yancek on 2021-04-27
When you initially boot and enter the BIOS firmware, you should see an option which is usually labelled Boot where you can make the changes.  I'm not familiar with Lenovo so you might do an online search on how to change EFI boot options in the BIOS of your particular Lenovo.

---


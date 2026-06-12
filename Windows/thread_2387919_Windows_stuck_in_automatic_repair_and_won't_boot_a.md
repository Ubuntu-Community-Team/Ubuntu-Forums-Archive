---
title: "Windows stuck in automatic repair and won't boot after ubuntu dual boot install"
date: 2018-03-25
forum: Windows
---

### Post by lethalflashbang on 2018-03-25
Hello,
I installed ubuntu and can load into that just fine, but when I try to boot into Windows, it says "Performing automatic repair" then proceeds to say diagnosing your pc then it says that it couldn't do anything and prompts me to shut off or view advanced settings (system restore, command prompt, ect.).
Thanks for any help in advance.

---

### Post by oldfred on 2018-03-26
Is that booting from grub?
And that is often the case if Windows fast start up is on.

You need to directly boot Windows which is easy if UEFI as you can boot from UEFI boot menu.
But if BIOS you have to temporarily reinstall a Windows boot loader to MBR, fix Windows, then restore grub.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Grub only boots working Windows. Or Windows that is not hibernated nor if it needs chkdsk. You then need your Windows repair disk to fix Windows, but may be able to directly boot Windows and use f8 to get into internal repair console.
Note that Windows 10 will turn fast start up back on with updates, so an on-going issue. Best if system is UEFI as then you can always directly boot Windows.

If BIOS:
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by lethalflashbang on 2018-03-26
dang, sounds like fast startup turned itself on again... I'll try to do what you say tomorrow morning and post results.. Thanks

---


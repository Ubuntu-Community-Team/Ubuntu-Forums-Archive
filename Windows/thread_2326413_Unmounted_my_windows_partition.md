---
title: "Unmounted my windows partition"
date: 2016-05-31
forum: Windows
---

### Post by Thomas_Deweer on 2016-05-31
Hey,

I am totally new to this but this is what happend.
I was testing my ubuntu that i installed on a usb flash drive. I wanted to access my (working) windows partition trough ubuntu. I was doing this as a test because I was about to help someone with his crashed windows.

However, when it said my drive was hibernated i went online to see how i could mount the windows partition. So i ran this command:
sudo mount -o ro /dev/sda2 /mnt
As soon as i did it, my partition disapeared from my explorer in ubuntu. Then i went to restart to boot my windows but my computer says: "Reboot and select proper boot device or insert boot media in selected boot device and press a key".

Any help or advice would be welcome.

---

### Post by oldfred on 2016-05-31
Mounts in /mnt do not show in Nautilus left panel.
You have to go to computer and drill down to /mnt to see it.

Did you force reboot with control alt del? You never should do that with Linux. But remember the elephants.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Windows 8 or later is always hibernated, and Linux will not mount NTFS read/write that is hibernated or needs chkdsk, so it will not damage the partition and then chkdsk might not be able to repair it.
Since mounted ro read/only, it would not have changed anything in Windows and the issue should not have been related to anything from Linux.

Did you change boot mode in UEFI. If Windows 8 or later, it should be UEFI and should boot if UEFI with secure boot on, or just with standard UEFI. But will not boot with BIOS/CSM mode.
How you boot a flash drive is not necessarily the same as the default boot in UEFI.
But since you said your Windows was sda2, that seems like a BIOS boot install, with sda1 as Windows boot partition. If you turned UEFI on, then it will not boot.

       
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Thomas_Deweer on 2016-05-31
I didnt force reboot, i just shutted down my ubuntu by pressing shut down. However I restarted the ubuntu and the partition of windows is there, but i still can't boot trough it.
For some reason i can go inside my windows boot partition now and see the files. Would pressing the up arrow next to the partition solve my issue?
I did the boot info to give more information.

[http://paste2.org/Xb5tc8hO](http://paste2.org/Xb5tc8hO)

Is there anything usefull u can see in this to help me further?

---

### Post by oldfred on 2016-05-31
Moved to Windows sub-forum since no Ubuntu installed.

I think script is just saying you left fast start on, or that it needs chkdsk.
You can only run chkdsk from Windows or Windows repair disk in Safe mode or its repair console.

Can you boot Windows and use f8 to get into its internal repair/safe mode? If not you need a Windows repair flash drive or installer with repair console.
You normally do not have time from grub menu to use f8 as it boots too quick. Some have tried and after multiple tries and pressing keys at almost same time have gotten it to work. But better just to have Windows repair disk.

You show Windows boot loader (syslinux is  a Windows type boot loader) that should directly boot Windows. Then make whatever repairs.
Boot-Repair can only run minor repairs to Windows like install syslinux. So you really need a Windows repair disk.

---


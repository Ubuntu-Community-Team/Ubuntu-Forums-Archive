---
title: "Windows 7 alongside Ubuntu"
date: 2014-07-26
forum: Windows
---

### Post by henrynalven on 2014-07-26
Hi, I'm trying to install Windows 7 64bit alongside Ubuntu 14.04. I made a partition on my HDD and when I try to install Windows I get a message saying "Windows cannot be installed to theis disk. The selected disk is of the GPT partition style." I've tried installing to an ntfs formatted partition and an unallocated partition. 

I am unable to boot the DVD in UEFI mode but I could when I installed Ubuntu. Has anyone else had this problem?

---

### Post by skimo12 on 2014-07-26
Hello Henry, i think that you'll get some more concrete answers soon. Please give us a bit more background. It seems that you are trying to install windows7 after installing Linux. Normally the way that it's done is to install Windows first, then install Ubuntu. I'll see if I can find a good link on this.

---

### Post by skimo12 on 2014-07-26
I found [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) , which confirms that you need to install windows first. However, it seems to support the idea you had to do the partitioning yourself. I'm now out of my depth : ) , and i'll leave this to the more experienced peeps. : )

---

### Post by henrynalven on 2014-07-26
In the past I've had issues installing Ubuntu with Windows installed first (severe graphical glitches), I'm not sure if that was why. Really, I'd hate to reformat my entire drive for Windows because I only plan on using it to run games that I can't get to work with Wine.

---

### Post by kurt18947 on 2014-07-26
I installed Windows 7 32 bit on a disk that already had Ubuntu Gnome.  This disk was 'MSDOS' but I thought 64 bit Windows 7 would install on GPT/UEFI systems.  The problem I had was Windows overwriting Ubuntu's boot info.  The boot repair CD fixed that.  I've not messed with GPT formatted disks so I'm no help there.

---

### Post by henrynalven on 2014-07-26
I found my solution. While digging around my box of old computer stuff, I came across an old hard drive. I blew off the dust, popped it in my pc and Windows is installing.

---

### Post by henrynalven on 2014-07-27
Ok, so I have windows successfully installed, but during boot up, I don't have the option to choose between Ubuntu and Windows, I have to choose the hard drive to to boot from. Does anyone know how to get GRUB to ask which OS to boot?

---

### Post by oldfred on 2014-07-27
If you have Ubuntu in UEFI mode on gpt partitioned drive and Windows in BIOS mode on a MBR(msdos) drive, you cannot dual boot from grub menu. UEFI & BIOS are not compatible and you then can only boot from UEFI/BIOS menu or from one time boot key like f12 is on my system.

You can convert a Windows 7 DVD to UEFI installer by copying to a flash drive and doing some updates.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---


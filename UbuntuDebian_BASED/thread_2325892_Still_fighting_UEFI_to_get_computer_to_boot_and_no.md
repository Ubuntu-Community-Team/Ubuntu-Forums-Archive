---
title: "Still fighting UEFI to get computer to boot and not just lock up on mobo splash scree"
date: 2016-05-26
forum: Ubuntu/Debian BASED
---

### Post by bennylava2 on 2016-05-26
Hi all. First thing I should say is I'm pretty much a Linux noob. So please bear that in mind. But I'm trying to learn it, and I'm running into problems just getting it to boot like we all agree that a computer should. 

I'm having some major problems getting an Ubuntu variant to boot normally on my computer. Its Zorin, I'm sure many of you have heard of it. The way things are now, it looks like I'm going to have to reinstall W7 using legacy. I learned that only 2 linux distros have  permission to implement or play well with UEFI: Ubuntu and Fedora. The rest no pay, no  play. 

I've now learned a bit about UEFI, and it seems its something of a BIOS  replacement. Sort of like the new and improved BIOS, if you will. Please  correct me if I have that wrong. But if that's the case, when you want to install Zorin, you're  basically telling UEFI to run in BIOS mode, right? You're never actually  going to be able to sort of "get rid" of UEFI. Your best bet is to get  it to work with the older stuff that is made to work with the old BIOS  rules, correct? Makes sense when you consider Ubuntu had to buy rights  to make it play well with UEFI. Or whatever the exact story is on that.  Either way, they had to cough up some money for it. Maybe Zorin is included since its ubuntu based? I'm probably not that lucky. 

  Anyway, isn't this going to be an intrinsic problem with most of the Linux  distros? Fighting with these new UEFI bios replacements, and trying to get  it all to work together? Cause like I said my settings to legacy don't  stick. The just change right back to UEFI when I had set it to legacy.  Granted I don't fully understand how its interacting with Windows, but  it looks like windows is all it really seems to care about. Cause when  the Windows 7 drive is unplugged, it still doesn't want to play nice and  just boot into Linux. It will, a time or two. Before it reverts the  settings from legacy back to UEFI. And then we're back to it locking up  on the mobo splash screen and me having to hit the cmos reset button.

If their idea was to drive me away from linux, its working. And some have theorized this, because IIRC microsoft had a big hand in the creation of UEFI. I know its old, as far back as 2002. But like everything there have been some changes as of late. Any help with this problem would be greatly appreciated.

---

### Post by oldfred on 2016-05-26
Moved to other OS since not an Official flavor.
       [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, Mythbuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE  

Do not know Zorin, but if based on Ubuntu it should support UEFI boot.
But almost all Windows 7 installs are BIOS based with MBR partitioning. You can install Windows 7 in UEFI mode if Secure boot is off, and a very few systems were shipped with Windows 7 in UEFI mode on gpt partitioned drives.

Always best to have all systems installed in same boot mode with newer UEFI hardware.
There are three boot modes, UEFI with Secure Boot, UEFI and CSM. Standard UEFI & CSM are will not work with Secure setting on.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Some systems also do not call it Secure boot, but have a setting for "Windows" or "Other". Key clue that is really Secure boot is that fine print says you must install Windows 7 in "Other" mode as Windows 7 does not support Secure boot.

And how you boot flash drive is then the boot mode it installs. But that boot mode may not be the default you have in UEFI to boot install you just made. So you must be consistent in how you boot.
And if Windows is BIOS/MBR best to always boot in CSM/BIOS/Legacy or whatever your specific system calls it.

Do you have Zorin installed?
      
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by bennylava2 on 2016-05-27
Thanks for the link. Do you know if I this can be done from an installed Distro? That is already installed on a hard drive. Well I had zorin installed, but somehow I broke it. It locked up and and now it hangs up when its trying to load the OS and it never actually loads Zorin. 

So let me see if I am understanding you right. Before I actually go to reinstall windows, I need to set my UEFI bios to CSM? Or is this going to be an option during the W7 install? 

Is there any way to salvage this without having to reinstall windows? As I said previously my settings in UEFI bios don't stick, they just revert. Is there an option when installing Ubuntu where I can tell it that I want to have it play nice with UEFI?

---

### Post by oldfred on 2016-05-27
How you boot installer UEFI or BIOS, is then how it installs, for both Windows & Ubuntu.

Very difficult to convert a Windows install.
Windows in BIOS mode has to have the 35 year old MBR(msdos) partitioning.
Windows in UEFI boot mode has to have gpt partitioning.
Ubuntu can boot in either UEFI or BIOS mode from gpt, but really should only use BIOS from MBR as UEFI wants gpt. But note installer is often a FAT32 partition on a MBR flash drive and boots in UEFI mode.

I believe you have to copy Windows 7 DVD or ISO install to flash drive and move a couple of boot files into an ESP - efi system partition for UEFI boot.
 How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)

You can run Boot-Repair from most Linux, either its live Lubuntu, your Ubuntu installer or any Ubuntu install after installed.
But Boot-Repair is primarily for Linux, very few fixes for Windows can be done from Boot-Repair.

---


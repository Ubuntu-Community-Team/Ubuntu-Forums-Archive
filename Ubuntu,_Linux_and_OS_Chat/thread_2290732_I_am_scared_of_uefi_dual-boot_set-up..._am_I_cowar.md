---
title: "I am scared of uefi dual-boot set-up... am I cowardly lion?"
date: 2015-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by t0p on 2015-08-14
For years I've been running Windows/Ubuntu dual-boots, and the set-up couldn't have been easier.Make Unetbootin USB, tell it to do a side-by-side installatiojn, and KA-ZOOM!! (well not quite KA-ZOOM but you get the idea) I had a Windows/Ubuntu computer.

But now this UEFI has come along, and I'm reduced to noobiness again.  I don't get it: the guides I read say I have to use some special "Power2Go 10" uefi bootloader.  Which confuses me - I have a Ubuntu 14.04.3 live USB courtesy of Unetbootin, and I can run live sessions on my new computer.  So what would happen if I hit "Install" instead of "Try without installing"?  Would I be up an unspeakable creek sans paddle?

I started this post as a general "ya boo sucks" complaint, but now fear it's veering towards a support thing?  Mods, please relocate as your omnipotence/omniscience/omnibus sees fit.  Ta!

---

### Post by qamelian on 2015-08-14
I didn't bother with Power2Go. All P2G does is allow you to mount an ISO image as if it was a physical disk. If you're starting from Windows, you don't need to do that. I started with a freshly formatted thumb drive, and just opened the ISO and copied it's contents to the thumb drive. I rebooted Windows 8.1 (and later 10) while holding down the Shift key, in order to get the UEFI boot menu. From there, I selected UEFI USB Device to boot from the thumb drive and proceeded with the install as usual. All went well, except for a couple of options I needed to add to GRUB to get my laptop to shutdown properly, but that had nothing to do with UEFI. 

Since I didn't wanted to do the UEFI dance above every time I wanted to launch Ubuntu, in my BIOS, I set the boot sequence to boot from my Ubuntu partition first, which gives me the old familiar GRUB boot menu, rather that the Windows UEFI equivalent, and which still recognizes Windows for those occasions I decide to use it.

Honestly, I didn't find the process any more difficult than on a non-UEFI system. If anything I like it better and find it more flexible.

---

### Post by Geoffrey_Arndt on 2015-08-15
I decided up front to start supporting the small companies that provide pre-installed, pre-configured PC's with Linux on board.   Went with a System76 Galago Ultra Pro.   Took all of 10 minutes to setup . . . no uefi hassles.   And updating from 14.10 to 15.04 was smooth as butter.   That's the route I'll be taking from now on . . . . the system uses a standard BIOS . . . no muss, no fuss.

---

### Post by kagashe on 2015-08-16
> **t0p said:**
> For years I've been running Windows/Ubuntu dual-boots, and the set-up couldn't have been easier.Make Unetbootin USB, tell it to do a side-by-side installatiojn, and KA-ZOOM!! (well not quite KA-ZOOM but you get the idea) I had a Windows/Ubuntu computer.

But now this UEFI has come along, and I'm reduced to noobiness again.  I don't get it: the guides I read say I have to use some special "Power2Go 10" uefi bootloader.  Which confuses me - I have a Ubuntu 14.04.3 live USB courtesy of Unetbootin, and I can run live sessions on my new computer.  So what would happen if I hit "Install" instead of "Try without installing"?  Would I be up an unspeakable creek sans paddle?

I started this post as a general "ya boo sucks" complaint, but now fear it's veering towards a support thing?  Mods, please relocate as your omnipotence/omniscience/omnibus sees fit.  Ta!

If you are installing from Ubuntu 14.04.3 live USB you don't need any uefi bootloader. but it will be better if you resize Windows partition while in Windows to make free space for making Linux partition during installation. By the way which version of Windows are you going to dual boot 7, 8, 8.1 or 10.

Kamalakar

---

### Post by mastablasta on 2015-08-18
> **Geoffrey_Arndt said:**
> I decided up front to start supporting the small companies that provide pre-installed, pre-configured PC's with Linux on board.   Went with a System76 Galago Ultra Pro.   Took all of 10 minutes to setup . . . no uefi hassles.   And updating from 14.10 to 15.04 was smooth as butter.   That's the route I'll be taking from now on . . . . the system uses a standard BIOS . . . no muss, no fuss.

except you don't get windows that way which some may want.

to the OP read the UEFI wiki page. seems quite clear to me. also do not mistake secure boot with UEFI. they are not one and the same. UEFI is arround since 2001 or something like that and one of the first OS to actually support it wasn't Windows or MacOS but Linux.

most importantly use clonezilla or redobackup to create an image then play all you like with your system drive. if you fail, you can just reimage the drive.

---

### Post by oldfred on 2015-08-18
What brand/model system? And what video card/chip?

Best to fully backup Windows & efi partition.
Use Windows tools to shrink the NTFS partition and reboot immediately to make sure it runs chkdsk to repair its new size.
Make sure fast startup in Windows is off. 
And if UEFI has a fast boot setting best to turn it off also.
And in UEFI turn off secure boot, although Ubuntu will boot with it on, you cannot currently use grub to dual boot with secure boot on.

I prefer to partition in advance as I have 25GB / (root) and large data partition(s).
I recently did all of above on a new Dell SFF Intel system which took several days. Backup alone was a lot as I had a Windows backup that Windows wanted, a Dell backup that Dell wanted & my own full system backup. That was 2 flash drives and multiple DVDs.

Then Ubuntu Something Else install to a working system on hard drive took 10 Minutes. I do have fast Internet.

Lots of details if not sure of how to do any of the steps are in link in my signature.

---

### Post by kagashe on 2015-08-19
> **oldfred said:**
> you cannot currently use grub to dual boot with secure boot on.

It works.

Kamalakar

---

### Post by neu5eeCh on 2015-08-19
You might not be so cowardly:

[http://linuxbsdos.com/2015/08/12/grub-install-errors-while-attempting-to-dual-boot-windows-10-and-linux-distributions/](http://linuxbsdos.com/2015/08/12/grub-install-errors-while-attempting-to-dual-boot-windows-10-and-linux-distributions/)

I haven't tried dual-booting with 10 yet (bought my last system from System76), but it definitely seems dicier than before---some suggesting that MS is to blame. Whether that's deliberate remains to be seen.

---

### Post by kagashe on 2015-08-20
> **VTPoet said:**
> You might not be so cowardly:

[http://linuxbsdos.com/2015/08/12/grub-install-errors-while-attempting-to-dual-boot-windows-10-and-linux-distributions/](http://linuxbsdos.com/2015/08/12/grub-install-errors-while-attempting-to-dual-boot-windows-10-and-linux-distributions/)

I haven't tried dual-booting with 10 yet (bought my last system from System76), but it definitely seems dicier than before---some suggesting that MS is to blame. Whether that's deliberate remains to be seen.This post is dated August 12, 2015 and the blogger could install Windows 10 and Linux mint as per [post dated August 18, 2015]("http://linuxbsdos.com/2015/08/18/how-to-dual-boot-linux-mint-17-2-windows-10-windows-8-1-on-a-pc-uefi-firmware/") 

Please note that the most important instruction is to select the **Device for boot loader installation** which should be "Boot EFI Partition".

The earlier attempt failed because he depended on default selection viz /dev/sda.

Kamalakar

---

### Post by oldfred on 2015-08-20
The error reported was from Fedora.

With grub it still normally is to install grub to a drive like sda, not a partition like sda2.
With UEFI it seems to automatically know to write to the ESP.

But there were some systems with locked ESP - efi system partitions. Nothing could be written into them. The solution seemed to only be to backup efi folders, erase FAT32 partition, create new FAT32 partition with boot flag & restore efi folders. Then it worked.

A very few have created two boot partitions which means two ESP. Which then also will cause issues.

---

### Post by kurt18947 on 2015-08-20
> **VTPoet said:**
> You might not be so cowardly:

[http://linuxbsdos.com/2015/08/12/grub-install-errors-while-attempting-to-dual-boot-windows-10-and-linux-distributions/](http://linuxbsdos.com/2015/08/12/grub-install-errors-while-attempting-to-dual-boot-windows-10-and-linux-distributions/)

I haven't tried dual-booting with 10 yet (bought my last system from System76), but it definitely seems dicier than before---some suggesting that MS is to blame. Whether that's deliberate remains to be seen.

I've read first hand accounts where Windows 10 upgrades to existing dual boot machines didn't break GRUB. That seems hopeful. On the other hand, as far as I can tell Microsoft no longer requires OEMs to include a way to disable secure boot like they did with Windows 8.x. OEMs are not forbidden to provide a way to disabled SecureBoot as they are with ARM/WinPhone but they're also not required to include a means to disable SB. I guess we'll have to start keeping a list of which OEMs and machines permit disabling fastboot/secureboot and which ones don't. And hope that list stayed somewhat up-to-date. Or buy from System76, ZaReason et. al.

---

### Post by mastablasta on 2015-08-21
is secure boot an issue with Ubuntu? as I understand it is not.

---

### Post by oldfred on 2015-08-21
I do not believe secure boot is an issue either. 
But I think the entire secure boot issue from Windows is more marketing than offering security. 

There was an issue that you could not boot Windows from grub with secure boot on, only from UEFI menu or one time boot key, but I have seen users say it does work now.

---

### Post by t0p on 2015-08-24
Thanks everyone who replied to my post.  I feel a little less cowardly now and will attempt to install Ubuntu 14.04.3 next to Windows 8.1 on my laptop when I get the chance (the laptop in question is elsewhere at the moment).

I've used Windows 8.1 some since I got the laptop, and it's constantly telling me it's found unwanted progs on the computer.  Mostly something to do with Firefox (annoying as I don't have Firefox on the laptop any more).  It's so hectic, compared to what I've been used to for years using Ubuntu.

I'm really miffed with Microsoft or HP or whoever it is that's brought uefi to the party.  My previous laptop (the one I'm using now) had Windows 7 on it, and I stuck Ubuntu 12.04 next to it no problems.  But on Windows 8.1 I have somehow picked up spyware and/or adware from somewhere (something called TriplePose I think?) and I get pop-ups all over the place, using Chrome (or Chromium, I forget) even though I have AdBlock Plus installed which is squashing even more ads for me.  Without ABP I'd be so snowed under with ads I wouldn't be able to do anything online.

I've been spoilt by many years of relatively hassle-free Ubuntu use.  V tempted to find a way to scrape Windows 8.1 off my laptop altogether and stick with what works best for me.  Just unsure how to do it.  I know you guys are mostly saying there's no real probs but... I don't buy new computers very often.  I can't afford to murder my latest...

---

### Post by oldfred on 2015-08-24
If it is an HP it is a bit more of an issue.

HP violated UEFI, and adds a description requirement to boot. And of course the only valid description is "Windows". 
But we have many work arounds and when you get there we can suggest which may be better. Some work for dual boot, some are better if only Ubuntu, and some users like a gui boot manager like rEFInd which also is a work around.

---


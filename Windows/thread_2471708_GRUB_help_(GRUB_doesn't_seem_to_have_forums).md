---
title: "GRUB help (GRUB doesn't seem to have forums)"
date: 2022-02-07
forum: Windows
---

### Post by tobias-richards on 2022-02-07
Sorry, but I don't know where else to turn to for GRUB help.

I have a USB stick with the Windows XP i386 installer using NTFS. I don't want to use FAT because I'll eventually want to repeat this process for booting installed XP with NTFS. No Linux is installed. The operating-system-that-must-not-be-named (lest this post be moved to the wrong forum) is installed. Here is what I'm trying to do:

I want to be able to boot my NTFS USB stick (and later the WinXP partition) with GRUB x64. GRUB x64 supports FAT, but not NTFS. I've heard that there is something called a "chain boot" that will allow GRUB x64 to boot to NTFS. How can I accomplish this for an NTFS USB and later NTFS partition?

GRUB i386 won't work because of the hardware-which-must-not-be-named.

If it helps, I'm using rEFInd x64.

---

### Post by coffeecat on 2022-02-07
First up: this doesn't belong in General Help. The strapline for General Help is clear and states:

> All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, Ubuntu Mate, Ubuntu Budgie, Ubuntu Studio and Ubuntu Kylin.

This question has nothing to do with Ubuntu or any of the *buntu flavours.

Second:

> **tobias-richards said:**
> 
GRUB i386 won't work because of the hardware-which-must-not-be-named.


The forum staff are volunteers who do their best to keep the forum running optimally for all members. Their work is not helped by playing silly games like this. You are using Apple Hardware. You've already made that clear in earlier threads. But this is an occasion when your question doesn't belong in the Apple Hardware section, *because you are not using *buntu.*

I've moved this thread to the Windows sub-forum, at least for the time being, since you appear to be trying to boot Windows with grub. I'll be interested to see if anyone has any solution for you.

---

### Post by oldfred on 2022-02-07
Windows XP was BIOS/MBR only.
But Macs are UEFI/gpt.
And rEFInd is for UEFI boot.

There was such a thing as hybrid gpt/MBR, but not recommended.
It was for booting old versions of Windows on Macs. Not sure if it worked back with XP.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

Years ago with BIOS PC, I created a Windows 7 repair flash drive. But it only used a small part of flash drive.
So I installed BIOS grub to NTFS Windows 7 partition and created my own grub boot stanza to boot the Windows repair partition PBR and loopmount several ISO in another partition. Do not remember details, but issue with /boot & /Boot in Windows as in Linux it is different, but Windows sees it the same.

Using UEFI, rEFInd & a Mac greatly complicate the issue.

---

### Post by rsteinmetz70112 on 2022-02-07
There is a help-grub mailing list.
[https://lists.gnu.org/mailman/listinfo/help-grub](https://lists.gnu.org/mailman/listinfo/help-grub)

---


---
title: "cancelled lubuntu install wiped operating system"
date: 2020-08-14
forum: Windows
---

### Post by tomato1232 on 2020-08-14
I wanted to test newest lubuntu on my machine and booted it from usb. I didn't found the option to test and cancelled installation after choosing language and keyboard layout.
Tried to remove usb stick and launch to my installed windows, but there is "no operating system" error on launch.

How to fix this and recover my files?

---

### Post by fragglebliss on 2020-08-14
Sounds like you've commenced an installation of Linux over the top of an existing Windows operating system. By cancelling the installation partial way through you have left the system with an incomplete booting operating system. You're most likely going to require a complete reinstall of a new operating system, whichever option you choose (Windows/Linux) is up to you.

---

### Post by tomato1232 on 2020-08-14
Is there a way to rescue my files (photos dociments etc) before install?

---

### Post by fragglebliss on 2020-08-14
> **tomato1232 said:**
> Is there a way to rescue my files (photos dociments etc) before install?

By restoring your backup before the new installation attempt.

---

### Post by fragglebliss on 2020-08-14
Need a bit more information as to what hard disk/partition configuration you selected when you attempted to install Linux.

---

### Post by tomato1232 on 2020-08-14
I didn't choose any partition, cancelled installation right after selecting keyboard layout

---

### Post by tomato1232 on 2020-08-14
I also haven't prepare any backups cause I didn't know that the installation would take place right after booting from usb. Is it possible to rescue data by using data rescue program through other machine?

---

### Post by fragglebliss on 2020-08-14
Possibly. Still, what you're saying doesn't seem to make much sense to me. Does your Windows instance have a recovery partition on the disk? Also, it might be possible booting into Linux live mode and trying to mount the drive. That way you can copy the files you want in live mode to a new safe place.

---

### Post by CelticWarrior on 2020-08-14
"Try Lubuntu" in the first menu is the option to test / run a live session. If you didn't see this menu then I wonder where did you get the installation ISO from and/or how did you burn it in the USB stick.

**Backups are something to have regardless of anything else. **So, hopefully, lesson learned by now. The reason for having current backups is that any OS can fail at any moment. The drive where it is installed can also fail. So, not having backups is NOT AN OPTION.

Atb this point however, and as already commented, we need more details. And to get those details you need a proper live session. Please make sure you download the ISO file from the official website lubuntu.me and use any available tool to "burn" it to the USB stick. You may need another computer for that probably.

---

### Post by tomato1232 on 2020-08-14
Ok so I just started live ubuntu from CD and looked up my partitions. It does look like nothing has changed since my "lubuntu problem".
I will now make backup of every partition to my external disk and attempt to fix no operating system detection, but at this time I don't know how to fix it without just reinstalling that lubuntu or windows.

---

### Post by guiverc on 2020-08-14
Question also asked at [https://askubuntu.com/questions/1267105/cancelled-lubuntu-install-wiped-windows-system](https://askubuntu.com/questions/1267105/cancelled-lubuntu-install-wiped-windows-system)

---

### Post by tomato1232 on 2020-08-14
So I have SONYSYS partition with EFI files(273mb) , windows recovery environment(1.5gb), EFI filesystem(273mb), microsoft reserved, basic data, another two windows recovery environment partitions (1gb and 32gb)
Is one of the partitions damaged so I cannot boot from harddisk OS or just my settings messed up? At this point I have no clue on fixing windows boot

---

### Post by CelticWarrior on 2020-08-14
Exactly which option did you chose for installation? "Erase and install..." or "install alongside" or "something else"?

The latter is very unlikely because that requires some knowledge about partitions.
If "Erase and install..." had been chosen and the installation actually started, you wouldn't have now the partitioning layout you comment above.
"Install alongside" would've tried to shrink the Windows system partition and install Lubuntu in the resulting unallocated space. In this case forcefully stopping the installation would have very bad results.

---

### Post by fragglebliss on 2020-08-14
Since this problem seem to be related to a Windows OS, I'm out.

I'm here to help with Ubuntu and Linux problems, not Windows OS. Mods should probably move this to a more appropriate thread.

---

### Post by Impavidus on 2020-08-15
It could also be an UEFI problem. You set the boot order to boot from DVD to run the live disk, now the UEFI no longer wants to boot from the hard drive. If that's the problem, it shouldn't be too hard to fix, but very hardware specific.

---

### Post by oldfred on 2020-08-15
Since all Windows issues, moved to Windows sub-forum.

Boot your Windows repair flash drive and run Windows repairs. You may need chkdsk more than once on all NTFS & FAT32 partitions.
And you may need to run the full set of commands to repair boot.

---

### Post by burbigo3 on 2020-08-15
What do you mean by needing chkdsk more than once ?

---

### Post by oldfred on 2020-08-15
Some have posted that chkdsk does not always fix everything on one pass. So you have to run it more than once.

---


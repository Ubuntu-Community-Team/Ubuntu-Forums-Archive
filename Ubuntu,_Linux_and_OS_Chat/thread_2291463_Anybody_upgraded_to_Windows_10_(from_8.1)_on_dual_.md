---
title: "Anybody upgraded to Windows 10 (from 8.1) on dual boot installation?"
date: 2015-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2015-08-20
I am looking for upgrading my Windows 8.1 to Windows 10 which has multi boot with Ubuntu 14.04, Debian 8.1 amd Ubuntu 15.04. I am afraid that Windows 10 might write to boot/efi partition making it difficult to boot the other Linux OS.

I would like to have feedback before upgrading.

Kamalakar

---

### Post by oldfred on 2015-08-20
Good backups are always recommended.
But you can and should just backup the ESP - efi system partition. It is not large and easy to restore if need be.

A few have posted that halfway thru Windows upgrade it failed. So you need the Windows backup to restore it.
Those with MBR/BIOS systems often have the issue where Windows does not rewrite MBR partition table with the Linux logical partition. Best to have partition table backup if MBR. Does not seem to be an issue with UEFI/gpt.

---

### Post by buzzingrobot on 2015-08-20
In the initial flurry of upgrades on and after 29 July, network congestion seemed to be causing problems for some users. There's a lot of stuff that needs to be pulled down.

You will upgrade into the same version you have in 8.1.  If it's Home, updates are mandatory and automatic. But, still, check for updates after you reboot when the install completes, just to be sure you get off to a good start.  Microsoft has released 3, I think, Cumulative Updates and one important security patch for IE.  Updates to Windows Defender -- new definitions -- are very frequent.

That privacy thing:  During the install, you will be asked how you want to configure your settings.  The default response is "Express".  That enables everything.  Down in the corner of that screen you will see a "Custom" button.  That takes you through several pages of options, privacy related and otherwise, that you can adjust. Everything can be adjusted in Settings later, even if you select the "Express Option".

The Mail app is buggy for many people:  downloading/syncing problems. Be sure that, in Settings, you have set Mail and Calendar as Background apps and that you have allowed Calendar to be accessed by other apps. (As with Evolution in Linux, calendaring and mail services are pretty much one thing on the back end here.)

I think Edge is a pretty good browser, and safer than IE.  But, it doesn't have an extension feature yet.  Coming later, apparently.

---

### Post by kagashe on 2015-08-21
> **oldfred said:**
> Good backups are always recommended.
But you can and should just backup the ESP - efi system partition. It is not large and easy to restore if need be.
Actually I have two partitions:
/dev/sda2 fat32 Label=SYSTEM_DRV Size=260 MB Used=37.25 MB Flags=boot,hidden which is mounted by Ubuntu at /boot/efi
/dev/sda3 fat32 Labei=LRS_ESP     Size=1000 MB Used=505.37 MB Flags=hidden which I can mount at /media/user/LRS_ESP

/dev/sda3 also has OneKey recovery folder for Windows apart from Boot and EFI folders
/dev/sda2 has BOOT and EFI folders

Kamalakar

---

### Post by makitso on 2015-08-21
I had no problem with my dual boot Win8/Ubuntu 14.04 EFI system.

---

### Post by oldfred on 2015-08-21
The FAT32 hidden partition, I believe holds efi boot files for system recovery or other vendor configurations. Not sure how they switch or if from UEFI you can use another FAT32 as efi. 

Some vendors put all the vendor efi type files in the main efi partition. And Boot-Repair would often add then all to grub making a very large grub menu.

With my new Dell last Dec, Windows 8 wanted a recovery, Dell wanted a recovery  and I made a full backup of the entire system with Macrium Reflect-free. That was two flash drives and multiple DVDs. And I was not planning on using Windows, but to view Comcast or HBO I needed Windows. :(

---

### Post by rebusgadfly on 2015-08-21
don't do it. Windows 10 is so buggy and not ready for prime time. I advise you stick to what you have.

---


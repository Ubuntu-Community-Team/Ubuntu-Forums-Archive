---
title: "Lenovo desktop computer won't boot Windows or go into BIOS"
date: 2015-12-17
forum: Windows
---

### Post by KayeNg on 2015-12-17
Hello guys.  

We have a relatively new Lenovo branded desktop computer (bought last year) that was pre-installed with Windows 8 (or 8.1).  Merely a couple of months into it, the OS got buggy.  It was still usable so we ignored it.  After a full year of using it, it worsened and was not able to boot.  

I'm not sure about this because I'm not the one using it, but some newer computers don't show the "Press F2 to enter BIOS)", right? It goes straight to Windows? So now I can't boot Windows--I get a message like some file is missing or corrupted--and I can't get to BIOS where I can change the boot sequence (I tried pressing F1 to F12 upon starting the computer, nothing happens).

What now? If I have a Windows 8 disc, would the computer automatically boot it first?  (I don't have the disc yet, because the Windows OS was pre-installed)

Thanks guys!

---

### Post by howefield on 2015-12-17
Thread moved to the "*Windows*" forum.

What is the model ?

[https://support.lenovo.com/gb/en/documents/yast-3jwkjx](https://support.lenovo.com/gb/en/documents/yast-3jwkjx)

---

### Post by KayeNg on 2015-12-19
Hello howefield, thanks, it wasn't in that least but I got lucky with pressing F1.  Looking at the sticker on the side of the desktop, I think it says H530.

Anyway, I can get to BIOS now, but it looks like legacy bios instead of UEFI ? I've managed to boot my Live lubuntu usb, though. 

Now I have a new problem.  I tried creating a partition for Lubuntu and another for swap.  They are positioned near the end (or near the right end), if you look at the partitions in Gparted.  During installation, I chose dev/sda as the "device for boot loader installation" .  Restarted the computer, it did not detect the lubuntu OS.  Only the windows OS, which is corrupted and cannot boot.

Then I figured I want a clean install of everything; I want a dual boot system of windows 8 and lubuntu.  I boot the lubuntu live usb, used gparted to wipe everything in hard disk, then set it up like so:

|       windows os       |                        data                        |     lubuntu     |   swap   |

The windows partition is still empty as I don't have a windows disc yet.  I proceed to install lubuntu in the ext4 partition.  "device for boot loader installation" was set to /dev/sda/
Reboot.  I got a black screen saying something which I forgot (the desktop is far away from me now, I'll get to see it couple days from now).  It either said it cannot find os or boot loader or something.  not sure. sorry.

The hard disk is GPT by the way.

What do I do now? Should I repost this in the Installation & Upgrades forum?

---

### Post by howefield on 2015-12-19
> **KayeNg said:**
> What do I do now? Should I repost this in the Installation & Upgrades forum?

Yes, do that with as much info as you can including the hardware specifications.

PS. You'll most likely have another problem if you install Windows after Lubuntu in that Windows will wipe out the grub loader.

---

### Post by KayeNg on 2015-12-19
I've dealt with the grub loader problem before in other desktops, I believe it's a simple fix.  I'll repost in the other forum.  Thanks for your time.

---


---
title: "SATA hotswap feature not working on ROG STRIX Z390-F Gaming board in Pop!_ 20.04"
date: 2020-05-21
forum: Ubuntu/Debian BASED
---

### Post by jasoncollege24 on 2020-05-21
I'm a bit of a linux newbie, using Pop!_OS, and having an issue that I can't figure out. Every Pop!_os related forum, and chat where I've presented this problem, no one could advise me, and could only tell me they didn't have any experience with SATA hot swap.


An SATA port on my board that has hotswap enabled in the UEFI acts like it's not swappable, never shows as a removable device, always shows corrupted partition tables/disks, when in Pop, and never shows a properly working disk. The attached device is an SATA Hot Swap bay, and works normally in Windows. board is a ROG Strix Z390-F Gaming Motherboard, and I'm using kde on Pop!_OS 20.04, but same issues in pop's default DE.


a GPT formatted disk was recently tried, but showed a corrupted partition table. When i tried using testdisk on it, it told me it saw a MSDOS partition table that was corrupted. I immediately pulled the disk, and placed it into a USB swap caddy. The disk worked, and all partitions were usable as expected.


This feature works perfectly in Windows. Is it possible this board is just too new, and I'd be better off just going back to Windows for now? I use the device a LOT, so not having it for use will make me fall back to Windows. As a reference, I just upgraded from a 5 year old gigabyte board, which had the same feature, and worked flawlessly in Pop!_OS.

This is a fresh, clean install. I didn't carry over my home directory, or any config files.

---

### Post by TheFu on 2020-05-21
Hot-swap means that an unused storage device can be disconnected or inserted. I've never tried it with SATA connections, but I have used it with eSATA connected storage.

How-swap isn't magic.  It still requires that the storage be mounted and umounted.  I wouldn't trust any GUI tool to manage this.

Corrupted partition tables and corrupted file system are a completely different issue. Those need to be solved. Being usable and being consistent are different. Did you run validations like fsck and check the smart data?

I'm suspecting the BIOS settings are wrong for those devices.  Is AHCI enabled as usually required for Linux?  RAID and IDE BIOS settings are to be avoided.

---

### Post by jasoncollege24 on 2020-05-21
I think you're misunderstanding...

The motherboard is designed this way. I know the disk would still need to be mounted/dismounted. Mounting/unmounting is not the issue here.
This setting turns the designated SATA port into a hot swappable SATA port by design, and the feature is at minimum 5 years old (My previous board is that old). In Windows, any disk inserted is seen as a removable device, and shows up in the list of removable storage devices, with a safely remove option. This tells me that the setting is working for the OS it was designed for.

On my previous board, (Gigabyte GA-Z97-D3H), it had exactly the same feature. When hot swap was enabled in the UEFI, Pop! would see any inserted disk as a removable device, treating it accordingly. On this board, Pop! sees any item in the swap bay as an internal drive, but always with corruption.

As per your questions about the partition tables, the disks are not actually corrupted. Removing the disk from the SATA swap bay, and placing it into a USB swap bay, without any attempt to solve the corruption makes the disk work perfectly, with no corruption seen. (I did mention this) This is not a problem with the disk, but with how Linux is seeing this feature of the board. There is nothing wrong with the actual disk.

Raid is disabled, as I never use it. All SATA stuff is set to AHCI, and there are no IDE based settings, or even a place/way to add IDE devices. The system is also set to disallow legacy BIOS features. CSM is enabled to allow POST info to go to my primary display. This setting was changed after my first attempt to use the hot swap bay in Linux, and made no difference in the issue, so that's not the cause either, just to rule that out. :)

---

### Post by TheFu on 2020-05-21
The GUI shouldn't have anything to do with this.  If you run the CLI versions of the commands, that could provide more output that GUI tools hide, if they bother displaying anything.

Lots of things to try in this link: 
[https://serverfault.com/questions/5336/how-do-i-make-linux-recognize-a-new-sata-dev-sda-drive-i-hot-swapped-in-without](https://serverfault.com/questions/5336/how-do-i-make-linux-recognize-a-new-sata-dev-sda-drive-i-hot-swapped-in-without)
[https://askubuntu.com/questions/989410/whats-the-proper-way-to-disconnect-hot-swap-sata-hard-drive](https://askubuntu.com/questions/989410/whats-the-proper-way-to-disconnect-hot-swap-sata-hard-drive) sudodus' answer seems reasonable.

---


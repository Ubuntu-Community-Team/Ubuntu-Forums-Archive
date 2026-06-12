---
title: "Move-Copy changing how it works"
date: 2018-11-03
forum: Ubuntu/Debian BASED
---

### Post by ellinas.mar91 on 2018-11-03
Hello,
Recently i try to move something from my external Hdd to Usb device, and i noticed that the move-copy works very differently from Mac or Windows.
The Progress bar is not real time neither is indicating a correct percentage of how much is remaining to complete the task, after some digging i think i understand why, it seems that when i initiate a copy to an external drive for example the file firstly go to buffer memory and after is transferred from buffer to the actual location that is supposed to be.

My Questions are:

How i can make the move-copy progress real-time.
Also i don't understand the use of buffer memory it wouldn't be better and faster to transfer directly to the new location.   

i want to make it behave like Mac or Windows not because i like them better but because the way Ubuntu Copy-Move functions work doesn't seem ok.

Thank you

---

### Post by TheFu on 2018-11-03
Welcome to the forums.

Doubt I have the answer you seek, but perhaps some explanation will be helpful.

Using buffers speeds up the transfers for small files since RAM is 100,000x faster than storage. 
* storage is slow
* networking is next slowest (usually)
* RAM is fastest

Windows and Mac both use buffers in the same way unless you setup USB storage to be "quick remove".  I've never looked for that option on Linux. Maybe it exists? IDK.  Regardless, the target disk is being written as quickly as possible, but since reading data is faster than writing it, the use of buffering (in RAM) will let the copy/move appear to finish faster than it actually does.  So, if you are moving a file off 1 disk, then the storage space will be freed before the total file has been written to the target disk.  Pretty much everyone in the world agrees this is a good thing.

If you want transfers to be faster, don't use FUSE file systems (like vfat/exfat/NTFS) and don't use GVFS. GVFS is almost always used when a GUI is involved in the mount. The performance hit for those can be 10-40% slower.  Both of those systems are known to be slower than native Linux mounts and native Linux file systems like xfs, ext4, and similar.  That is because the Linux file systems run in the kernel and use "real" mounts.

Why do FUSE and GVFS even exist?  Because they are flexible and easy, but the cost is performance.  FUSE makes it easy to create a userland (non-kernel) file system and make it easily available to the world.  GVFS is part of Gnome and makes graphical mounting of storage easier than using the core mount command or going through the fstab.  Both of these are historically how Unix systems mount storage and have been optimized for performance with Linux file systems.

As for the GUI aspects, those aren't part of the OS. They are just a GUI.  Try different GUI programs if altering the progress is really that important.  Or if you want the fastest move/copy possible, use a shell/terminal and skip the GUI completely.  You can easily test my claims and see for yourself if I'm correct or not.

If you really want to get the best possible performance, with Linux you can turn the parameters for every disk and every buffer.  A little googling should bring up some techniques that use **hdparm**, **bonnie++** and a few other tools to optimize the throughput for your specific system and files.  This is usually beyond something a beginner would do, but it is possible.

Using different control channels between disks should also improve performance.  Usually this is seen where there are 2 USB connected disks and a move/copy is happening between them.  If they are on the same controller, then that single controller limits the amount of throughput.  But if the disks are on different controllers, then it is the PCI bus which would be the limiting factor.

I've seen that FUSE is getting some much needed performance improvements in the newest kernel merge. [https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.20-FUSE](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.20-FUSE)

Having access to this level of control is part of what makes Linux so fantastic.

Lastly, expecting Linux to behave like Windows will just leave you frustrated.  There are huge differences in the philosophies for the OSes, which are part of the reasoning why Unix-like systems work differently.

---

### Post by TheFu on 2018-12-05
I forgot, but when you use a GUI to "move" a file, some of those GUIs will also copy the file into the "Trash".  That could create 2 full copies depending on the number of separate file systems involved.  If you do the move from the CLI/shell, that extra work will not happen, unless you create a tiny script to manually do it.

---


---
title: "Cannot boot into windows 7"
date: 2016-01-24
forum: Windows
---

### Post by KayeNg on 2016-01-24
Hi guys.  I have this dual boot system that was working great.  

Originally, I made the windows 7 system WITHOUT the 100mb system reserved partition.  Both windows and lubuntu were working fine for the longest time.

Then sometime after, the windows system got corrupted.  I decided to reformat and reinstall the windows system, but this time just allowing the windows to automatically set the 100mb system reserved partition.  (that means this time my sdb1 partition is the 100mb partition.)

After installing the windows thru the dvd install media, the grub was gone, but that isn't the problem as I know how to get it back.  The problem is windows won't boot.  

I get this message:

> error: no such device: 2C6097746097438C.
Setting partition type to 0xb

Press any key to continue...

Believe me I've tried everything, from using the commands in (windows) diskpart (/fixmbr etc.) , to using boot-repair.  Nothing works.

I'm not really sure but I think I've encountered this problem before in another computer; I may have fixed it using the windows command "clean" or "clean all".

1.  I'm ok with using clean or clean all to completely wipe the drive, but I wonder if there's a linux equivalent?

2.  Or can you suggest something a little less destructive?

3.  Yesterday while in Lubuntu, I used gparted to delete sdb1 (windows system reserved 100MB) and sdb2 (windows os partition), then boot the windows dvd install media, then the install media automatically detected the sdb2 partition for installation;  I let it install.   Still cannot boot.  I get a black screen with two options, to start normally, and to attempt repair.  Neither works.

Maybe "clean all" command is in order? (although I would like to try a linux version of that, if there is one.)

By the way, there's another hard drive, sda.  If it matters.

Thanks a lot

---

### Post by Bucky Ball on 2016-01-24
*Thread moved to **Windows**.*

Probably better to ask this in a Windows forum and the ***Cafe*** is not a support area. ;)

---

### Post by yancek on 2016-01-24
The error you posted in your first post; error:no such device shows a UUID after it.  Since you re-installed windows, it created a new UUID for that partition and the one shown in the error message is the old one which is also the one which is in the /boot/grub/grub.cfg file.  Boot Ubuntu and run the command:  sudo blkid  and check the output for the partition on which windows is installed and put the new UUID for that partition in the grub.cfg file, save the file and do not run update-grub and re-boot to test.  It might work to just run sudo update-grub.  It would be helpful if you posted the output of the boot repair script.

---


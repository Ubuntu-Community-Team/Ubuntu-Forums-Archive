---
title: "Windows doesn't detect HD, Ubuntu does"
date: 2015-02-06
forum: Windows
---

### Post by jackly2 on 2015-02-06
Hi,
I've got a single HD in my laptop with multiple partitions:

/dev/sda1 = ext4
/dev/sda3 = ntfs
/dev/sda5 = swap

Now Ubuntu (and gparted etc) detect this HD fine (and Ubuntu is installed on the ext4). But Windows doesn't even boot. I tried using a DVD to install Windows, but the Win Installer doesn't detect the HDD either, it just says there are no HDDs. So it's not a hardware issue, but I'm not sure what's going on here. Any one got any insight?

---

### Post by buzzingrobot on 2015-02-07
Going by distant memory. Windows doesn't know about Linux file systems like ext4 and, I think, Linux bootloaders.  I believe it expects either an empty unpartitioned drive or a drive with Windows partitions.

If you need to replace Ubuntu with Windows, I'd try using Gparted to delete all the partitions, then reboot into the Windows DVD.

---

### Post by jackly2 on 2015-02-07
The thing is, I have an NTFS partition there, so it should be at least detecting that. Instead, it detects absolutely nothing. If I boot the Win Installer with the HD unplugged, it's the exact same thing as though it were plugged in. It should detect SOMETHING right? At first I thought the HD was faulty, no problem. But then I accidentally had the Ubuntu DVD inside and it ran and installed perfectly!

---

### Post by yancek on 2015-02-08
Which version of windows are you trying to install and have you tried booting it on another computer?

---

### Post by jackly2 on 2015-02-08
I'm trying to install 7, though I've tried 10 TP as well. They've  installed perfectly (using the same DVD) on a different laptop, so it's  definitely something with this laptop. Like I said, I thought it was  hardware-related until Ubuntu worked perfectly... 

Ha I think this guy once had this same issue - [http://ubuntuforums.org/showthread.php?t=1902679](http://ubuntuforums.org/showthread.php?t=1902679)

---


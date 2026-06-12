---
title: "Boot Repair help"
date: 2015-08-09
forum: Windows
---

### Post by dave191 on 2015-08-09
OK, I had Win 7 and Mint dual booting on my Dell laptop.  My HP laptop died after upgrading win 7 to win 10.  I then installed win 8, upgraded to 8.1, updated until I got the invite to win 10 and installed (Upgraded) on the Dell.  Needless to say, it now dual boots with windows menu to win 10 or win 7.  Grub is gone and I wanted to try Boot Repair to fix it..  Boot repair seems to want to load the old dual boot grub with win 7 and Mint. I want three choices, win 7, win 10 and Mint.  Will the windows boot menu show up if I choose win 7?  Here is the link to the Boot Repair info summary:

[URL="http://paste.ubuntu.com/12044057"]http://paste.ubuntu.com/12044057

[/URL]

---

### Post by oldfred on 2015-08-10
Moved to Windows sub-forum.

Yes, Windows only boots from the drive set in BIOS as boot, then from the primary NTFS formatted partition with the boot flag. Any newer installs of Windows overwrite boot files in the boot partition and add the original install to the BCD.  Second install has no boot files of its own.

If you had installed your second copy of Windows to a primary partition you could have made it directly bootable from grub. But Windows only directly boots from primary partitions. So never delete the sda2 Windows boot partition as it is for booting both Windows.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

Boot-Repair can really only fix Linux issues and a few minor Window issues like MBR. You really need to always have a current version repairCD or flash drive for every system you have installed. Or you need 3 bootable repair or live installers. New Windows may work on older Windows, not not vice-versa.

---

### Post by dave191 on 2015-08-10
Interesting reading... thx for the links.  I'm glad I did not let Boot Repair make changes tho I could have restored the systems.  Not sure which Windows I will keep.  I would still like to boot to the Linux system also... but the Boot Repair question is answered...

---


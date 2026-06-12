---
title: "Have Win7, Win Xp, and Mate 16, Grub can't see xp"
date: 2014-03-02
forum: Windows
---

### Post by konungursvia on 2014-03-02
I bought a new 1TB laptop hdd yesterday, added windows 7, then used gparted to make an 18 Gb partition for xp, and about 44 Gb for Linux Mate 16.

I installed xp, then installed Mate, so I have 3 os's on there.

At first, GRUB2 had Windows 7 listed, but it booted only into xp. So I ran the Win7 recovery disk, fixed the MBR, and now GRUB2 has Windows 7 listed and it boots directly into Win 7 when selected. Linux boots fine when selected too.

But I can't seem to get Grub or Win7 bootloader to list the Xp partition as a bootable os choice. Here's my info.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x74644f1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1819961676   909877414+   7  HPFS/NTFS/exFAT
/dev/sda3      1819971718  1953523711    66775997    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5      1819971720  1855218329    17623305    7  HPFS/NTFS/exFAT
/dev/sda6      1855219712  1953523711    49152000   83  Linux

Any ideas?

---

### Post by oldfred on 2014-03-02
Moved to other OS since not Ubuntu.

Is XP sda2 or sda5?

And only since XP it may be possible to boot from grub when in logical, but better to be primary. 
Windows only boots from a primary NTFS partition with the boot flag.
Second instals of Windows do not have any boot files but are added to the first install. Newer versions include old version in BCD, not sure when installing XP second how that may work. You probably had to run an update to get Windows 7's BCD to add XP.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Since already installed you may be able to run repairs if both are primary partitions.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by konungursvia on 2014-03-02
Xp is in sda5... My other laptop hdd triple boots okay, can't remember how I got that to work, probably installed things in a different order. Ideally, I would like to manually add a winxp entry in grub-customizer, or, go into windows 7 and edit the mbr from there, if I had good advice on how either way.

---

### Post by konungursvia on 2014-03-02
I might try this next:
[http://superuser.com/questions/305764/how-to-dual-boot-when-windows-xp-was-installed-after-windows-7](http://superuser.com/questions/305764/how-to-dual-boot-when-windows-xp-was-installed-after-windows-7)

---

### Post by oldfred on 2014-03-02
I do not know if PBR or partition boot sector in your XP install is correct. Windows just does not like logical partitions to boot from.
But you should be able to move the XP boot files to the sda5 partition, edit boot.ini to be the 5th partition and see if grub will boot it directly.

       Boot WinXP from extended partition - See posts by Herman
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
Boot Windows 7 logical maybe? Posts by Herman
[http://ubuntuforums.org/showthread.php?t=2104540](http://ubuntuforums.org/showthread.php?t=2104540)

   How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

You do know XP will not be supported after April?

---


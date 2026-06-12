---
title: "Add existing Windows 7 from non-first partition"
date: 2017-02-13
forum: Windows
---

### Post by norgorn on 2017-02-13
I had single HDD with Windows7 (which is still working and I can load that OS).
The idea was to split new SSD into two parts - for Linux and Windows and move old windows to SSD (there is enough space in windows partition on SSD). But that's were I made a stupid mistake and didn't read dual-boot manual. Windows must be in the first partition. And it isn't in my case.
I've used ddrescue to copy windows into its new partition and the files are fine.

Now, fdisk -l looks like this
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         2048 218750975 218748928 104,3G 83 Linux                                <- This system loads perfectly
/dev/sdb2       218753022 468860927 250107906 119,3G  5 Extended
/dev/sdb5       218753024 234375167  15622144   7,5G 82 Linux swap / Solaris
/dev/sdb6       234377216 468860927 234483712 111,8G  7 HPFS/NTFS/exFAT           <- This is new windows, dd from an old one


Disk /dev/sdc: 596,2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x054d054c

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdc1  *         2048     718847     716800   350M  7 HPFS/NTFS/exFAT                               <- This is an old windows and it also works
/dev/sdc2          718848  164558847  163840000  78,1G  7 HPFS/NTFS/exFAT                         <- These are windows main files, wanted to simply move 'em
/dev/sdc3       164558848 1250260991 1085702144 517,7G  7 HPFS/NTFS/exFAT


Obviously, update-grub cannot find the new Windows system (there is even no loader for it).


Is there any way to make Windows working from it's new partition on SSD without totally reinstalling everything?
Or the only way to accomplish this setup is to recreate all partitions, ddrescue old windows to the first partition, copy windows loader and install linux into what's left?

---

### Post by howefield on 2017-02-13
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2017-02-13
> Windows must be in the first partition. And it isn't in my case.

No, it doesn't have to be on the first partition.  It does need it's boot files on a primary partition marked active.  In your case, that would be sdb1 so for the system you have on sdb6 which is a logical partition, you would need to boot it from sdb1.  Modify with bcdedit from the windows on sdb1 to add sdb6 windows.  That 'might' work.  Are all of these different windows versions or are they all different licensed windows 7 installs?

---

### Post by oldfred on 2017-02-14
Unless your original install was sda6 with same start sector, I do not see how it will work anyway. Windows PBR partition boot sector has embedded info for booting & partition start & size. 
Perhaps adding a primary NTFS partition as sdb3 with a boot flag & the Windows boot files.
And running chkdsk on the sdb6 partition.

But Windows really likes primary partitions.

 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)

---


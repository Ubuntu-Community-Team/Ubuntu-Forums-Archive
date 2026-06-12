---
title: "How do I install a 3TB HDD with 4K sectors in ubuntu server?"
date: 2013-01-03
forum: Server Platforms
---

### Post by rs2k on 2013-01-03
I tried to use instruction like these but could only figure out how to set it up with 512b sectors. The drive I have uses 4K sectors and I'm pretty sure setting it up with 512b sectors will utterly destroy performance.

[http://icesquare.com/wordpress/how-to-install-a-3tb-drive-on-linux/](http://icesquare.com/wordpress/how-to-install-a-3tb-drive-on-linux/)

---

### Post by darkod on 2013-01-04
So where exactly did you got stuck?

In that tutorial parted is not touching the sector size at all. And ignore the comments, some of them are very wrong.

Most of the 4k disks have a physical sector size of 4096 bytes so that 3TB can fit on the plates, but they still have 512B logical sector size for compatibility with OSs that expect one sector to be 512B. That's why when you use the print command in parted to print the details, is says sector size logical/physical 512B/4096B. That's normal.

This "conversion" is done by the intelligence on the disk itself, and it's normal. It's how it should work.

If you can't see the whole 3TB first check in BIOS that it's not limiting the disk size. Maybe you need bios update to support the disk.

Also in that tutorial the guy used parted to create partition starting from 0 which is a mistake. These days you need to start the first parttion on sector 2048 which is equivalent to 1MiB so that the partitions on the disk are aligned for optimal performance.

So, rather than what that guy did in parted, change the unit to MiB, print the disk details which will also print the disk size in MiB, and create the partition (if you only want single partition) starting from 1MiB and ending at the last MiB (or one before the last).

For example, a 3TB disk should have in reality something like 2,861,022 MiB. So creating a single partition spanning the whole disk on a disk device called /dev/sdX would be like (replace the X with the correct letter):
```
sudo parted /dev/sdX
unit MiB
mklabel gpt
print (to see the total size in MiB)
mkpart primary 1 2861022
quit
```

If the disk size is few MiB more or less than 2861022 adjust the ending location.

That's it. After that create the filesystem you want on the partition.

---

### Post by rs2k on 2013-01-04
Thanks for the help! I was ale to get through it, but I didn't want to get stuck with a slow drive. I've read running a 4k sector drive at 512b could potentially slow performance. I'll make the changes you've suggested then check how quickly the drive works.

---

### Post by Wim Sturkenboom on 2013-01-04
This might be an interesting read: [https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

---

### Post by Vegan on 2013-01-04
I suggest using a UEFI based system board if you want to use disks bigger than 2 TB. This way the BIOS will be able to boot it up.

Ignore the 4K sector, ext4 etc generally do not use 512 byte allocation units anyway.

When I last installed a linux like that it worked fine. I used the 64 bit version mind you as the 32-bit one has the short word problem.

---


---
title: "Grub on multiple drives"
date: 2010-06-06
forum: Server Platforms
---

### Post by awacs on 2010-06-06
(tangent to my other thread "Karmic -> Lucid not booting"). I have four hard drives on a Lucid box, and (as it happens) the fourth drive is the boot and root. Could I also install grub on the other three (ext4) hard drives, keeping the same root? Will this disturb the data there? How would the machine decide which copy to use, anyway?

Thanks!

---

### Post by oldfred on 2010-06-07
You can but it does not add anything. The MBR or master boot record is the first sector of the hard drive, it is not part of any partition.

Computers based on the MBR partitioning scheme boot from the primary master. The old IDE standard had primary and secondary channels and master and slave drives for a total of 4 drives. Now with SATA you can have more drives and the first to boot (still often called primary master) is set in BIOS. The BIOS starts boot and turns it over to the MBR of the primary master. That used to be large enough to do something but now it just jumps to files elsewhere on the drive.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by awacs on 2010-06-07
Oh,ok - thanks.

---


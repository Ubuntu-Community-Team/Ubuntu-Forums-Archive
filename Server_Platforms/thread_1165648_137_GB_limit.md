---
title: "137 GB limit"
date: 2009-05-20
forum: Server Platforms
---

### Post by Vegan on 2009-05-20
Can 9.04 get around the 137 GB LBA24 disk limits. My web server disk failed and new disks are > 137 GB.

---

### Post by cariboo on 2009-05-20
I've got a 120Gb, 320Gb 2X400Gb and 750Gb disks connected to my server with zero problems.

---

### Post by geirha on 2009-05-20
If the IDE-controller has a proper linux driver, then there should be no problems. If it's SATA drives, there's no 137GB limit.

---

### Post by kustomjs on 2009-05-20
it could be also your bios limit you probley have to reflash your bios.

what kind is the motherboard and specs of it?

---

### Post by Vegan on 2009-05-21
I tried a 500 GB disk and it showed up as 137 GB, there is no new BIOS.

---

### Post by Wiebelhaus on 2009-05-21
BIOS update is always top priority.

---

### Post by kustomjs on 2009-05-21
then it sounds like you cant use 500gb on your motherboard and if there is no bios update then your SOL.

---

### Post by Vegan on 2009-05-21
Windows can see the disk, how it works is you make a tiny partition for the OS and make a second partition for the rest of the disk.

Linux uses more partitions than Windows does so hence my inquiry.

I ranted at IBM for a BIOS or the source so I could add LBA48 and LBA64 to it.

I was thinking that Grub could be leveraged to some degree.

---


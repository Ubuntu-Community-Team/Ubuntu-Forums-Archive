---
title: "A question on RAID and fdisk"
date: 2010-08-31
forum: Server Platforms
---

### Post by Azdour on 2010-08-31
Hi,

I've been playing with a HP Server (with HP Embedded SATA RAID Controller RAID) with various RAID levels. I set it up with 3 HDDs. 2 are 250gb with which I created one logical drive (logical drive 1) from them with RAID 1 for mirroring. The last HDD is 500gb and I added it as logical drive (logical drive 2). So my RAID now has two logical drives.

After installing Ubuntu I ran fdisk -l thinking that I would only see two drives one with 250gb and one with 500gb. What I actually see is all three HDDs, sda (250gb), sdb (250gb) and sdc (500gb). There is an error message on sdb reporting the disk does not have a valid partition table.

Is this correct? Thanks in advance.

---


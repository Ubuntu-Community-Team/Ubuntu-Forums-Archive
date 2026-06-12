---
title: "How can I create partition table around partition image?"
date: 2013-04-04
forum: Virtualisation
---

### Post by Freek07 on 2013-04-04
I have dd dump of NTFS partition. It mounts OK (loopback), I can access it inside XEN as well.
But because it's only a partition (sda1) without partition table and MBR, I cannot make it boot (fixmbr destroys it).

So- what would be the easiest was to build partition table around this dd image so fixmbr from recovery console would make it boot? (one partition, mbr and that's it)?

---

### Post by dcstar on 2013-04-07
> **Freek07 said:**
> I have dd dump of NTFS partition. It mounts OK (loopback), I can access it inside XEN as well.
But because it's only a partition (sda1) without partition table and MBR, I cannot make it boot (fixmbr destroys it).

So- what would be the easiest was to build partition table around this dd image so fixmbr from recovery console would make it boot? (one partition, mbr and that's it)?

[LIST=1]
[*]This has nothing to do with Virtualization, which is probably why there have been no responses.
[*]Create a partition on a drive that is slightly larger than the image you have, then use dd to copy the image to that partition location.
[/LIST]

---

### Post by Freek07 on 2013-04-10
Thanks, that's what I did- I dd-ed empty file bigger than partition image, created MS DOS partition table with one primary bootable NTFS partition on it and DD-ed partition image to offset=63 (as that's where the first partition starts)- and it's working :)

---


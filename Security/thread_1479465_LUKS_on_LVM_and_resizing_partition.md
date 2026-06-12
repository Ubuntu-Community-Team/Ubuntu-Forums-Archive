---
title: "LUKS on LVM and resizing partition"
date: 2010-05-10
forum: Security
---

### Post by voidzero on 2010-05-10
Hi,

I have a LVM logical volume, that contains a LUKS encrypted volume, on which is an ext4 filesystem. I shrank the partition to the minimum size. Next step is to luksClose the device, and then to resize the LVM logical volume.

I suspect that LUKS has overhead. So if the ext4 filesystem was resized from, say 1TB to 500G, I have the idea that resizing the LVM LV to 500G does not take LUKS overhead into account and this might corrupt data on the end of the FS.

So, what's the smart move to take? How do I calculate the safe minimum LV size? Or should I just give the 500G disk a few gigabytes extra to be sure?

---

### Post by frostschutz on 2010-05-11
Two methods:

1) shrink the filesystem a bit more (x-1 GB), then resize the LVM partition (x GB), then grow the filesystem to the space that's available on the new device.

2) determine the exact size of the LUKS header, see 'cryptsetup luksDump /dev/partition', payload offset in 512byte sectors. For example if the offset is 2056 that would mean the LUKS header is 1052672 bytes. Resize your filesystem to X - size, resize LVM partition to X.

Personally I very much prefer method 1) even if it means an additional shrinking/growing operation. I feel much safer letting the OS figure out the size than doing the math myself.

---

### Post by voidzero on 2010-05-11
Ah, yes, why didn't I think of that: resize the filesystem, then resize the LVM to be a little bigger, and then grow the filesystem again. Smart thinking!

But, since I also asked my original question because it tickled my curiosity, I'm glad that you could answer that also. So thank you for both answers. You're a :KS

I was wondering about one more thing: are sectors always 512 bytes?

---

### Post by frostschutz on 2010-05-11
Not anymore, there are some HDDs around now that use 4KB sectors. However that's a very recent development.

---

### Post by voidzero on 2010-05-11
Alright. So it's always drive dependent and not filesystem dependent -- and the sector can be seen with fdisk, I just noticed. Thank you!

---


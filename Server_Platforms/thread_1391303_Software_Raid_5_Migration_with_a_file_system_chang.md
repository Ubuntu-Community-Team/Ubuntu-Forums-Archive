---
title: "Software Raid 5 Migration with a file system change"
date: 2010-01-26
forum: Server Platforms
---

### Post by sk8er3810 on 2010-01-26
Everything is software raid using mdadm
3x320GB HDDs in raid 5
1x1.5TB HDDs in raid 1(don't ask)

The above are LVMed to create ~2TB of combined space using reiserFS.  I'm not really happy with the performance so I'm moving to XFS while I'm at it.

I FINALLY got around to ordering 2 more 1.5TB HDDs.  The end goal is

3x1.5TB HDD in raid 5 formatted to XFS

for a total of around ~2.7GB of space.

1. Create raid 5 array using the new 2x1.5TB HDDs.(yes, very pointless at the moment, please continue reading)
2. Copy data from 2TB LVM to the new ~2.7TB raid 5. (will mdadm let me be an idiot? It apparently let me force create a single drive in a raid 1)
3. Move the original 1.5TB over to the new raid 5 to actually provide redundancy.

Am I missing anything?

---

### Post by BobVila on 2010-01-26
My god that looks like a scary process. Sorry I can't offer anything definitive, but I'd venture to guess that it'll let you assemble your new RAID 5 with the 2 drives, but not start it.

EDIT: After a second look, the "Create" section seems to say that I'm wrong and things could go ok for you. [http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm) 

/me hopes you're not doing this with critical data.

Best of luck!

---

### Post by fjgaude on 2010-01-27
Should work just fine, if you know what you are doing. <smile>

---

### Post by tgrimley on 2010-02-06
Should be okay, I've done this twice.  Just triple check before you execute any command :)

---

### Post by Xianath on 2010-02-07
Assuming a recent enough kernel and mdadm, you should be able to migrate from RAID1 to RAID5. I suggest you try this: add one of your 1.5TB drives to the RAID1 array as active and let it rebuild. Then add the other one as a spare. Try to reshape to RAID5 using -G -l 5 -n 3. If that doesn't work, change the spare to an active mirror and let it rebuild, then try to reshape again. Yes you will waste some time but if either of these work, you'll be much safer than with a 2-drive RAID5.

Oh, and one other piece of advice. Unless you're really short of time, run those new week through a week of intensive use including SMART long tests and raw I/O benchmarks (you may need to temporarily format them for benchmarks to work). There's nothing that hurts more than a brand new disk going bad on you. And if those 1.5T disks are green/eco ones, make sure you turn off power saving and spin-down as they really don't play well with RAID.

Cheers, and good luck.
Peter

---


---
title: "What, ext4 better than btrfs?"
date: 2009-05-01
forum: The Cafe
---

### Post by whoop on 2009-05-01
Currently ext4 is faster than the (unstable) btrfs file system: [http://www.phoronix.com/scan.php?page=article&item=btrfs_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=btrfs_benchmarks&num=1)

I was planning on using btrfs as soon as it was labeled stable, but this benchmark got me thinking.

Hope this is just temporary.

---

### Post by gnomeuser on 2009-05-01
faster != better

Aside that ext4 is production ready, performance is quite tuned. BtrFS is still being actively developed heavily, performance is not tuned. Aside that you can get better performance for certain things by enabling it's transparent compression, but that would be the same as getting your butt kicked in other areas. You have to know what you are meassuring, Phoronix for all it's nice qualities rarely have any idea what they are measuring when they do benchmarks.

---

### Post by Skripka on 2009-05-01
> **gnomeuser said:**
> faster != better

Aside that ext4 is production ready, performance is quite tuned. BtrFS is still being actively developed heavily, performance is not tuned. Aside that you can get better performance for certain things by enabling it's transparent compression, but that would be the same as getting your butt kicked in other areas. You have to know what you are meassuring, Phoronix for all it's nice qualities rarely have any idea what they are measuring when they do benchmarks.

Didn't btrfs kill one of your drives not too far back?

---

### Post by gnomeuser on 2009-05-01
> **Skripka said:**
> Didn't btrfs kill one of your drives not too far back?

No no.. I have lost drives in the past but due to hardware failure. Btrfs was the cause of partition corruption due to being unfinished, I wouldn't recommend it for average users just yet. 

One thing you should know and accept when testing developmental filesystems like btrfs is that errors will occure and failure will happen, you will lose data. 

This is not like testing ext4, ext4 is was a fairly stable filesystem all through it's development since it was based on the Ext3 codebase.

---

### Post by whoop on 2009-05-04
> **gnomeuser said:**
> faster != better
I understand that faster isn't necessarily better, but there is allot of talk about btrfs being the future successor of ext*. Btrfs surely has allot of new features up it's sleeve but speed is definitely an important part of a "better" file system. Especially if it's going to be the new mainstream file system for linux.
I'm not saying it is slow or anything, I just expected it to be faster than ext4 even in developmental stages.

---

### Post by LightB on 2009-05-04
Yes, it's not finished. Besides, who cares, at least we have more options than ext3 and a few other barely maintained fs.

---


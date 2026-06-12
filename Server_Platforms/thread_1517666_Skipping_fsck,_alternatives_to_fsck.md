---
title: "Skipping fsck, alternatives to fsck"
date: 2010-06-25
forum: Server Platforms
---

### Post by LithiumIon on 2010-06-25
Hi Everyone,

I recently installed Lucid on my Acer H340 server. I have 2 x 1TB software RAID-1 devices running. All drives are formatted ext4.
When I restarted my server fsck started running. It has now been running for close to 36 hours. 

It just shows a black screen with:

```

fsck from util-linux-ng 2.17.2
/dev/md0: clean 285892/60678144 files, 187158559/242690800 blocks

```I cannot wait any longer than this, is there any to skip this check? Pressing esc brings up some purple screen that says "ubuntu" and has some sort of loading animation which is a few small circles in a line that keep changing between red and white. 

How can I disable this check in the future? Is there some alternative tool I can run once in a while when the system is running?

Thanks.

---

### Post by mk1w86 on 2010-06-25
You can disable it by changing the number after your raid array to 0 in /etc/fstab.  However I'm not sure if it would be a good idea.

You might want to consider another file system such as JFS or XFS which do not require regular fsck checks as far as I know. ;)

---


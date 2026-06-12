---
title: "Btrfs questions"
date: 2012-02-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by undoIT on 2012-02-28
I just finished installing the latest daily build of Ubuntu 12.04 on my Macbook Air 4,2 (with pure EFI boot!!!) and I've got to say, it is awesome so far! Since this isn't my primary laptop, I decided to try out the Btrfs file system. I have a few questions:

1. How do I enable SSD mode? (I'm guessing I add "ssd" to fstab but want to make sure this is correct).
2. How do I enable trim? I selected the encrypt home folder option during installation. Normally trim would be enabled by adding "discard" to the fstab. However, it seems that the "allow_discards" option needs to be used with cryptsetup when disk encryption is used. Ubuntu uses ecryptfs. I'm confused about how to turn on trim support with the encryption method Ubuntu uses.

---

### Post by idoitprone on 2012-02-28
> **undoIT said:**
> I just finished installing the latest daily build of Ubuntu 12.04 on my Macbook Air 4,2 (with pure EFI boot!!!) and I've got to say, it is awesome so far! Since this isn't my primary laptop, I decided to try out the Btrfs file system. I have a few questions:

1. How do I enable SSD mode? (I'm guessing I add "ssd" to fstab but want to make sure this is correct).
2. How do I enable trim? I selected the encrypt home folder option during installation. Normally trim would be enabled by adding "discard" to the fstab. However, it seems that the "allow_discards" option needs to be used with cryptsetup when disk encryption is used. Ubuntu uses ecryptfs. I'm confused about how to turn on trim support with the encryption method Ubuntu uses.

I help with question 1

> cat /sys/block/sda/queue/rotational Assuming the author of the blog is correct and the drive sda is correct pathname, if it is 0 with brtfs then it says dont worry. Brtfs has detected ur ssd. or else you have to add **ssd **to /etc/fstab
[http://www.madeo.co.uk/?p=346](http://www.madeo.co.uk/?p=346)
[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

---

### Post by undoIT on 2012-03-01
Thanks! I ran the command:

```
cat /sys/block/sda/queue/rotational
```

and it returned a 0. Btrfs is correctly detecting the SSD :)

---

### Post by oldos2er on 2012-03-02
Thread moved to **Ubuntu +1 (Precise Pangolin).**

---

### Post by undoIT on 2012-03-08
I've been experiencing abnormally high CPU utilization and sporadic temporary system lockup during the process of copying a large number of files to a USB drive. Is anyone else with Btrfs seeing this?

btw, here is a recent article (march 2, 2012) benchmarking Btrfs vs EXT4 on Linux kernel 3.3:

[http://www.phoronix.com/scan.php?page=article&item=linux_33_btrfs](http://www.phoronix.com/scan.php?page=article&item=linux_33_btrfs)

I think I'm going to stick with EXT4 (except for the rolling release distros I use) until Btrfs is avaialable as default option for stable versions of Ubuntu.

---


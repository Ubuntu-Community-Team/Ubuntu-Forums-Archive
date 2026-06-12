---
title: "Make Ubuntu simultaneously unlock multiple encrypted partitions at boot"
date: 2010-07-15
forum: Security
---

### Post by Zorgoth on 2010-07-15
I installed 4 encrypted partitions (/, /var, /tmp, and swap) that are mounted at boot using the Alternate Installation Disc, and they all have the same password, but I have to type that password in 4 times when booting up.  How do I make it so I only need to type in my password once?

---

### Post by bodhi.zazen on 2010-07-15
That is what LVM is for.

You make a crypt -> format it to LVM -> make the partitions within the LVM.

While not exactly what you are asking, should give you teh general idea :

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview")

---


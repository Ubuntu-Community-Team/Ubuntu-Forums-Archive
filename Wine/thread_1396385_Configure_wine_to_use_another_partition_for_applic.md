---
title: "Configure wine to use another partition for applications?"
date: 2010-02-02
forum: Wine
---

### Post by sansa dude on 2010-02-02
I have a spare partition on my dell mini 10v and I would like to set wine up to use it to install applications too instead of my ubuntu install, is this possible? If so how? Thanks in advance!

---

### Post by asdfoo on 2010-03-12
> **sansa dude said:**
> I have a spare partition on my dell mini 10v and I would like to set wine up to use it to install applications too instead of my ubuntu install, is this possible? If so how? Thanks in advance!


It is possible, _but_ the partition needs to be formatted to a linux style partition, eg ext3fs or ext2fs.  NTFS (windows) is not supported well enough to run applications from it.

You can define additional drive letters in winecfg by pointing them to the location they map to.

---


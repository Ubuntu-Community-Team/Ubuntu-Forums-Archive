---
title: "ext2online on 10.04.1"
date: 2010-10-13
forum: Server Platforms
---

### Post by heinrichborowski on 2010-10-13
On 8.04 (ext3fs) I used ext2online to grow a root partition after extending the underlying LVM partition.

What is the supported way of achieving the same thing on 10.04 (ext4fs) ?  The command "ext2online" does not seem to be available.

---

### Post by heinrichborowski on 2010-10-14
The answer I received on [http://forum.ubuntuusers.de/topic/ext2online-auf-10-04-mit-ext4fs/](http://forum.ubuntuusers.de/topic/ext2online-auf-10-04-mit-ext4fs/) is: Use **resize2fs**.

---


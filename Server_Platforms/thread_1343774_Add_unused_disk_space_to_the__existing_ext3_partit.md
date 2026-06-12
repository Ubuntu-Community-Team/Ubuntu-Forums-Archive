---
title: "Add unused disk space to the  existing ext3 partition"
date: 2009-12-02
forum: Server Platforms
---

### Post by Johnsie on 2009-12-02
Hi,
   I want to increase the size of my ext3 partition. There is currently 10gb of unused disk space in the machine and I want to put that space to use.

How can I do this on Ubuntu Server? I dont have physical access to the machine. Can 'parted' do this? If so, how?

Thanks in advance

---

### Post by Grenage on 2009-12-02
You can do it with parted, but only if you can unmount the partition (obviously).  I'd also recommend backing up any data on the partition being resized.

---


---
title: "AIX disk cloning"
date: 2007-05-02
forum: Server Platforms
---

### Post by coobav on 2007-05-02
I was asked to perform disk clone for a company. The problem is that it is with AIX filesystem. I get a message:

There is a valid AIX label on this disk.
Unfortunately Linux cannot handle these
disks at the moment. Nevertheless some
advice:
1. fdisk will destroy its contents on write.
2. Be sure that this disk is NOT a still vital
part of a volume group. (Otherwise you may
erase the other disks as well, if unmirrored.)
3. Before deleting this physical volume be sure
to remove the disk logically from your AIX
machine. (Otherwise you become an AIXpert).

How to clone it ?

---


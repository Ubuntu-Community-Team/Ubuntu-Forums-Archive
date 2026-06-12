---
title: "NFS issue with nested mounted file system"
date: 2008-03-27
forum: Server Platforms
---

### Post by ClementMenier on 2008-03-27
Dear all,

     I have come into a little issue with NFS. I want to export with nfs a directory /data.
    This directory however contains several mount points
/data/disk1  # mount point for disk1
/data/disk2  # mount point for disk2

    However when mounting /data remotely, I don't see the contents of disk1 or disk2 (just 2 empty directories). Note that if I put files directly in /data, I can see them correctly through nfs.

     Is there any option I should give to nfs to allow nested mounted filesystem ?

Thank you very much for your help,
Clement Menier
PS : I use Ubuntu 7.10

---


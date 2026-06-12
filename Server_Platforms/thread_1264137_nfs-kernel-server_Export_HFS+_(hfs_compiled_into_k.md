---
title: "nfs-kernel-server: Export HFS+ (hfs compiled into kernel)"
date: 2009-09-11
forum: Server Platforms
---

### Post by Romey-Rome on 2009-09-11
So the word on the tubes is that in order to export HFS+ volumes with nfs-kernel-serve, HFS+ support must be compiled into the kernel, rather than a module.

So I recompiled the kernel (2.6.28 on 9.04) with HFS+ support, but I still get: 

"exportfs: Warning: /Volumes/Media does not support NFS export."

lsmod doesn't list HFS+ loaded, but I can mount & read/write to HFS volumes, so I can only conclude that it's working as expected, just can't export.

Journaling is already disabled...

I tried to be clever & symlink HFS+ folders into an ext3 export, but I was defeated (just get an empty folder). 

Any ideas?

Thanks!

---


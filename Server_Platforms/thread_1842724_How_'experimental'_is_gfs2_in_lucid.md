---
title: "How 'experimental' is gfs2 in lucid?"
date: 2011-09-12
forum: Server Platforms
---

### Post by pdwerryhouse on 2011-09-12
I notice that the gfs2-tools package in Lucid says:

> Description: global file system 2 tools (EXPERIMENTAL)
 GFS2 *MUST NOT* be used in production environment yet.

There's just one problem: the kernel, in lucid, provides a gfs2 module, but doesn't have a gfs module.

Thus, any attempt to mount a filesystem created with mkfs.gfs fails with:

```
error mounting /dev/mapper/cluster on /mnt: No such device
```

...whereas anything created with mkfs.gfs2 works fine.

I have a need to run a clustered filesystem in a production environment on two 10.04 servers; so how unstable is gfs2 on lucid likely to be?

Cheers,

Paul

---


---
title: "using tar"
date: 2009-12-27
forum: Server Platforms
---

### Post by Vegan on 2009-12-27
I was wondering, tar is an ancient program but it is still useful.

I was wondering if it can support giant tarballs now that ext4 can work with massive files.

I backup system files into a home folder which is then backed up itself in another layer.

Eventually the tarball could get a bit fluffy with all the parts.

---

### Post by ajgreeny on 2009-12-27
As I understand it, the max size of a tar file depends on the filesystem on which it is being produced or to where it is being archived.  So for an ext4 filesystem it could be huge, much bigger I suspect than anyone could sensibly work on, or with, on an ordinary PC.

---

### Post by KiLaHuRtZ on 2009-12-27
Max file size for ext4 is 16TB; max volume size is 1EB.

---


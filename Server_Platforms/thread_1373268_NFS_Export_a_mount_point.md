---
title: "NFS Export a mount point"
date: 2010-01-05
forum: Server Platforms
---

### Post by Hypnoz on 2010-01-05
When I put an NFS mount point into /etc/exports, then do exportfs -r, I see this
exportfs: Warning: /autohome does not support NFS export.

Is there a way I can pass an NFS export through one server to another that can't directly see the netapp?

EDIT: I realized based on how NFS works, this is not possible. There may have been a way I could share an NFS mount through Samba using CIFS or something, but in the end I just ended up putting an rsync into /etc/cron.hourly.

---

### Post by nasreen888 on 2010-01-07
Share a different directory on the same volume with hardlinks to the 10 datafiles.

Things will then get out of step if the 10 data files are deleted and replaced as the unlink will only affect the first directory and not the 2nd, the 2nd will still hold a copy of the old data file (shared inode), so if you replace the files you would have to remake the links.

If the files are simply modified, then the changes will be seen immediately.

So an alternative would be to hold the real files in the 2nd directory and use symbolic links in the original.
___________________________________________
[CMH Bulbs](http://www.growlightexpress.com/ceramic-metal-halide-bulbs-9/)
[wall décor for girls room](http://artcreations.com/eShop/products.asp?mcid=11&mctgy=Baby%27s+Room&scid=59&sctgy=Girls+Room)

---


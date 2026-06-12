---
title: "Problem with VmWare Shared Directories"
date: 2008-07-13
forum: Server Platforms
---

### Post by Flatron on 2008-07-13
Hi!

I've got a Ubuntu hardy server edition installed in VmWare Workstation ACE Edition 6.0.2 (the VmWare is on windows).
I installed the VmWare tools, and it appeared to work correctly, I can run the mkdir and edit any file with mcedit in the shared directory, but if I try to checkout something from svn, I got the next message:```
svn: Can't move 'xbt/misc/.svn/tmp/entries' to 'xbt/misc/.svn/entries': Permission denied

```
I created a symlink in /var/www, but if I open any php, apache doesn't run it, but sends to the browser as a download.
The fstab line:```
.host:/                 /mnt/hgfs               vmhgfs  defaults,ttl=5,gid=33,dmask=007,fmask=007     0 0

```

I used the same with the previous version of ubuntu, and that worked fine.

---

### Post by LordFarquaad on 2008-11-03
I also encounter this issue on intrepid under vmware player. In fact it looks like svn creates the entries file without write permission, then tries to move a temporary file over it. As windows does not allow to remove read-only files, it refuses to replace it with the temporary file and thus we get this error…

Did you find a workaround? This is quite annoying…

---


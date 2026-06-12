---
title: "Best filesystem for server exports"
date: 2011-01-06
forum: Server Platforms
---

### Post by MakOwner on 2011-01-06
I'm setting up a server and I have an 8 x 2TB drive array attached.
I'll be exporting this via NFS from an Ubuntu host/server.

I'll be storing a mixture of very large (4GB - 25GB) files and many small files in separate directory structures.  Think movies and music.
The movies need to stream off this thing, so priority goes to the large files.

I have configured the array in raid 5, using software raid (yes, I know about the raid 5 and drive recovery issues at 2TB.  I have backups, and I'm taking my chances...)

I was thinking about using XFS for the filesystem, but even with no data on the system at all, I can't run an xfs_check without it running out of memory.  Doesn't give me warm fuzzies.  

What would be an optimal filesystem for a 14TB volume that a low resource server can handle filesystem checks/repairs and performs satisfactorily for movie and music streaming?

---

### Post by HermanAB on 2011-01-06
Howdy,

My favourites are the old IBM JFFS and SGI XFS.  I don't get warm and fuzzy over Ext4 yet.

---

### Post by MakOwner on 2011-01-06
> **HermanAB said:**
> Howdy,

My favourites are the old IBM JFFS and SGI XFS.  I don't get warm and fuzzy over Ext4 yet.

I started with XFS, it's just that I can't see any way to check/repair the filesystem with the xfs_* tools.  About the only thin I can get to work in 4GB of memory is  "xfs_info -V".

That said, on the one system where I run xfs, I have never had an issue, but if I do, I'm just screwed and I don't like that idea.

I can't even make a test filesystem, break it and practice recovery - the tools just won't execute.

---


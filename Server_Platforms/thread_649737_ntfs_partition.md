---
title: "ntfs partition"
date: 2007-12-25
forum: Server Platforms
---

### Post by CuBone on 2007-12-25
I decided to remove xp from my home network server and I'm now installing ubuntu instead. My serever is basically a network share for mediafiles, although I have some jboss instances and a torrent client running on it to. The network share is placed on a single HD and it's formated in ntfs, the os has it's own hd. 

Is it worth the hassle to find some way to temporarily move my files (about 300 gb) to another storage just to format the disk containing the share from ntfs to ext3 or reiserfs? What's the downside if I continue to run ntfs on the drive?

---

### Post by crouton on 2008-01-03
None, thanks to the fuse filesystem and ntfs-3g.  Read/write support of NTFS filesystems.  Given that the OS itself is on it's own disk, you could leave the share disk alone entirely.  You may eventually decide to change that share's filesystem to something else depending on your situation or access methods.

---


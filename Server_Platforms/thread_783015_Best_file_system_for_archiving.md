---
title: "Best file system for archiving"
date: 2008-05-05
forum: Server Platforms
---

### Post by cleanroom on 2008-05-05
I'm installing a 250 GB hard drive into my 6.06 server and will be doing daily backups from various machines to the hard drive with rsync.  Is any file system more advantageous for this than another?

Thanks,

Cleanroom

---

### Post by kidders on 2008-05-06
Hi there,

That all depends on what you want. For instance, "more advantageous" could mean...[LIST]
[*]Better storage efficiency (in terms of disk space)
[*]Shorter write times
[*]Resistance to corruption, sudden power loss, etc.
[*]Etc...
[/LIST]

Many of the typical requirements for backup filesystems (eg good RAID performance, or the ability to handle large files) don't apply to your situation, so the choice is a less critical one. Having said that, you might for example decide to...[LIST]
[*]Choose Ext2, because dumping the filesystem journal would significantly improve performance, at the cost of reliability.
[*]Choose ReiserFS if you're planning on backing up millions of very small files, to avoid wasting disk space.
[*]Choose JFS to save time when running fsck.
[/LIST]

If you weren't using rsync, XFS might be a good choice ... depending, of course, on exactly what you're rsync-ing. Essentially, you haven't provided enough information to make any useful recommendation, but hopefully this post will give you some ideas. The best suggestion I can offer is to decide what you want to achieve, and opt for the filesystem type that gives it to you.

---


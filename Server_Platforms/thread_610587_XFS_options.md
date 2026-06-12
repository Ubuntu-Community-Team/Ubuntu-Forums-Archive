---
title: "XFS options"
date: 2007-11-12
forum: Server Platforms
---

### Post by fab4am on 2007-11-12
Hi, 

I have a 7tb XFS filesystem. The partition is supposed to stock big files between 2mo and 50mo. Quite no small files.

So i'm trying to adapt the mount option to what I need, and what I need is not performances but security. I want to be sure that NONE of the files will be lost, even if there's a power failure.
For now, I just tried the noatime mount option, but I know there is a lot of options, even if I don't really understand what they stand for.

Do you have any suggestion to make my filesystem safer ? 

Thanks

Amandine

---

### Post by kerry_s on 2007-11-12
> Do you have any suggestion to make my filesystem safer ? 

backup, backup and backup.
noatime is a performance option, if you want safer you should run it stock, with no added options. me i could care less, i backup important stuff, mine looks like this->
```
/dev/hda3       /               xfs     defaults,noatime,logbufs=8        0       0
```

checking is turned off, never found the checking useful to me.

make sure you read the man page->

```

xfs(5)                                                                  xfs(5)



NAME
       xfs - layout of the XFS filesystem

DESCRIPTION
       An  XFS filesystem can reside on a regular disk partition or on a logi-
       cal volume.  An XFS filesystem has up to three parts: a data section, a
       log  section,  and  a  realtime section.  Using the default mkfs.xfs(8)
       options, the realtime section is absent, and the log area is  contained
       within  the  data section.  The log section can be either separate from
       the data section or contained within it.  The filesystem  sections  are
       divided  into  a  certain  number of blocks, whose size is specified at
       mkfs.xfs(8) time with the -b option.

       The data section contains all the filesystem metadata (inodes, directo-
       ries, indirect blocks) as well as the user file data for ordinary (non-
       realtime) files and the log area if the log is  internal  to  the  data
       section.   The  data  section  is  divided  into a number of allocation
       groups.  The number and size of the allocation  groups  are  chosen  by
       mkfs.xfs(8)  so  that  there  is normally a small number of equal-sized
       groups.  The number of allocation groups controls the amount of  paral-
       lelism  available in file and block allocation.  It should be increased
       from the default if there is sufficient memory and a lot of  allocation
       activity.  The number of allocation groups should not be set very high,
       since this can cause large amounts of  CPU  time  to  be  used  by  the
       filesystem,  especially when the filesystem is nearly full.  More allo-
       cation groups are added (of the original size)  when  xfs_growfs(8)  is
       run.

       The  log  section  (or  area, if it is internal to the data section) is
       used to store changes to filesystem metadata while  the  filesystem  is
       running  until those changes are made to the data section.  It is writ-
       ten sequentially during normal operation and read  only  during  mount.
       When  mounting  a filesystem after a crash, the log is read to complete
       operations that were in progress at the time of the crash.

       The realtime section is used to  store  the  data  of  realtime  files.
       These  files had an attribute bit set through xfsctl(3) after file cre-
       ation, before any data was written to the file.  The  realtime  section
       is  divided  into  a  number  of  extents  of  fixed size (specified at
       mkfs.xfs(8) time).  Each file in the realtime  section  has  an  extent
       size that is a multiple of the realtime section extent size.

       Each allocation group contains several data structures.  The first sec-
       tor contains the superblock.  For allocation groups  after  the  first,
       the  superblock  is  just  a copy and is not updated after mkfs.xfs(8).
       The next three sectors contain information for block and inode  alloca-
       tion  within  the allocation group.  Also contained within each alloca-
       tion group are data structures to locate free blocks and inodes;  these
       are located through the header structures.

       Each  XFS  filesystem  is  labeled  with  a Universal Unique Identifier
       (UUID).  The UUID is stored in every allocation  group  header  and  is
       used to help distinguish one XFS filesystem from another, therefore you
       should avoid using dd(1) or other block-by-block  copying  programs  to
       copy  XFS filesystems.  If two XFS filesystems on the same machine have
       the same UUID, xfsdump(8) may become confused  when  doing  incremental
       and  resumed  dumps.   xfsdump(8) and xfsrestore(8) are recommended for
       making copies of XFS filesystems.

OPERATIONS
       Some functionality specific to the  XFS  filesystem  is  accessible  to
       applications    through    the    xfsctl(3)    and    by-handle    (see
       open_by_handle(3)) interfaces.

MOUNT OPTIONS
       Refer to the mount(8) manual entry for descriptions of  the  individual
       XFS mount options.

SEE ALSO
       xfsctl(3),   mount(8),  mkfs.xfs(8),  xfs_info(8),  xfs_admin(8),  xfs-
       dump(8), xfsrestore(8).



                                                                        xfs(5)


```

---


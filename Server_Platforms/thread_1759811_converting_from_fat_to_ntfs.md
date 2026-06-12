---
title: "converting from fat to ntfs"
date: 2011-05-16
forum: Server Platforms
---

### Post by bakhona on 2011-05-16
Hi guys

I've looked everwhere but cant find a solution for this. I am trying to convert my hard drive format from fat32 to ntfs. Is there any way for me to do this on ubuntu server, i know in the desktop edition gpart is normally most appropriate.

Please help.
Thanks 
Bakhona

---

### Post by deathadder on 2011-05-16
You can't convert from fat32 to NTFS. What you'll need to do is backup everything on the fat32 drive and then reformat it as NTFS. You can use the [mkntfs (mkfs.ntfs)]("http://linux.die.net/man/8/mkntfs") command from your Ubuntu server to actually format the drive.

---

### Post by dtfinch on 2011-05-16
Windows can [convert FAT to NTFS](http://technet.microsoft.com/en-us/library/bb456984.aspx). I'm curious why you want to do that though.

---

### Post by TBerk on 2011-07-20
This reply is a few months later but one reason seems to be a large file 'cap' on FAT32.

[http://en.wikipedia.org/wiki/File_Allocation_Table]("http://en.wikipedia.org/wiki/File_Allocation_Table")

*Note table on the right hand side re: *

```
Max file size 	

4 GiB minus 1 byte (or block size if smaller)
```



NTFS, otoh, has a much larger limit, or cap on files size:

[http://en.wikipedia.org/wiki/Ntfs]("http://en.wikipedia.org/wiki/Ntfs")

```
Max file size 	

16 EB &#8722; 1 KB (format);
16 TB &#8722; 64 KB (implementation)[3]

```

I'm currently trying to copy a 6Gig+ file over to a FAT32 volume and had forgotten all about this restriction.


TBerk

---


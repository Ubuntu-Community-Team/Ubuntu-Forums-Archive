---
title: "Best File System For Home Server?"
date: 2010-04-05
forum: Server Platforms
---

### Post by DBrocks on 2010-04-05
Hey guys,

Well I am rebuilding my home file server, and I was wondering what FS is the best for my purpose? I will be using 1x250GB SATA system drive, and several 1.5TB drives in RAID for storage. I was thinking EXT3 for the system drive, and XFS for the storage array. Any other suggestions are more than welcome!

---

### Post by iissmart on 2010-04-05
Definitely XFS for storage, check out this guide on how to tune it to perfection: [http://everything2.com/index.pl?node_id=1479435](http://everything2.com/index.pl?node_id=1479435)

Then ext3 or 4 for the filesystem. I don't really notice a difference between the two.

---

### Post by FuturePilot on 2010-04-05
It depends on what you will be doing. Dealing with lots of large files? XFS would probably be the best for that. If you're just dealing with general purpose file storage then Ext3/4 would be the best for that. Ext* is probably the best general purpose file system. Personally though, on the server side of things I don't trust Ext4 still. My servers are still using Ext3.

---

### Post by nix4me on 2010-04-05
voted system - ext3, storage - xfs.  All my servers are setup this way.

---

### Post by scouser73 on 2010-04-05
For system I chose ext4 and for storage, I chose other (ntfs), as I have five external hard drives totalling nearly 3Tb & I've found that ntfs doesn't use as much space as ext.

---

### Post by blur xc on 2010-04-06
This is a very interesting subject for me -as I'm planning on doing something almost identical. 

When you say xfs for storage if you will be using a lot of "large" files, what constitutes a large file?  My server will eventually hold my digital photo collection, which so far consists of more than 50,000 files.  Also, with every generation of digital camera, file sizes dramatically increase.  Used to be about 1mb, then 3 - 3.5 mb, now 12mb, the new FF digital cameras shoot at around 24mb and larger (50mb, I thin for uncompressed raw files).  Who know what they will be in 5 or more years.

Also, home videos captured from the camcorder would eventually end up there as well.

Thanks,
BM

---

### Post by Xianath on 2010-04-07
Those files would definitely qualify as large as far as filesystems are concerned. XFS is less efficient than EXT3 and even (yuck) JFS when it comes to the sub-megabyte range, but in my experience it absolutely rocks for large files. For me, the final straw in favor of XFS for large files (photos, videos, Lightroom catalog, virtual machine images etc) is the fact that it supports defragmentation natively, and fast. It's the difference between 2MB/sec and 200MB/sec throughput (those numbers are real, in my case).

Ultimately though, ZFS is the mother of all filesystems. The OP never mentioned Ubuntu or indeed Linux so if the goal is "just" to have storage, I'd go with NexentaOS. It wasn't there yet when I built mine but my next one will definitely be running NCP3. If and when BTRFS gets where ZFS is now, I'll reconsider again. The important thing is to stay ahead of the curve :)

Cheers,
Peter

---


---
title: "Recommended file system for a server"
date: 2006-06-13
forum: Server Platforms
---

### Post by DanielArdelian on 2006-06-13
I'm building a Samba File server with Ubuntu 6.06 server. This will mostly serve lots of small files (4 KB ~ 100 KB average).
  Can anyone make any recommendations for a filesystem on the data partitions ?

  Thank you,
  Daniel Ardelian.

---

### Post by ScatterBrain on 2006-06-13
I've had very good luck with XFS and Reiser. 

If I had to choose, I'd probably go with XFS.  It seems to be more stable and faster for my needs.

---

### Post by jimcooncat on 2006-06-13
I've been very happy with ReiserFS on my mail server. I wasn't so happy with Ext2 and Ext3. This is entirely subjective observance, and it may be that I understood Reiser's documentation better, as well as believed what people said about it's performance with small files.

Whatever filesystem you choose, please remember to check the physical media. The mkfs for Reiser does not run badblocks. Read the man pages, run badblocks to output to a file, then mkreiserfs with the badblocks file you made. If I had bad blocks at all on my hard disk, I'd probably buy a new one now rather than spending the time installing and configuring a server on it.

---

### Post by DanielArdelian on 2006-06-13
Thank you everybody for your suggestions. 
Tell you what...once I get this thing set up, I'll run some performance benchmarks on it. 

Until then, if you know any tools that can help me with those benchmarks, please menion them here.

---


---
title: "SSD tweaks in Linux"
date: 2008-09-06
forum: The Cafe
---

### Post by Ub1476 on 2008-09-06
SSD starts to pop up all over now, so I devoted this thread to share/gather some information on how to improve your Linux/Ubuntu system for SSD. Also reccomend that you tell which laptop those tips and tricks works good with (if there's any difference).

I'll write down some tips/headline (detailed instructions in link) which I found on Geek Sheet, zdnet blog:

[LIST]
[*]If your system motherboard uses a disk caching bus, change the BIOS setting from “Write Through” to “Write Back”.  

[*]Use the “noop” I/O scheduler.

[*]Change the file system mount options on SSDs to “noatime”.

[*]Ditch the journal and RAID your SSDs.
[/LIST]

[Source]("http://blogs.zdnet.com/perlow/?p=9190")

I'm personally not sure about EXT2 (no journal) and EXT3 (journal). I read that some people get serious performance issues with EXT2 and therefore use EXT3 even though it writes more to disk.

Please share more information, tips and tricks. :)

---

### Post by insane_alien on 2008-09-06
i would still use a journalled filesystem. they can prevent a lot of things going wrong. 

however, there are different levels of journalling. going for the one the write less to disk would probably be a good idea.

---

### Post by Ub1476 on 2008-09-06
> **insane_alien said:**
> 
however, there are different levels of journalling. going for the one the write less to disk would probably be a good idea.

So how do you do that?

---

### Post by youngalfred on 2008-09-06
there are numerous tweaks to make a journaling file system write less. alot of them can be found at [http://www.ubuntu-eee.com/index.php5?title=Main_Page](http://www.ubuntu-eee.com/index.php5?title=Main_Page)
some include the dirty writeback tweak and less swappyness.  I myself use reiserfs on my eee because of some reason i cant remember :p

---


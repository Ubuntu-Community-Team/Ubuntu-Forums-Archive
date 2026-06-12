---
title: "Defragmentation tip - a shell script"
date: 2010-07-07
forum: The Cafe
---

### Post by linux18 on 2010-07-07
After lots of reading about how EXT2/3/4, XFS, JFS, ReiserFS, and other *nix-based filesystems work I feel like I'm almost an expert on the subject. Linux based filesystem's get fragment about 1% of the time, so de-fragging isn't necessary under any normal conditions. Even better, using the "cp" and "mv" commands actually de-fragment the hard disk ( because the filesystem always tries to save a file contiguously, so moving a file around will give the filesystem another chance at keeping it contiguous ). In addition, when a file is fragmented, the performance loss is far less than it would be on windows. 

Ok, now for the bad news. If, in the rarest of cases fragmentation does occur, your lost in the linux world. No defragmentation utility exists ( well, some from 1998 and other very obscure ones ). So, with the help of some of the [www.commandlinefu.com](www.commandlinefu.com) people I bring you the deframenting command:

```
 find ~ -maxdepth 20 -type f -size -16M -print > t; for ((i=$(wc -l < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a" /dev/shm/d; mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t  
```  

Essentially, it moves files from your /home  to /dev/shm ( the linux ramdrive directory ) then moves them back to give the filesystem a second chance at keeping files contiguous. This command only targets files under 16mb, because if you are experiencing fragmentation, small files are the likely culprit. This command won't rename or change anything, it can even be run with applications that should be effected ( it might temporarily move around text files, firefox cache / config files, etc. but you can still use firefox and view files while this is running somehow ). 

Why use this script? Well, you shouldn't be experiencing fragmentation in ubuntu, so if you system is sluggish it's your virtualbox kernel modules ( it's still window's fault :p ). However, if you torrent and don't pre-allocate disk space or if your disk was full and you deleted everything ( and don't want to wait for the filesystem to automagically defragment ) then this script may help ( although its probably just the placebo effect )

Finally, to end my first ubuntu forum post, I would recommend that you don't use the script :confused:... because it may perpetuate the idea that linux systems "might" need defragmentation "in extremely rare cases". While true, if you are experiencing fragmentation AND a slowdown from fragmentation your best option is send your hard disk to someone for analysis so that when EXT 5 comes out, even rare cases won't need defragmentation.

Any thoughts?

---


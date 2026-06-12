---
title: "urgent rsync question: local copy, incremental bits?"
date: 2007-04-10
forum: Server Platforms
---

### Post by Underpants on 2007-04-10
I have to move lots of large files from point A to point B.

There is a windows file server at each end.

There is a Linux machine running next to point A. 

Each server has a respective share in this case: POINT-A and POINT-B

POINT-A and POINT-B are mounted in the home folder of my admin user on the Linux machine. 

I want to use rsync to mirror A to B. 

So as far as the Linux machine is concerned, it’s copying files from a local source to a local destination. However, in this scenario I’m finding that rsync isn’t comparing the files and just transferring the different bits like it does if I were using two Linux machines (one on each end) it’s transferring the entire file. The files I’m trying to keep synced are 10 and 20gb and only have a T1 to move them across. I can use a linux box on both ends without any problems, but I’d rather keep it simple and only use the single machine.

Am I missing something?

---

### Post by sgenchev on 2007-04-11
Well, you will be much better off installing rsync on Windows servers - I use cygwin, not sure if there is a native windows port, or setting a linux box on the other side of T. rsync in cygwin works well for me when I have to have a windows box.
 The reason is simple. Consider how rsync does it's magic for transferring only differences between 2 machines: 
  Machine1 looks at it's copy of a large file one little chunk at a time (I vaguely remember 32K number but I could be wrong) and calculates it's hash. Again, I am not sure if it is MD5 or SHA or some other hashing scheme - it does not really matter. Machine2 does the same thing with it's own copy. Then they compare 2 hashes; if they are the same - off to a next 32K, if they are not - transfer this 32K piece of file over and move to the next piece
 Now, if you are doing it on locally mounted filesystem, for you to calculate hashes on a Point B's server your local rsync process have to download the file anyway over your T1 link. At this point you might as well just copy it over entirely and do not bother with hashes - they would only slow you down.
 For incremental transfers you *have* to have rsync machines on both ends - there is no way around it.

---

### Post by MJN on 2007-04-11
<snip double post>

---

### Post by MJN on 2007-04-11
> **Underpants said:**
> Am I missing something?

Quite possibly, as mentioned above the fact that file hashing requires access to the files (and their contents).

Also, given you're doing a local transfer (as far as rsync sees things) you would also at the very least need to use the **--no-whole-file** option to force partial file transfers. Not doing so would fall back to the default of sending the whole file regardless how much has changed.

Mathew

---


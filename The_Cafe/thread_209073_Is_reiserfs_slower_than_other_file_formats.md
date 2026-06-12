---
title: "Is reiserfs slower than other file formats?"
date: 2006-07-04
forum: The Cafe
---

### Post by K.Mandla on 2006-07-04
I've been tinkering with reiserfs on an older laptop, because I read somewhere that it was ... somehow less prone to fault (does that sound right?). I'm all for that, but I've noticed my boot times seem slower than when I had straight ext3 partitions. Is that just my imagination? :confused:

---

### Post by Kimm on 2006-07-04
AS far as I know, reiserfs is less stable than ext3, but is much faster.

> 
**I've been tinkering with reiserfs on an older laptop** [...] I've noticed my boot times seem slower than when I had straight ext3 partitions. Is that just my imagination?


Thats probably your "Older laptop" playing tricks on you ;)

---

### Post by prizrak on 2006-07-04
First and foremost ReiserFS is a file system not a file format. There is a topic somewhere on the forum here about file system benchmarks you should look for it. I believe XFS and JFS are the fastest file systems.

---

### Post by kripkenstein on 2006-07-04
There is a benchmark out on the web somewhere, that 'proves' ReiserFS is slower than ext3 and some others. This benchmark is quoted quite a lot actually. But it is based on very old hardware, CPU-wise. In general, ReiserFS is built to run on faster hardware, where it should outperform other filesystems. So in general ReiserFS is a reasonable choice (several distros, including SUSE I believe, use it as default).

However, you say you have an older laptop. Depending on how old it is, ReiserFS might not be a good idea. Basic ext3 is better for slower systems.

---

### Post by K.Mandla on 2006-07-04
[QUOTE=prizrak]First and foremost ReiserFS is a file system not a file format.[/QUOTE]
Thanks, I corrected that.

[quote=kripkenstein]There is a benchmark out on the web somewhere, that 'proves' ReiserFS is slower than ext3 and some others. This benchmark is quoted quite a lot actually. But it is based on very old hardware, CPU-wise.[/quote]
Was it this one?

[http://fsbench.netnation.com/](http://fsbench.netnation.com/)

That looks quite comprehensive, although to be honest, it might be more information than I wanted. The all-knowing Wikipedia seems a little more direct, but less specific.

[quote=Wikipedia]Compared to ext2 and ext3 in version 2.4 of the Linux kernel. when dealing with files under 4k and with tail packing enabled, ReiserFS is often faster by a factor of 10–15.[/quote]
I don't know how accurate that is for my case, since I use 2.6+, and I'd bet most of my files are bigger than 4K. :rolleyes:

I think I shall experiment and see what works best for me. Like I said, the CPU in this machine is relatively slow (750Mhz), and that might be what seems to lag with reiserfs. JFS might be next for me.

This is what I like about Linux: I'm learning stuff. Thanks, all.

---

### Post by RavenOfOdin on 2006-07-04
Both partitions of my iMac 333 G3 are formatted with reiserfs and they're doing a great job, all things considered. 

I'd have to say no to the question in the thread title.

---

### Post by maagimies on 2006-07-04
I've been experimenting with quite a few filesystems, and in the end, always used reiserfs.
If I'm working on a low-cpu machine I'll use ext3 or jfs, but in every other, reiserfs.
IMHO it has better desing philosophies then other filesystems.

I'm just hoping Reiser4 to get more stable... sometimes it seems like Duke Nukem Forever ;)

edit:
To actually answer the question on the topic,
no,
ReiserFS is the fastest filesystem I've used, atleast in my usage :D

---


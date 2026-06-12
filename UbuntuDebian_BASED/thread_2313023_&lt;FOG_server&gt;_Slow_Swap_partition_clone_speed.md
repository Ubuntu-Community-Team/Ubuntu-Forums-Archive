---
title: "&lt;FOG server&gt; Slow Swap partition clone speed?"
date: 2016-02-09
forum: Ubuntu/Debian BASED
---

### Post by Nikolai D. on 2016-02-09
Hi there,
Cant remember my FOG forums login lol,
But anyway its still quite related so decided to post here in the meantime, why not,
(why not accumulate some know how on the forum of one of the most popular distro huh).
So i use FOG server, and some months ago i remember i had similar issue, but never came back to it to test it again,
Now an old friend of mine also started experimenting with FOG server, and he wanted to clone CentOS to different computers,
And he says its slooow to clone it. He had actually done what he wanted, but still i wondered what would be a proper solution to this question.
Now i have been googling and found this explanation: [http://clonezilla-sysresccd.hellug.gr/clonezilla.html]("http://clonezilla-sysresccd.hellug.gr/clonezilla.html")
That says: > 
By default, Clonezilla Live uses partclone for nearly all filesystems, including ext2/3/4, NTFS and FAT32. If a filesystem isn't supported by partclone, but is supported by partimage (spesifically: if the filesystem is HFS, HPFS or JFS), it is cloned by partimage.
if it isn't supported by either (for example Linux swap, though it doesn't make any sense to clone swap partitions), it is cloned by dd. Unlike partclone or partimage, dd copies all blocks of the partition instead of only used, resulting in slower imaging process and bigger images.
And since Clonezilla and FOG, since they are on Linux, and i suppose use same technologies on the backend, i tought its appropriate to ask it here as a general linux related question.
Does this then means that you actually, as soon as you try to clone a linux installation which has swap partition, with linux available tools, cant do anything to speed it up?
What is the simplest/right other solution to clone/auto install linux on a few computers?
thanks,
ND.

---

### Post by Nikolai D. on 2016-02-10
Most probably Cobbler is the right answer.

---


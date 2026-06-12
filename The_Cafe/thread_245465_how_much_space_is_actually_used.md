---
title: "how much space is actually used?"
date: 2006-08-27
forum: The Cafe
---

### Post by TheRingmaster on 2006-08-27
how much space does a 360 MB avi file actually take up?

---

### Post by aysiu on 2006-08-27
Is this a trick question?

---

### Post by TheRingmaster on 2006-08-27
well I've seen some things that download 100MB but only take up 50MB (just an example).

Edit: how would I compress that avi file and have it still play in totem?

---

### Post by GuitarHero on 2006-08-27
A file that's 360mb is going to take up 360mb, unless you get a video compression program of some sort to make it smaller.

---

### Post by djsroknrol on 2006-08-27
360MB would be roughly 1/3 of a 1GB HD....if that helps...

---

### Post by kate99 on 2006-08-28
360MB is not 360Mb exactly. it has a difference. might be 348, 357.5 but not exactly 360.

---

### Post by kate99 on 2006-08-28
sometimes it doesn't actually take up a complete 360, it will be between 348-359 MB.

---

### Post by daou on 2006-08-28
360MB / 1.024 = 351.5625 MB used. But I believe it also depends on your cluster size, although this really only has a big effect on large numbers of small files.

---

### Post by M7S on 2006-08-28
> **jpazindustries said:**
> well I've seen some things that download 100MB but only take up 50MB (just an example).

Edit: how would I compress that avi file and have it still play in totem?
The only case where something is a 100 mb download and then only takes up 50 mb, that I could think of is cd-images. When you download a cd-image it's always bigger than the actual files on the cd are when you've burned the cd-image. I've heard of extreme cases when a cd with 50 mb data resulted in a 700 mb image.

An avi-file is just an file though and should not change it's size.

---

### Post by TheRingmaster on 2006-08-28
okey dokie, thanks for your help

---

### Post by bom28 on 2006-08-28
Some file systems can write files in sparse mode, with this mode applications can create a huge empty or partly written file that will use disk space only for the non-empty parts. It's commonly the case for p2p apps like torrents.
"ls -l" will give you the size of the file. Use "du" to know how much space  is actually used on the disk (taking into account cluster uaage and sparse mode).
Or maybe your question is about the confusion where sometimes 1MB=1024*1024 bytes and sometimes 1MB=1000*1000 bytes

---


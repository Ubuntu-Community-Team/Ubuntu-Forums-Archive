---
title: "Music Playback Through Archives(.zip, .rar, .7z, etc.)"
date: 2010-07-14
forum: The Cafe
---

### Post by rabid9797 on 2010-07-14
So I've recently discovered that my favorite music player(foobar2000) supports playback of files in basically all popular archive formats, which I think is pretty freakin cool.

Now I have a relatively large music library(40 GB+) and this got me wondering, what would be the advantages/disadvantages to archiving my ENTIRE library either by artist or album?

I have done absolutely no research on this yet, but I just wanted to get an opinion from the community and find out if anybody else has ever considered doing this/has any experience with archived playback.

Does archiving reduce disk use a significant amount?
Does it affect playback quality or seek time?
What's the best archive format for this kind of use?
Is it even feasible?

Anybody have any ideas?

---

### Post by gnomeuser on 2010-07-14
Your music is very likely already compressed (even lossless FLAC files are compressed) and you won't gain anything.

You can get this transparently, e.g. using btrfs' compression mount option. This will compress files that benefit from it, decreasing the required amount of IO at the cost of slightly higher CPU load.

However for the purposes of storing music, you are not going to have any gains.

---

### Post by mikewhatever on 2010-07-14
Archiving music would not reduce disk space usage, because mp3s, oggs, and other digital formats are already compressed. Regardless, what you want is doable, but sounds like a big waste of time.

---

### Post by rabid9797 on 2010-07-14
So I guess reducing disk use is out of the question(not that I am in need of space, I have more than I'll ever use haha)

What about transferring music? I use a program called SyncToy to sync my music folder across 3 different machines, would there be any advantage in reading/transferring data across my wireless network if they were archived?(One big file vs. many small files)

---

### Post by cariboo on 2010-07-14
Music files are already compressed, you aren't going to gain anything by trying to compress them again. Try it yourself select a bunch of files and check the size of the selection, then create a zip file containing the same files, and compare the size.

---

### Post by hyperdude111 on 2010-07-14
I just tried this to see if it made any effect. I didn't compress my entire library but, it got a folder of 173.6mb down to 167.6mb. Seems pretty pointless TBH, it only save the equivalent of 1 song.

---


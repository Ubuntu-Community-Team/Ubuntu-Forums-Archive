---
title: "Tarballing your whole home folder?"
date: 2007-11-28
forum: The Cafe
---

### Post by blithen on 2007-11-28
Is it a good idea or a bad one? I would just back it up but I have to bring all my settings over to a new hard drive I'm getting tomorrow. Has anyone ever done it?

---

### Post by p_quarles on 2007-11-28
Yes, it can be done. Not a bad idea, unless you do what I did back when I didn't know better, and try to create the archive from *within* my user's home folder. (because, you know, that will create an archive that could expand infinitely, only constrained by the size of the hard drive -- and yes, I figured out what I'd done in time to stop it from ruining my day)

Just wondering, though, why a tarball? If you have the external media, there are other ways to mirror a directory (i.e., rsync, scp). But, yes, tarballs can accomodate very large directory structures.

---

### Post by Mateo on 2007-11-28
sounds fine to me.  BUT

there are many temp subfolders there.  I'd empty those so you don't tarball a lot of unnecessary stuff.

---

### Post by blithen on 2007-11-28
> **Mateo said:**
> sounds fine to me.  BUT

there are many temp subfolders there.  I'd empty those so you don't tarball a lot of unnecessary stuff.

Alright. Thanks guys!

---

### Post by blithen on 2007-11-28
Well my plan was to tarball the home folder and then put it on my 2gig flash drive. Unless of course I can fit it onto my flash drive without having to tarball it would just make my day.

Haha yes! I can. Though the write speed on the drive is total crap. but I will just not tarball it and copy everything over.
29387 items, totalling 927.3 MB

---

### Post by Mateo on 2007-11-28
i'd tarball anyways.  I'd rather move around 1 file than thousands of files.  just me i guess.

---

### Post by FuturePilot on 2007-11-28
> **p_quarles said:**
> Yes, it can be done. Not a bad idea, unless you do what I did back when I didn't know better, and try to create the archive from *within* my user's home folder. (because, you know, that will create an archive that could expand infinitely, only constrained by the size of the hard drive -- and yes, I figured out what I'd done in time to stop it from ruining my day)

Just wondering, though, why a tarball? If you have the external media, there are other ways to mirror a directory (i.e., rsync, scp). But, yes, tarballs can accomodate very large directory structures.

You know what's funny? I did that once :lolflag:
I was try out a backup program and I had placed the destination within the source. I was wondering why it was taking so long. Found out it was caught in a loop8-[

---

### Post by p_quarles on 2007-11-28
> **blithen said:**
> Well my plan was to tarball the home folder and then put it on my 2gig flash drive. Unless of course I can fit it onto my flash drive without having to tarball it would just make my day.

Haha yes! I can. Though the write speed on the drive is total crap. but I will just not tarball it and copy everything over.
29387 items, totalling 927.3 MB
Just a quick warning about that: if the flash drive is formatted (as many are) as a FAT16/32 partition, it would actually be better to tarball it first. FAT partitions don't retain Unix permissions, which means trouble for things like your .dmrc file. Tarballs will retain those permissions, regardless of what filesystem they're sitting on. 

I didn't know that you were talking about an amount of data that would fit on a flash drive, or I would have mentioned that before. My home folder/partition currently uses about 43 gigs. :)

@FuturePilot: Exactly the same. I was wondering why it would take more than hour to compress the 4 gigs or so of data I had in my home folder at the time -- then I thought to check the hard drive usage, and realized what was going on. Only funny because I was able to catch it. :)

---

### Post by blithen on 2007-11-29
> **p_quarles said:**
> Just a quick warning about that: if the flash drive is formatted (as many are) as a FAT16/32 partition, it would actually be better to tarball it first. FAT partitions don't retain Unix permissions, which means trouble for things like your .dmrc file. Tarballs will retain those permissions, regardless of what filesystem they're sitting on. 

I didn't know that you were talking about an amount of data that would fit on a flash drive, or I would have mentioned that before. My home folder/partition currently uses about 43 gigs. :)

@FuturePilot: Exactly the same. I was wondering why it would take more than hour to compress the 4 gigs or so of data I had in my home folder at the time -- then I thought to check the hard drive usage, and realized what was going on. Only funny because I was able to catch it. :)

Alright. thanks for the info. Though I might just format it to like EXT3. or something similar. 'Cause I don't want to tarball it.

---

### Post by mridkash on 2007-11-29
Make a tarball and split it into 500 mb chunks and save them onto DVDs. Thats how I backed up.

use the command split in terminal and to join back use cat

PS. Make sure that you do a md5sum check on the tarball before and after copying and match the number, otherwise the file may get corrupted.
type md5sum 'file path' in terminal

---

### Post by PrimoTurbo on 2007-11-29
> **mridkash said:**
> Make a tarball and split it into 500 mb chunks and save them onto DVDs. Thats how I backed up.

use the command split in terminal and to join back use cat

Why would you split it into 500 mb chunks if a DVD can support 4.7 GB?

---

### Post by timcredible on 2007-11-29
i've made tar files of my /home directory when installing new distros and moving to new computers, it works well, just ```
tar -cvf home.tar /home
``` works very nicely, and since it retains all file permissions, you can extract the files by double-clicking on it on the new system and extracting whatever files you want.  if you do a ```
tar -xvf home.tar
``` make sure you have the UIDs matching between the old system and new system or you won't be able to access anything.  using the fileroller gui to extract files resets the UIDs on the files so you don't have to worry about that.

---

### Post by samjh on 2007-11-29
I tar my home directory regularly for backup, and before each reinstall.

Just make sure to get rid of the contents in .thumbnails .nautilus .cache and your browser's own cache directories.  They can take up a lot of unnecessary space.

---

### Post by bobbocanfly on 2007-11-29
> **PrimoTurbo said:**
> Why would you split it into 500 mb chunks if a DVD can support 4.7 GB?

Safety? If one Tarball fails and you have deleted the source you will still have the other couple of Tars with your data on it. Never brilliant to lose it as you will have lost all the files in that tar but its better than starting fresh without anything.

---

### Post by mridkash on 2007-11-29
> Why would you split it into 500 mb chunks if a DVD can support 4.7 GB?

> Safety? If one Tarball fails and you have deleted the source you will still have the other couple of Tars with your data on it. Never brilliant to lose it as you will have lost all the files in that tar but its better than starting fresh without anything.

I do that because I heard somewhere that too big files are not supported on DVD filesystem and can lead to file corruption.

And this happened, I stored 9 of the chunks (4500 mb) on a dvd and it burned successfully but later when I did md5sum on each of the chunk, I was surprised to find that the last file was corrupted.
Conveniently, I burned that 500 mb file to another dvd without any harm to data. If the file was 4 gb something then the whole dvd would have been wasted.

Also, the chunks become handy to store anywhere temporarily, like pen drives, cds etc.

The split files are not tars. They cannot be opened until joined back again. Its just the convenience of handling files.

---


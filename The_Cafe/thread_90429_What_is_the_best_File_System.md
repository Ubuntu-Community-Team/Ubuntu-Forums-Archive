---
title: "What is the best File System?"
date: 2005-11-14
forum: The Cafe
---

### Post by Sunnz on 2005-11-14
Out of the four popular File Systems for Linux, ext3, reiserfs, JFS & XFS, what are the difference between them? What are the pro and con? What are they good at?

---

### Post by Samuel on 2005-11-15
[en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") explains it best.
personally i prefer ext3, its readable by all the live CDs or boot disks i have tried and also can be read from windows using software, i have never had a problem with it, i guess is use it because it dosnt give me headaches.

from what i understand, Reiser and XFS are supposed to be the best in terms of performance because they are good at moving around small files fast, however i cant say i have ever noticed a difference, i used reiser on suse and xfs on gentoo and i cant say i can really see any performance differences.

---

### Post by tom-ubuntu on 2005-11-15
I prefer ReiserFS over all the others. Didn't have any problems so far.

Was using ext3 before. Then the filesystem went corrupt an needed to be checked on the next reboot. It took around 3 days, if I remember correctly. Reiser is a lot faster in any terms.

---

### Post by Ubuntist on 2005-11-15
[QUOTE=Samuel]
[en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") explains it best.
personally i prefer ext3, [it] can be read from windows using software
[/QUOTE]

After reading the same Wiki, I decided to go with Reiser for its speed when I installed Ubuntu recently.  So far, no problems.

Can you give me a pointer to the software which allows Windows to read ext3?

I saw a mention somewhere recently that the latest Linux kernel can write NTFS.  That would eliminate my need for a FAT32 partition.

---

### Post by bionnaki on 2005-11-15
fat32 is the best.
everyone should install ubuntu on it.

---

### Post by gord on 2005-11-15
sarcasm reeeeeeeally doesn't work on the internet huh?

---

### Post by stimpack on 2005-11-15
Ive used both, no probelms with both, however the ext3 'filecheck' that occurs every 20 mounts is highly embarrassing, you dont want that coming up when your Windows mates are around, so I now use ReiserFS.

---

### Post by Zerocool10482 on 2005-11-15
I'm using ext3 and I think everythings ok so I'm fine. I have a dual boot machine. What is swap and why is it taking up 1.4gb of space?

---

### Post by Pablo_Escobar on 2005-11-15
[QUOTE=Zerocool10482]What is swap and why is it taking up 1.4gb of space?[/QUOTE]
Swap is a disk space that serves as an extra RAM when the standard one is used up. Mostly for RAM hungry programs. The same is in Window$ - called swap file.
It's 1.4GB because as I pressume You've had Ubuntu installer let the partitioning for You. It should be around 2 x RAM You have on Your PC.
Mine is 1,14 GB :)

---

### Post by Sunnz on 2005-11-15
What about XFS and JFS? They seem have the same bag as reiser but a little more?

---

### Post by Wally68 on 2005-11-15
I was reading the other day about XFS and reiserfs in a thread about reiser4. From what I gathered, xfs is good for servers, but not too good for desktop use. I use rieserfs, which is stable and fairly quick. I did notice slightly faster boot times with reiserfs over ext3, but not really any performance gains. What I did notice though, is that with reiserfs, stuff doesn't disappear like it did with ext3 (reasons unknown). To make reiserfs boot even faster use the 'notime' and 'notail' options in fstab.
Wally

---

### Post by Sunnz on 2005-11-15
So what makes XFS good for server use?

---

### Post by WildTangent on 2005-11-15
I've heard that XFS is extremely fast, but becomes unstable if you don't shutdown properly, example: power failure. That's why it's good for servers, because they're usually hooked up to some form of redundant/UPS power supply.

-Wild

---

### Post by ubuntp on 2005-11-15
I've been using XFS on a server for about 5 years now and can only recommend it, but it isn't for everyone. It was originally developed by SGI to be used with large video files, so it is faster than all other filesystems when it comes to reading/writing large files (high bandwith I/O). I'm using it on a fileserver that is serving 500MB+ files.

It's also a robust journaling filesystem like ext3 or ReiserFS, so the remark about XFS being unstable and losing data is not true. In fact it has excellent user tools for recovery and things like that. The harddrive in the server was failing once and i was able to read about 95% of the raw data off the drive (with dd) and xfstools were able to recover all of it.

[http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/)

---

### Post by Zerocool10482 on 2005-11-15
Thanks I wanted to know what that was. Can I use less of a swap? I don't want to use 1gb of my hard drive.

---


---
title: "Dual-booting XP/Ubuntu, items not showing up in XP?"
date: 2010-04-26
forum: Ubuntu Moblin Remix
---

### Post by DanteDouglas on 2010-04-26
So, I'm using an Acer Aspire One using UNR 9.10, dual booted with XP. On XP, I can add things to the shared partition (the drive is 50gb XP, 50gb Ubuntu, and 60gb shared) and they'll show up fine in the Ubuntu partition, but for some odd reason XP can't find whatever I put on the shared partition from the Ubuntu environment.

XP does, however, recognize SOMETHING is there, it just can't see it. I tried viewing hidden folders, nothing. Any help?

---

### Post by DanteDouglas on 2010-04-27
Any help here?

---

### Post by JimTaverna on 2010-04-27
I'm stumped. Is the partition NTFS or Fat32?

I do have a compromise solution, though, that may work for you until you get things straightened out. Well, three actually.

The first is a driver called [[COLOR="Blue"]extfsd[/COLOR]]("http://www.ext2fsd.com/") which allows you to read/write ext partitions...with certain limitations. The website gives a somewhat brief overview of the capabilities, but it seems to be a capable enough solution.

The second is another driver called [[COLOR="blue"]EXT2 IFS[/COLOR]]("http://uranus.chrysocome.net/linux/ext2ifs.htm"), which does essentially the same thing, though it may cover more than the previous solutuion. It also reads/writes to ext file systems.

The third, and final, option is called [[COLOR="blue"]Explore2fs[/COLOR]]("http://uranus.chrysocome.net/linux/explore2fs-old.htm"), which was created by the developer of EXT2 IFS. This is a safer route, in that you can only read from the ext fs.

None of these may be the perfect solution for you, especially if you want to segregate your downloads/music/whatever data from the OS. Your setup is precisely what I have configured and I prefer it that way. I have links in Win 7 (user directory) to the data on my "Storage" partition, so that if/when/absolutely I have to nuke the OS, there's no need to worry about any files I might have left there that I need and reconstruction is made somewhat easier. 

Also, I'm sans an external backup drive, so data corruption becomes more critical for me, at least for now.

Regardless, it will at least give you the option of accessing data on both systems while you figure out the problem, assuming such access is critical for you.

BTW, if you already know about the aforementioned tools, you never read this post, and I was never here. :)

Good luck! JT.

---

### Post by DanteDouglas on 2010-04-27
Yeah, thanks, but I did know about those programs :P

This has never happened to me before, I'm really confused. The partition is FAT32, and XP doesn't even seem to see that anything is there... it's really weird. Like, for example, Ubuntu reads the partition as having 18 free gigs, but XP says it has 42gb free. Really really odd.

---

### Post by JimTaverna on 2010-04-28
Check out this thread:

[http://tinyurl.com/surehopethisworks](http://tinyurl.com/surehopethisworks)

It isn't EXACTLY the same issue that you face, but it does have more than a few of the problems you are confronted with. A resolution was found, so maybe there's hope for your situation yet.

---

### Post by DanteDouglas on 2010-04-28
Thanks Jim. I'm not super well-versed in cfdisk, but it seems fairly straightforward. I could probably do what the thread is suggesting in Gparted too, I'll dink around a bit.

---


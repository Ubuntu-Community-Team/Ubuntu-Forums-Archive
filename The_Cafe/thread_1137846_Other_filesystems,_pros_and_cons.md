---
title: "Other filesystems, pros and cons?"
date: 2009-04-25
forum: The Cafe
---

### Post by Rokurosv on 2009-04-25
So I've only used Ext3 and 4 on all my Linux installs and I've had no problem with them, but I'm a little curious what do the other filesystems offer? Anyone here using another FS other than ext? I've always been tempted to try another one.

---

### Post by |Mitch| on 2009-04-26
google "file system benchmarks" 

After a little research of my own, I believe I understand EXT4 to be the best all around. 

Reiserfs is better for moving a large number of small files

XFS is better for moving large files 

EXT4 has the better average on reading/writing

I believe I understood that right.

---

### Post by SunnyRabbiera on 2009-04-26
> **|Mitch| said:**
> google "file system benchmarks" 

Yes but benchmarking is not a up front experience, and varies per system.

Anyhow I have tried XFS and JFS, XFS is speedy but I always had issues with loading it, JFS I also tried but it never lasted a day.
EXT seems fine

---

### Post by Rokurosv on 2009-04-26
Benchmarks are good references but they vary from system to system. I was looking for user experiencies, for example corruption of files and other things. I've tried ext4 and I think it was too much for my dv1000 Pavilion. I'm running ext3 with Debian and it runs smooth and my laptop doesn't get too hot but I guess that doesn't involve filesystems.

@Sunny: What do you mean trouble loading? Like GRUB or booting into it?

---

### Post by SunnyRabbiera on 2009-04-26
> **Rokurosv said:**
> 

@Sunny: What do you mean trouble loading? Like GRUB or booting into it?

Indeed, for me I prefer GRUB over LILO so what loads well with it is what I use.

---

### Post by Peasantoid on 2009-04-26
I've heard ReiserFS is good. Apparently now there's a stigma because its creator killed someone.

Edit: Did some research and apparently it isn't that decent of a filesystem at all. Oops.

---

### Post by samjh on 2009-04-26
If I'm not using ext3, it's JFS.

JFS is a fantastic file system.  When I tried Jaunty Alpha, I had a couple of hard crashes, but JFS recovered just fine.  It's very robust, and handles power-out situations better than XFS.  Performance is solid too - as fast as, if not faster than, ext3.

---

### Post by dragos240 on 2009-04-26
Ext2 is great on a flash drive, it doesn't hog too much space.

---

### Post by stimpack on 2009-04-26
> **Rokurosv said:**
> I was looking for user experiencies, for example corruption of files and other things.

I'd urge you to ignore any user experience regarding data-corruption. Its such a complicated area and the sample size here is impossibly small, that you will get nothing out of it.

As for user-experience of things like speed, I found ReiserFS was the fastest for loading World of Warcraft.

Now if ZFS ever hits kernel, I think the contest is over.

---


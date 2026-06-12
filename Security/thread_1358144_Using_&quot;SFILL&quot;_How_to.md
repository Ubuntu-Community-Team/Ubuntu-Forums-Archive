---
title: "Using &quot;SFILL&quot; How to ???"
date: 2009-12-18
forum: Security
---

### Post by wittsend on 2009-12-18
Hello,
 
I need to wipe data on a computer a friend is donating. Previously it had Windows 2000 and I have loaded Ubuntu 8.04 LTS on a full drive sized partition. I need to overwrite the remaining free space where Ubuntu didn't use in the install. I found out about "Sfill" but am CLUELESS to use it.
 
I don't do "Linux speak" well. To me it is like reading a book upside down in a mirror. So, if some could in a **step by step fashion, in simple english** tell me what to do and how to do it, it would be greatly appreciated. Assume I know nothing so if I need to get to a certain place please tell me how to get there.
 
I believe I have Sfill installed (as best I can tell) and I know how to get to the Terminal, but that is about it. I read about being "in the root", but haven't a clue how to get there. Again I only want to overwrite ALL the free space, but not whip the drive of Ubuntu.
 
Thank you for your time.
Regards, Tom

---

### Post by unmole on 2009-12-18
Try this..Open the terminal and type

```
sfill mountpoint/
```Replacing mountpoint/ with the "address" of the partiton you wish to screw.


P.S. It is not 'being in the root' it is 'becoming root'.
This should help you [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by BkkBonanza on 2009-12-18
As long as you give it some path on the physical drive you want to wipe it will work ok. It only needs a "mountpoint" to decide which free space (which partition) you're talking about.

Hence, if you have just one partition mounted for everything you could do like this,

sudo sfill /home

If you have multiple partitions mounted in various places then choose a path on a mounted partition you want to fill.

Note that sfill can take a long time. It basically allocates all free space and starts filling it multiple times and then deletes the whole thing. So don't do stuff that will be busy creating/deleting files while you do this.

If I recall last time I used it you can open another terminal and watch the free space shrink away as it works, using "df -h".

---

### Post by wittsend on 2009-12-18
Thank you both for your assistance.  I presume that the perpetually active hard drive light is an indicator that I have been successful. :)
 
Tom

---

### Post by BkkBonanza on 2009-12-18
I like to watch it fill...

watch -n 5 df -hm

(ctrl-c if you get tired)

Actually, now that I think of it... if you have a big drive this can be excruciatingly slow. It does some 27+ passes! Nowadays most experts say that so many passes provide no benefit.

If you already started it you can ctrl-c and it will clean exit. Then try,

sudo sfill -lzv /home

This only does 2 passes and a final zero. More sane I think.
And the v causes some info to print out as it goes.

---

### Post by lordal on 2010-01-05
> sudo sfill -lzv /home

This only does 2 passes and a final zero. More sane I think.
And the v causes some info to print out as it goes.     According to the  sfill Manpage 

[html]http://manpages.ubuntu.com/manpages/karmic/man1/sfill.1.html
[/html] > **-l**     lessens the security. Only two passes are written: one mode with
              0xff and a final mode with random values.

**-z**     wipes the last write with zeros instead of random dataso -lz should change the second and final pass from random values to zeros rather than add a third pass.

Therefore I would use,
```
sudo sfill -lv /home
```Hope this helps,

 Al

---

### Post by ron_o on 2010-08-24
Actually, I just ran this on a 250GB ext2 partition with a core2duo and a SATA drive. The quickest command I found was this:

```
sudo sfill -f -v -ll <MountPoint>
```

This is the most insecure mode there is but for large partitions it's necessary, unless you want to wait several days or weeks to finish on a large drive. The code above finished in about 100 minutes. But without the "f" option, it was running over 1,000 minutes and only 25% done!

There's no reason to believe that zeros won't be as affective as random numbers, and one wipe will do as well as 25. I'm going to try photorec to see if I can get anything off it.

[EDIT]

I ran photorec on the partition and I found nothing of interest to me, but there still could be something of interest on there. It found 17 files with 128 GB of data, but I don't know what those files are of. It's all these *.gpg, *.swf, *pap and *.asp files that it said it recovered. But I couldn't open them up. Photorec just thought they were files and didn't know what to do with them, I suspect. There were "hidden sectors" that were present, too, which I know nothing of.

Perhaps this way isn't perfect, but it's good enough for me at this time. There's only one way that you can be sure that all your data is gone and that is absolute obliteration of your hard drive completely. The next best way is to use your drive's ATA firmware's security feature and let it overwrite all your data, even bad blocks. I tried this latter technique and I almost borked my drives completely. I wouldn't recommend it.

---

### Post by rookcifer on 2010-08-24
> **ron_o said:**
> There's no reason to believe that zeros won't be as affective as random numbers, and one wipe will do as well as 25. I'm going to try photorec to see if I can get anything off it.

That's right.  There is indeed no reason to believe multiple passes are better than one.  There is no experimental evidence anywhere that shows data wiped with one pass is recoverable.  And zeros are as effective as random data.  The only difference is with random data no one can prove the drive was wiped.

---


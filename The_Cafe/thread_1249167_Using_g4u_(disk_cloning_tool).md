---
title: "Using g4u (disk cloning tool)"
date: 2009-08-25
forum: The Cafe
---

### Post by billdotson on 2009-08-25
By reading the g4u (ghost 4 unix) documentation/FAQs I found out that you don't HAVE to have the size of your image backup be the same size as the disk or partition you are copying. How do you do this you say? Well, write zeros to the empty space of your partition! The author said that g4u doesn't understand different filesystem types because it reads data at a lower level than a filesystem. Therefore, to write zeros to a partition or a drive you can use an operating system you want to clone to do the filesystem specifics for you. 

One example that was given was to open a text file and fill it with 0s until the partition ran out of space then save it. After backing up the image you could compress it and voila, the zeros or "empty space" would be compressed down to a very small size. He also mentioned some special Windows programs to do this and the use of dd and /dev/zero. 

However, I have some questions: if you wanted to write zeros to all the empty space on a partition how would you find out where to start? You certainly couldn't just pick byte 12848471253 and have dd start churning away without messing something up..

Also, MS is being really nice about Vista and have made it so that the second service pack won't install if "third-party disk management tools" are used. I don't know how but they made it so that cloned images of Vista wouldn't contain the right system files or the updater would not recognize them. If you used dd or g4u to make a low level partition or drive backup of a Vista install wouldn't that be a way around that? 

G4u sounds like it copies data at the hardware level and I am almost certain that that is what dd does, so aren't they basically the same thing?

---

### Post by billdotson on 2009-08-27
bump.
 
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

That says that dd cannot presently clone Vista OEM partitions. I thought dd was a low level copier that copied below the filesystem level. How would MS have made it so that Vista refuses to boot or whatever it does if it is copied below the filesystem level? Unless dd means that OEM Vista won't boot on anything except the exact same hardware I don't see how that is possible. Same for g4u if it copies at a lower than filesystem level.

Now for the other question: how would you find out where to start writing zeros to the partition or hard drive so you could make a compressed backup at a good size but not ruin the image? You can't just do "dd if=/dev/zero of=/dev/sdb3 starting at block 1283744 until end of partition"... or can you (obviously in another syntax)?

---

### Post by cariboo on 2009-08-27
Have a look at this [thread]("http://ubuntuforums.org/archive/index.php/t-1228710.html"), it may answer your question.

---

### Post by yabbadabbadont on 2009-08-27
> **cariboo907 said:**
> Have a look at this [thread]("http://ubuntuforums.org/archive/index.php/t-1228710.html"), it may answer your question.

Actually, that archived version is probably a little confusing to those who didn't see the original thread.  All the quotations are lost.  Just in case the OP here didn't see the link to the original thread, it is here:

[http://ubuntuforums.org/showthread.php?t=1228710](http://ubuntuforums.org/showthread.php?t=1228710)

---

### Post by cariboo on 2009-08-27
That thread i only three week old, so it isn't archived yet, just click the link at the top of the page that says:

```
View Full Version : [all variants] overwrite unused disk space with zeros
```

---

### Post by billdotson on 2009-08-28
Ok, thanks for that article. I normally try to search the forums but I sometimes have difficulty finding answers or either the answers are hidden very deep within a thread about a very specific issue (often times when I have a more general info question).

The only thing I don't understand is: Why cant you fill a file up with zeros in your root filesystem? Does that mean you don't do it from within the operating system or that you shouldn't even do it on that filesystem from something like a live cd?

---

### Post by yabbadabbadont on 2009-08-28
It would be safe to do it from a livecd, as long as you then removed the file you used to fill the filesystem before trying to boot using it again.

---

### Post by billdotson on 2009-08-28
Why would having a full filesystem cause issues? Is it because of temporary files that have to run while the system is loaded?

So I think I understand this: you use /dev/zero to fill a file full of zeros to the point where there is no disk space left. Then you delete the file (shift delete or regular delete to trashbin?) Then all the empty space that used to be there is filled with zeros and if you make a g4u or dd image of the partition the compressed image will be significantly smaller. Correct?


*Does anyone have an idea as to why dd cannot clone OEM Vista installs? I just don't see how if a program copies below the filesystem level how something inside the filesystem can dictate what it can do.*

I believe i am right about this but when using dd to image anything you always umount it first right?

I suppose since ntfs read/write support on linux seems top notch now you could just use dd to file a file on your windows partition full of zeros instead of having to use a special program for it. Using dd or g4u is pretty cool because it isn't filesystem specific and it creates a backup only of the files on there at the time, not the ones you deleted a long time ago that are still extractable with some special hard drive tools (I think this is correct but if I am wrong please correct me).

---

### Post by billdotson on 2009-09-08
bump.

Could someone give me a possible explanation of why Vista OEM can't be cloned with dd?

---


---
title: "input/output error (5) on ext4 for 9 files on new HDD"
date: 2016-11-29
forum: Ubuntu Development Version
---

### Post by alain.roger on 2016-11-29
Hi,

i've several files (videos of my son) that can not be rsync. Progress of operation is done to 100% but once at 100% kubuntu "17.04" returns me an input/output error (5).

Firstly i have to say that i transfer data from my former HDD 500GB to my new 2TB HDD. data were transfered without any issue and were ok.
Now i want to move those files from the directory sdb1/videos to another directory on sdb2/videos-to-review but i can't copy or rsync them.

I firstly check if HDD had some bad sectors with smartmontools and badblocks commands but no BAD SECTORS.

So what can i do to get those files back to working state ? There are very important as they are about my son and for my lawyer. 

Thx

---

### Post by howefield on 2016-11-29
Moved to the "*Ubuntu Development Version*" forum.

---

### Post by dino99 on 2016-11-29
what is the output from > file data-file as well as > strings data-file? if neither of these commands are able to read the file, there is a very high probability that your file is corrupted since disk and filesystem corruption "has already been" ruled out ...

This could be the result of bad RAM in your computer. Try testing your RAM by booting in recovery mode. Then select the option to test your RAM, from there.

---

### Post by #&amp;thj^% on 2016-11-29
Also would be good to know is how is the 2TB HDD formatted IE: ext4/3 vfat ntfs or other?
But " input/output error (5)" is a nasty error and often no solution to. (At least that I have found)

---

### Post by sudodus on 2016-11-29
You checked for bad blocks, but did you check and try to repair the file system?

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number.

The data are very important, so it is a good idea to start by cloning the drive to another drive of at least the same size, and try to recover the data from the cloned copy. You can use ***ddrescue*** to clone the drive. See this link and links from it,

[Repair the partition table and file system of a pendrive](https://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by alain.roger on 2016-11-30
i did a sudo fsck /dev/sdb1 once unmont partition and it solved my issue. Partition is ok, files are readable and rsync works well now with those files.

---

### Post by sudodus on 2016-11-30
I'm glad you found a solution, and thanks for sharing it :-)

---

### Post by #&amp;thj^% on 2016-11-30
> **alain.roger said:**
> i did a [COLOR=#000000][FONT=Ubuntu Mono]sudo fsck /dev/sdb1 once unmont partition and it solved my issue. Partition is ok, files are readable and rsync works well now with those files.[/FONT][/COLOR]

I am very happy to hear this also...sometimes the data (Possible Loss) is worth more or at least as much as Gold.
I like hearing happy endings.:D
Best Regards

---


---
title: "When will Ubuntu fix the 4GB file transfer size too USB bug/error?"
date: 2009-05-28
forum: The Cafe
---

### Post by Mai_Tsu on 2009-05-28
This is really annoying.

---

### Post by schauerlich on 2009-05-28
I don't think Ubuntu will fix it. Its developers might.

---

### Post by hanzomon4 on 2009-05-28
You wouldn't be transferring files to a fat32 partition would you? Cause fat can't handle files larger then 4gb... you have to split and then cat once it's on some other filesystem

---

### Post by rileinc on 2009-05-28
I remember experiencing the same problem when transferring a 2GB file. At first, the speed was around 10MB/s, but within 5 seconds it drops to 2MB/s, then less than 256KB/s. 
I looked around for solution and found out that it had something to do with the kernel and Ubuntu wasn't the only distro suffering from it. I never found a solution or work-around.

---

### Post by eragon100 on 2009-05-28
Transferring data to my mp3 player is very slow as well, luckily I usually only have to copy one song to it. All of my other USB sticks, and my external harddrive are fast tough. My previous mp3 was, too. So apparently the problem only exists with certain drivers, ie. it may be the manufacterer's fault.

---

### Post by Mai_Tsu on 2009-05-28
> **hanzomon4 said:**
> You wouldn't be transferring files to a fat32 partition would you? Cause fat can't handle files larger then 4gb... you have to split and then cat once it's on some other filesystem

No, NTFS.

> **rileinc said:**
> I remember experiencing the same problem when transferring a 2GB file. At first, the speed was around 10MB/s, but within 5 seconds it drops to 2MB/s, then less than 256KB/s. 
I looked around for solution and found out that it had something to do with the kernel and Ubuntu wasn't the only distro suffering from it. I never found a solution or work-around.

My lowest USB transfer speed is 9.2 MB/S.

> **eragon100 said:**
> Transferring data to my mp3 player is very slow as well, luckily I usually only have to copy one song to it. All of my other USB sticks, and my external harddrive are fast tough. My previous mp3 was, too. So apparently the problem only exists with certain drivers, ie. it may be the manufacterer's fault.

It only affect's single files over the size of 4GB.

---

### Post by monsterstack on 2009-05-28
Some problems I had with ntfs file systems were a badly fragmented drive, and a drive that was almost full, but still (so it said) had enough space for my stuff. Have you tried using the latest [ntfs-3g]("http://www.ntfs-3g.org/index.html#download") [ntfs-3g.org] driver? The one in the jaunty repository is 2009-2.1, but the current version is 2009-4.4. Could make a difference. I've never tried transferring such enormous files, though. What do you do now? Would splitting the files and then joining them together on the ntfs disk work? Alternatively, would using ext* filesystems be acceptable?

---

### Post by gn2 on 2009-05-28
What files do you have that are bigger than 4gb? :confused:

---

### Post by fballem on 2009-05-28
> **gn2 said:**
> What files do you have that are bigger than 4gb? :confused:

Probably some DVD .iso files.

---

### Post by monsterstack on 2009-05-28
> **fballem said:**
> Probably some DVD .iso files.

Or maybe the Debian Lenny Blu-Ray iso image. That thing is about 19gb if I remember correctly.

---

### Post by Tristam Green on 2009-05-28
i wasn't aware of such a bug.  i transfer dvd iso's all the time to my 32gb flash stick and have never had a problem.

---


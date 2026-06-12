---
title: "Windows Partition being stubborn with Wine via Permissions"
date: 2010-10-29
forum: Wine
---

### Post by Gr3ghammett on 2010-10-29
I have a dual boot laptop. I use Windows 7 on one partition, and Ubuntu 10.10 on the other.  What I have done in the past when there was something on the Windows Partition that I wanted to run on the Ubuntu partition, I used wine and went right to it as is in the file manager and there was no issue.

A few years later, there now is.  By default, all the executables in my Windows 7 partition are seen by Ubuntu as being "not marked as an executable".  When I go to the Permissions tab of the desired file that resides on my windows partition, and check "mark as executable" it quickly unchecks itself, since obviously my profile on ubuntu isn't the owner of my files on my windows partition.

My question is, is there a way around this, so i can reference files on my windows 7 partition and run them with wine on my ubuntu os like before?  I'm trying to not have to copy folders, so I can save on hard drive space.

Thanks ahead of time!

---

### Post by Soulcage on 2010-10-29
You're not supposed to run programs from you windows partition. They made it impossible since it could destroy your windows partition. [http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2")

---


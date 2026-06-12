---
title: "Backingup ext4"
date: 2010-01-31
forum: Ubuntu One (CLOSED)
---

### Post by linkingeek on 2010-01-31
I have Installed 9.10 but i can't rely on its stability so is there any way for backing up whole system as image?
I have heard of "clonezilla" but it saves whole system bit by bit, means systems free space too.

---

### Post by duanedesign on 2010-01-31
There is a nice page on the wiki that can help you decide.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by kaibob on 2010-02-01
> **linkingeek said:**
> I have Installed 9.10 but i can't rely on its stability so is there any way for backing up whole system as image?
I have heard of "clonezilla" but it saves whole system bit by bit, means systems free space too.

The alternative (Ubuntu-based) version of Clonezilla seems to do a better job with ext4 drives. A few months back, I tried the "stable" version of Clonezilla, and it wouldn't work at all. 

When I create a drive image with the default settings, Clonezilla does not create a sector-by-sector image, and it does not include free space. I have a 160-GB drive with Windows and Ubuntu, and my drive images are typically about 1.6 GB. I don't know why things would be different in your situation.

---


---
title: "Debug my hard drive...."
date: 2009-02-13
forum: The Cafe
---

### Post by aschwerin.moses on 2009-02-13
Well.. i want to debug my hard drive. I have a SATA hard drive. How do u guys suggest me to go about doing this???... will the old MSDOS commands work well.. or is there anything else.. please suggest..

---

### Post by aquavitae on 2009-02-13
What exactly do you mean by debuging your hard drive - do you mean the equivalent of the dos scandisk? The program that does basically the same thing in linux is called fsck, but its not something you should need to do manually.  It automatically runs occasionally when you boot up and the only reson for doing in manually is if you have reason to believe there is a problem with your drive.

---

### Post by aschwerin.moses on 2009-02-13
yea.. having problems with my hdd.. it gets detected sometimes, multiple restarts, resetting the cables works sometimes.. so just want to start from scratch..

---

### Post by aquavitae on 2009-02-13
So you need to do a physical scan? I can try to guide you through the process, but its not trivial. If you do a physical scan (i.e. when it checks each block for physical errors) the bad blocks list is saved to the current partition, so if you repartition your disk you'll lose that list.

As a start, can you post the output from the command```
sudo fdisk -l
```This will tell you what partitions you have and how they are formatted.  It will affect the arguments which need to be given to fsck.

---

### Post by mips on 2009-02-13
Your drive is failing, backup your data.

---

### Post by aquavitae on 2009-02-13
> **mips said:**
> Your drive is failing, backup your data.
Good advice.

---


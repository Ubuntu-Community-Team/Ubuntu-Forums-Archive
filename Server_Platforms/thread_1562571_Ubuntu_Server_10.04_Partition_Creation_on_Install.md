---
title: "Ubuntu Server 10.04 Partition Creation on Install"
date: 2010-08-27
forum: Server Platforms
---

### Post by akira7799 on 2010-08-27
Hey All,

I am currently trying to setup Ubuntu Server 10.04.  I have installed Ubuntu twice, having only to wipe the drive and start again.  

My problem is this: when trying to setup LVM partitions and mount drives in Webmin following install, I can only partition/format a 54mb section of hard disk space when there is about 54gb left on the drive.

Is there something basic I'm missing?  Can I extend the 54mb section to the full 54gb?  

I used the LVM - Guided Using Part of Disk selection when installing Ubuntu.  

Sorry if I've missed any info to help you answer my question.  Also, if this is a frequent question, I apologize.  I've looked for this answers to this problem to no avail.

Thanks,
akira

---

### Post by akira7799 on 2010-08-28
[Solved]  

I ended up manually installing/partitioning the Ubuntu 10.04 Install.  

- I used 100mb for boot formatted ext4
- 2x amount of ram for swap formatted swap (2gb)
- 10gb for / formatted ext4 (root file system)
- remainder of drive for /home formatted ext4

Looking forward to using the forum more!
Dave

---


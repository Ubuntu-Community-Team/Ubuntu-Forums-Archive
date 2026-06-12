---
title: "setting up Raid"
date: 2009-03-25
forum: Server Platforms
---

### Post by bujums on 2009-03-25
I am getting ready to install ubuntu Server.  I have done it many times but never with Raid in mind.  I found a little info out there on doing this but I still have a question.

If I plan to have two 500 GB hard drives for backing up several computers in the a network (Raid).  Do I need to have a separate hard drive for my OS and home partitions?  Or, can I just partition one of the large drive for those areas?

If it matters... I am setting up a small server for Shared files and important backups for 5 computers.

---

### Post by Bachstelze on 2009-03-25
If you're doing RAID-1, you can install everything on RAID, including your root and /boot parptitions. GRUB will be able to boot from them just fine.

---

### Post by bujums on 2009-03-25
Good! That is what I was hoping for... Thank You

---


---
title: "[mdadm] RAID5 crashed. Need to add faulty disk back"
date: 2010-10-22
forum: Server Platforms
---

### Post by 8086 on 2010-10-22
My server has not been powered on for the last few months, and when I finally turned it on yesterday and installed a fresh new Ubuntu 10.10 I started getting disk errors from my RAID.

Luckily this RAID5 ran fine with only 3/4 disks, and I thought I'd backup what was on it while it was still running ok. Unfortunately after writing some data to the RAID, yet another disk was marked as faulty, and thus it no longer functions. 

I would like to add the last-to-be-marked-as-faulty drive back in, and then mount the raid as read-only just to save what I can, but I have so far been unsuccessful in doing so. I was hoping someone here could help?

More specifically I have a RAID5 /dev/md0 where sda1 and sdd1 are removed, and just sdb1 and sdc1 are still active. I want to add sda1 to /dev/md0 and just clone the whole device using dd: ```
dd if=/dev/md0 of=/mnt/my_backup_drive/raid.img
```
Any ideas on how I can make this happen? I need that data ...

ps. Leave my lackluster backup routines out of this for now :p

---


---
title: "RAID 0 with 2 SATA disks"
date: 2006-05-08
forum: Server Platforms
---

### Post by xeo_pt on 2006-05-08
I need to make a two SATA disks, one of 125 Gb and the other with 250 Gb
act like one drive.
The best I did was make a RAID 0 but it doesn't install Grub.
If some one can help me.

Thanks in advance.

---

### Post by LordHunter317 on 2006-05-09
You can't do it that way.  Why do you want to do this?  This sounds really, really bad, and a good way to lose data.

---

### Post by xeo_pt on 2006-05-10
[QUOTE=LordHunter317]You can't do it that way.  Why do you want to do this?  This sounds really, really bad, and a good way to lose data.[/QUOTE]
Thanks for your help, but can you give me any clue of how to solve this problem?

---

### Post by LordHunter317 on 2006-05-10
You *can't*.  I said that.

You could at most, partition the second drive out and get a RAID-0 that way, with wasted space on that disk (well you can use that partition as you please, but it won't be as part of the array).  You'll still need a non RAID-0 /boot.

If you want JBOD, you can span with LVM2.  But you don't want to do that either.  And you'll need a non RAID-0 /boot.

Why do you want to do this?

---


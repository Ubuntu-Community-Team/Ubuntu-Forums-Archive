---
title: "fsck on RAID 5"
date: 2009-11-04
forum: Server Platforms
---

### Post by pwebster25 on 2009-11-04
Can fsck run on a software RAID 5 setup?  I have the following and my system hangs when the fsck runs after the 30th boot.

boot - md0 - RAID 1 (2 drives plus spare)
/ - md1 - RAID 1 (2 drives plus spare)
/home - md2 - RAID 5 (3 drives)
/var - md3 - RAID 5 (3 drives)

Sometimes I can get it to skip (ESC) and it runs fine. I do have the desktop GUI loaded on my server setup, as I am more comfortable in a gui environment.

Once the server boots (when I can get passed the fsck) it runs fine (apache, php, mysql) and it keeps going without any assistance.

I am running Jaunty server amd 64 with desktop gui.
It is an AMD 64 processor and has 3 identical 500 GB HDDs.
The server primarily serves moodle for a school.

---

### Post by fjgaude on 2009-11-04
Yes, **fsck** works fine on an **mdadm** array... I've done it dozens of times without issue.

---

### Post by pwebster25 on 2009-11-04
Thanks.  I tried running fsck and e2fsck from a jaunty live CD.

sudo e2fsck -C0 -p -f -v /dev/sda5
It threw an error and wouldn't run.  Said it wasn't a valid ext2 file system (it is ext3).

sudo fsck /dev/sda5
I got the following 

fsck.mdraid: not found
Error 2 while executing fsck.mdraid for /dev/sda5

---

### Post by fjgaude on 2009-11-04
Feels like you have a failed array. What do you get with this:

```
sudo mdadm --assemble --force --scan
```

I guess you can't boot, eh? One of the three drives is bad?

---

### Post by pwebster25 on 2009-11-05
Thanks, Frank-
Unfortunately, I made a stupid mistake and:
1) Didn't have an external backup.
2) Decided to reinstall system on the / partition (All the data I needed was on the /var partition.  Unfortunately, I also overwrote everything on the /var partition.

I ran this 
```
sudo mdadm --assemble --force --scan
```
from live cd and it assembled my array just fine and I can view it in nautilus.  However, none of the files that I need are there.  

I have looked at tools like gddrescue but it seems that the recovery tools won't find a whole directory that has been deleted, only individual files (by file extension, etc). 

I had a couple major (to me and my colleagues) mysql databases (one was running moodle).  I think I have lost all of that.  A very expensive lesson about taking my time and about external databases.

I think if I had run this command yesterday before overwriting the disk I could have rescued/backed up what I needed and then reinstalled the system.

---

### Post by fjgaude on 2009-11-05
Don't feel too bad, for it is mistakes that cause us to learn lessons, really learn. We all learn, day-by-day.

---


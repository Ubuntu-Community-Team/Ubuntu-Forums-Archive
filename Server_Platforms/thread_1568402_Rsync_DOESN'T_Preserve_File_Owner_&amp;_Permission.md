---
title: "Rsync DOESN'T Preserve File Owner &amp; Permission - Using Automounted NTFS backup drive"
date: 2010-09-05
forum: Server Platforms
---

### Post by AlexanderDGreat on 2010-09-05
Hi, this is my machine:

ext4:
1x 80gb - /boot, /swap, /(root) - sda
1x 80gb - /home - sdb

ntfs:
1x 250gb - /backups - sdc

1. First of all, I automount sdc /backups via /etc/fstab like this:

```
/dev/disk/by-label/backups /media/backups ntfs defaults,uid=1000 0 2
```

2. Second I use a rsync to backup my /boot/ /(root) and /home

For example:

```
rsync --delete -avz /boot /media/backups/boot/
```

When I check **sdc** (my ntfs backup drive), all files in there are 777, whereas it should be 755, and sometimes the owner is me, whereas it should be ROOT.

As an experiment, I backed up my files NOT in **sdc** (my ntfs backup drive), but in my /home folder instead, **_RESULT: every thing is OK, and it preserved file owner & permission!_**

Is there something I'm missing here? Is there something I don't understand?

Please help because I'm learning to BACKUP my system. Thanks for reading. :)

---

### Post by TwoEars on 2010-09-05
NTFS doesn't use UNIX permissions. This is your problem.

---

### Post by BkkBonanza on 2010-09-05
Also, rsync has options -p and -t to preserve perms and file times, which are useful for backups. But won't help with NTFS anyway.

And you mounted the NTFS drive with uid=1000 - which I believe makes the default ownership "you" since 1000 is the uid of the first user on the system.

---

### Post by AlexanderDGreat on 2010-09-05
Thank you man, bodhi also has the same answer:

[http://ubuntuforums.org/showthread.php?t=283131&page=19]("http://ubuntuforums.org/showthread.php?t=283131&page=19")

Great community. :)

---

### Post by AlexanderDGreat on 2010-09-05
@BkkBonaza - Thank you for answering, my problem is now solved.

I'm using CRON and RSYNC to backup my files.

Heliode's guide on backing up files with TAR works as well. I've restored my computer 10x already, using experimental cron, rsync, and tar. No fancy GUI, and I'm just a beginner.

Thanks man. Have a nice day. :)

---


---
title: "BIG PROBLEM - Reshaping mdadm RAID5"
date: 2011-12-11
forum: Server Platforms
---

### Post by szafran on 2011-12-11
Hi,

I have a huge problem. A couple of days ago I've runned a reshaping of my RAID5 array from 10 to 8 HDDs. FS is ext4. So first I've done:

```
resize2fs /dev/md2 11000G
e2fsck -f /dev/md2
mdadm /dev/md2 --grow --array-size=12000000000
mdadm /dev/md2 --grow --raid-devices=8 --backup-file=/root/backup
```

and after 2 days it finished giving me an array with 10 HDDs, which included 2 spares (so everything ok untill now)
But then I've done some stupid thing. Didn't calculate the size and executed:

```
mdadm /dev/md2 --grow --raid-devices=7 --backup-file=/root/backup
```

and it started reshaping.
I've stopped the reshaping process at about 10% (it took some tim for my stupid brain to process what I've done)

Will I be able to fix the file system after that reshaping ? Or I've lost 10TB of data ??

Any suggestions welcome (preferably ones that will help me to keep my data)


EDIT: As it turns out after finishing the reshaping everything turned out fine. Probably there were no files on the truncated part of the filesystem :P

---


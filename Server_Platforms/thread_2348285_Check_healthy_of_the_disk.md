---
title: "Check healthy of the disk"
date: 2017-01-02
forum: Server Platforms
---

### Post by sed_faster on 2017-01-02
Hello folks,

I know the software mkfs to format and ignore badblocks on disk (through this link: [https://ubuntuforums.org/showthread.php?t=2320318&p=13469469#post13469469](https://ubuntuforums.org/showthread.php?t=2320318&p=13469469#post13469469)
But now I need check healthy of my drive. I googled and find this command:
```

sudo fsck /dev/sdd1

```

I read the man fsck and I know which this software serve to check healthy of the disk but the report it was very fast and only print something like "clean" (sorry, but I can't remember all sentence).
I need know if this software it is the best option!

Thanks

---

### Post by deadflowr on 2017-01-02
fsck is file system checker.
What you want is smartmontools which reads the S.M.A.R.T data of the hard drive.
See: [https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

---

### Post by CharlesA on 2017-01-03
> **deadflowr said:**
> fsck is file system checker.
What you want is smartmontools which reads the S.M.A.R.T data of the hard drive.
See: [https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

This is a good start. Keep in mind that a disk can fail even if SMART reports everything is OK. This is why it is important to keep up-to-date backups. Without a backup, if a disk dies with no warning, you have lost all your data.

However, it is a good idea to do the SMART tests and keep an eye on the metrics such as Reallocated Sectors and Pending Bad Sectors. There are other metrics you should be looking at as well. Please see here:
[http://www.computerworld.com/article/2846009/the-5-smart-stats-that-actually-predict-hard-drive-failure.html](http://www.computerworld.com/article/2846009/the-5-smart-stats-that-actually-predict-hard-drive-failure.html)
[http://serverfault.com/questions/519726/how-reliable-is-hdd-smart-data](http://serverfault.com/questions/519726/how-reliable-is-hdd-smart-data)

---


---
title: "Script to remove directories no quite right!"
date: 2006-03-09
forum: Server Platforms
---

### Post by emut on 2006-03-09
I have installed sbackup from Sourceforge and it's great.  Only problem it does not have any way to remove old backup file so the backup directory ends up filling up pretty quickly so I have tried writing a script to clean out the directory but it is only removing the contents of the directory not the empty directory.

Script:

```
#!/bin/bash
#
#/home/colin/Scripts/
PATHTOCLEAN="/var/backup"
DAYSOLD="14"
find $PATHTOCLEAN -mtime +$DAYSOLD -exec rmdir -R {} \;
```

The backup is saved to the /var/backup directory in it's own directory each night.  When the script is run it removes the contents of the directories sbackup created but does not remove the directory.

```
colin@server:~/Scripts$ sudo ls -l /var/backup
total 84
drwx------  2 root root 4096 2006-03-09 15:08 2006-02-17_14.09.39.516738.server.ful
drwx------  2 root root 4096 2006-03-09 15:08 2006-02-18_03.00.02.322924.server.inc
drwx------  2 root root 4096 2006-03-09 15:08 2006-02-19_03.00.02.762177.server.inc
drwx------  2 root root 4096 2006-03-09 15:08 2006-02-20_03.00.02.135884.server.inc
drwx------  2 root root 4096 2006-03-09 15:08 2006-02-21_03.00.01.970768.server.inc
drwx------  2 root root 4096 2006-03-09 15:32 2006-02-22_03.00.02.029022.server.inc
drwx------  2 root root 4096 2006-03-09 15:32 2006-02-23_03.00.02.744578.server.inc
drwx------  2 root root 4096 2006-03-09 15:32 2006-02-24_03.00.03.162135.server.inc
drwx------  2 root root 4096 2006-03-09 15:32 2006-02-25_03.00.02.843705.server.ful
drwx------  2 root root 4096 2006-03-09 15:32 2006-02-26_03.00.02.813422.server.inc
drwx------  2 root root 4096 2006-03-09 15:32 2006-02-27_03.00.02.853955.server.inc
drwx------  2 root root 4096 2006-03-09 15:32 2006-02-28_03.00.02.942755.server.inc
drwx------  2 root root 4096 2006-03-01 03:03 2006-03-01_03.00.03.551245.server.inc
drwx------  2 root root 4096 2006-03-02 03:03 2006-03-02_03.00.03.110524.server.inc
drwx------  2 root root 4096 2006-03-03 03:03 2006-03-03_03.00.03.621528.server.inc
drwx------  2 root root 4096 2006-03-04 03:03 2006-03-04_03.00.02.935621.server.inc
drwx------  2 root root 4096 2006-03-05 03:04 2006-03-05_03.00.04.002490.server.ful
drwx------  2 root root 4096 2006-03-06 03:03 2006-03-06_03.00.03.503630.server.inc
drwx------  2 root root 4096 2006-03-07 03:03 2006-03-07_03.00.04.297044.server.inc
drwx------  2 root root 4096 2006-03-08 03:03 2006-03-08_03.00.03.644106.server.inc
drwx------  2 root root 4096 2006-03-09 03:03 2006-03-09_03.00.04.276479.server.inc

```

How can I get the script to remove the empty directories left behind?

---

### Post by emut on 2006-03-13
Now sorted, I set a crontab up to run it as it was and it ran fine deleting the empty ones.  Just didn't work when I ran it by hand!

---


---
title: "Drive Information and WebMin"
date: 2016-03-03
forum: Server Platforms
---

### Post by mirdragon on 2016-03-03
Hi,

I have 5 x 3 TB data drives installed with the OS installed on an 120GB SSD and the allocated space per data drive is 2.79TB

2 drives are currently in ZFS format from an old system which I am currently transferring the data and then will reformat to Ext4

when I look at the dashboard on WebMin it says I only have 12.22TB yet I calculate there should be at least another 1.5TB

Am I current in thinking this is either a Ubuntu+ZFS issue or Webmin issue

thanks

---

### Post by howefield on 2016-03-03
Thread moved to the "*Server Platforms*" forum.

---

### Post by SeijiSensei on 2016-03-03
When you format a drive with ext4, a portion of the drive is set aside for root.  The default is 5%, which is way too much on a large device like yours. That might account for the "missing" space you see from webmin.

From the man page for the "-m" option to mkfs.ext4 ("man mkfs.ext4")

> 
Specify the percentage of the filesystem blocks reserved for the super-user.  This avoids fragmentation, and allows root-owned daemons, such as syslogd(8), to continue to function correctly after non-privileged processes are prevented from writing to the filesystem.  The default percentage is 5%.

If you use
```
sudo mkfs -t ext4 -m 1 [device]
```
then only 1% of the drive will be reserved for root.  I don't know if 0 is a valid value here.

---


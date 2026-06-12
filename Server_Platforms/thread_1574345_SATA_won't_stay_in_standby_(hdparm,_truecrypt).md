---
title: "SATA won't stay in standby (hdparm, truecrypt)"
date: 2010-09-14
forum: Server Platforms
---

### Post by Blu3IcE on 2010-09-14
Hi there,

I have two additional disks in my server for backup and data storage. They are connected via SATA. One is a Samsung and the other is a Seagate.

They are both encrypted with Truecrypt and mounted in /media.

Since I don't use them to often (once a week) they are set to standby via hdparm, which works perfectly.
To monitor the standby behavior I poll them every 5 minutes with hdparm -C and log these values (with cacti).

The problem is, every day between 7:30am and 7:40am something wakes up both drives.
I already looked everywhere (cronjobs, anacron, ...) but I was unable to find a solution to stop my drives from spinning up.

I'm still running Hardy:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

Ask if any more informations needed, i'll be happy to give them.

---

### Post by Blu3IcE on 2010-09-17
Ok, it took my a while, but by using the kernel log file with ```
echo 1 > /proc/sys/vm/block_dump
``` I found the programms reading from my drives:
```
Sep 17 07:46:43 Hostname kernel: [485648.856070] standard(28162): READ block 12312 on dm-0
Sep 17 07:46:43 Hostname kernel: [485648.884452] standard(28162): READ block 8216 on dm-0
Sep 17 07:46:43 Hostname kernel: [485648.906910] ls(28172): READ block 12320 on dm-0
Sep 17 07:46:43 Hostname kernel: [485648.909387] ls(28172): READ block 12328 on dm-0
Sep 17 07:46:43 Hostname kernel: [485648.909402] ls(28172): READ block 12336 on dm-0
Sep 17 07:46:43 Hostname kernel: [485648.909410] ls(28172): READ block 12344 on dm-0
Sep 17 07:46:43 Hostname kernel: [485648.909417] ls(28172): READ block 12352 on dm-0
```

Now the question... what is the program/daemon "standard"?
And why is there an ls running? What is causing this?

---

### Post by Blu3IcE on 2010-09-17
Ah, filesystem is ext3, mounted with noatime.

---


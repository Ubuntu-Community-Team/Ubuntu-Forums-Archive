---
title: "Allocate more disk space to /var directory"
date: 2009-09-06
forum: Server Platforms
---

### Post by hanzgroove on 2009-09-06
Hi,

I'm having a problem with my server where the /var directory is full. I was in the process of importing a large amount of data into MySQL when I noticed it just stopped importing. Turns out the /var directory is full. How can I increase the disk space allocated to the /var directory? i'd appreciate any help on this. Thanks.

Here's an output of df -H:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/md1               996M   241M   705M  26% /
tmpfs                  1.1G      0   1.1G   0% /lib/init/rw
varrun                 1.1G    66k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G   177k   1.1G   1% /dev
tmpfs                  1.1G      0   1.1G   0% /dev/shm
/dev/md5               5.0G   595M   4.5G  12% /usr
/dev/md6               5.0G   5.0G    25k 100% /var
/dev/md7               237G   4.9M   237G   1% /home
none                   1.1G   4.1k   1.1G   1% /tmp

---

### Post by volkswagner on 2009-09-06
It looks like you have space available at /usr and /home which both are adjacent to /var partition.

You can use parted to resize the partition and use the newly freed space to allocate to resizing /var partition.

```
man parted
```

You will need to reboot for changes to take.

---

### Post by hessiess on 2009-09-06
Or you could move the mysql data dir somewhere else in the fs where you do have enough space.

---

### Post by hanzgroove on 2009-09-06
Thanks for the advice fellas. I was a bit worried about using parted on a production server so I just ended up moving the MySQL data directory to /home/db which has plenty of space. Worked like a charm. Thanks again.

---


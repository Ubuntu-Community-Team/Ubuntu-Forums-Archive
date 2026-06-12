---
title: "mdadm email failure"
date: 2007-08-04
forum: Server Platforms
---

### Post by t3kn0lu5t on 2007-08-04
I have a 6.06LTS Server with the base install.  I have a RAID1 array of two disks configured for use via /dev/md0
I'm trying to use a simple command via cron to alert me if the array degrades.

```

gray@io:~$ sudo mdadm --monitor -1 --scan --mail somebody@example.com /dev/md0
sh: /usr/sbin/sendmail: No such file or directory
gray@io:~$

```

SOLVED - It helps to have an MTA installed/configured.  Duh.

---


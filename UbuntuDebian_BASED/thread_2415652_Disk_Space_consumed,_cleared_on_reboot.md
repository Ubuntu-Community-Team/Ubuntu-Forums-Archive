---
title: "Disk Space consumed, cleared on reboot"
date: 2019-03-29
forum: Ubuntu/Debian BASED
---

### Post by kyle00322 on 2019-03-29
I'm running my Zentyal (based on Ubuntu) as my mail server and firewall, My disk fills up for no apparent reason throughout 24 hrs and when I reboot it goes back to 10% used.

```
kyle@wendellsmail:~$ df -l
```

**This is the usual state of my system**
```
Filesystem                        1K-blocks     Used Available Use% Mounted on
udev                                3949692        0   3949692   0% /dev
tmpfs                                796192     6252    789940   1% /run
/dev/mapper/wendellsmail--vg-root 228710796 21352584 195670688  10% /
tmpfs                               3980952       16   3980936   1% /dev/shm
tmpfs                                  5120        0      5120   0% /run/lock
tmpfs                               3980952        0   3980952   0% /sys/fs/cgroup
```

/dev/mapper will continue to rise throughout the day going up about 10% an hour I can't seem to find what consumes all the disk space.. Any suggestions?

---

### Post by jeremy31 on 2019-03-29
Moved to Ubuntu/Debian based

---


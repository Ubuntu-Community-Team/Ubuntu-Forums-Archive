---
title: "I just can't seem to get Huge Pages working"
date: 2015-12-18
forum: Server Platforms
---

### Post by ajthemacboy on 2015-12-18
Hi! I have a home server running Ubuntu 15.10. I use it almost entirely for Java servers. My applications would benefit a lot from Huge Pages, but I just can't seem to get them working. 

Meminfo:

```
AnonHugePages:   1140736 kB
HugePages_Total:     256
HugePages_Free:      256
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB


```

/etc/security/limits.conf:

```

# End of file
aj   soft   memlock    4194304
aj   hard   memlock    4194304

```

/etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="hugepagesz=128M hugepages=8"
```

/etc/sysctl.conf:

```
vm.nr_hugepages = 256
vm.hugetlb_shm_group = 1000
```

Whenever I start my Java application with ```
[COLOR=#222426][FONT=Consolas]-XX:+UseLargePages[/FONT][/COLOR]
``` I get this:

```
Java HotSpot(TM) 64-Bit Server VM warning: Failed to reserve large pages memory req_addr: 0x00000006c0000000 bytes: 4294967296 (errno = 12).
```

I've tried everything I can find. A while ago I tried creating a group just for Hugepages, and it didn't work. I want to be able to start my Java application from the default user, 'aj', so I really don't want to create a separate group anyway.

---

### Post by ajthemacboy on 2016-01-02
Bump, anyone have any suggestions?

---


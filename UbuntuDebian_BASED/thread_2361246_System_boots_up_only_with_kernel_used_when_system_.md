---
title: "System boots up only with kernel used when system was installed."
date: 2017-05-14
forum: Ubuntu/Debian BASED
---

### Post by x3ua on 2017-05-14
I installed Elementary OS (trusty based) yesterday to PC with fakeraid. Had to install mdadm package to get disks usable. No problems when installing and everything worked fine. After upgrade to new kernel, PC does not boot up anymore. If I use old kernel (4.4.0-38-generic) it will boot up, but not with 4.4.0-77-generic or -lowlatency. I think something is missing from new kernel. I tried to reinstall mdadm -package, but it wont help.

I'm using XFS filesystem to / and /home.

---

### Post by oldos2er on 2017-05-14
Moved to Other OS Support, Ubuntu/Debian BASED.

---

### Post by Bashing-om on 2017-05-14
x3ua; Hello; Welcome to the forum.

Yeah agreed - dependencies not installed,

Try - from a booting kernel :
```

sudo apt update
sudo apt full-upgrade

```

Re-boot and see what the result is .

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by x3ua on 2017-05-14
All upgrades where already installed, did not help.. What could be problem? I guess XFS support is included to kernel, so it has to relate fakeraid.

---

### Post by Bashing-om on 2017-05-14
x3ua; Well ..

Let's look and make sure that all of the -77 kernel packages are installed:
```

dpkg -l | grep linux-

```


[INDENT][INDENT]could be - other
[/INDENT][/INDENT]

---

### Post by x3ua on 2017-05-14
```

$ dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                all          Linux image base package
ii  linux-firmware                                 1.157.8                                                   all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.77.83                                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-38                         4.4.0-38.57                                               all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic                 4.4.0-38.57                                               amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-77                         4.4.0-77.98                                               all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-77-generic                 4.4.0-77.98                                               amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-77-lowlatency              4.4.0-77.98                                               amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.77.83                                               amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                       4.4.0.77.83                                               amd64        lowlatency Linux kernel headers
ii  linux-image-4.4.0-38-generic                   4.4.0-38.57                                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-77-generic                   4.4.0-77.98                                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-77-lowlatency                4.4.0-77.98                                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic             4.4.0-38.57                                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-77-generic             4.4.0-77.98                                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.77.83                                               amd64        Generic Linux kernel image
ii  linux-image-lowlatency                         4.4.0.77.83                                               amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-77.98                                               amd64        Linux Kernel Headers for development
ii  linux-lowlatency                               4.4.0.77.83                                               amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                      all          base package for ALSA and OSS sound systems

```

---

### Post by Bashing-om on 2017-05-14
x3ua; Hummm ..

kernels are complete and up-2-date .
I am at a loss as to what to suggest other than reading the boot log .
How one could 'journalctl' from an external source - well I am open to learning !

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by x3ua on 2017-05-15
There's something missing from kernel. Can't mount raid array when boot to recovery.
```
mount: special device /dev/mapper/pcd_cbgagdbkhb1 does not exist
```

Found old topic like this: [https://ubuntuforums.org/showthread.php?t=1959706](https://ubuntuforums.org/showthread.php?t=1959706)

---


---
title: "Audicity Will Not Open"
date: 2017-01-31
forum: Ubuntu Studio
---

### Post by G_M_Slater on 2017-01-31
When I attempt to launch Audacity nothing happens. To troubleshoot I tried launching it from a command line and got the following:

** (Audacity:11184): ERROR **: Resource problem creating '/tmp/orbit-gslater' Trace/breakpoint trap (core dumped)

I am running Ubuntu Studio 15.10. Does anyone know how to resolve this? I have never encountered it before.

---

### Post by howefield on 2017-01-31
Well, leaving aside that 15.10 is beyond End of Life and no longer supported, have you run out of space/inodes to create the file ?

What's the output of ..

```
df -i
```

---

### Post by G_M_Slater on 2017-01-31
> **howefield said:**
> Well, leaving aside that 15.10 is beyond End of Life and no longer supported, have you run out of space/inodes to create the file ?

What's the output of ..

```
df -i
```

df -i gives the following:

```
Filesystem        Inodes   IUsed     IFree IUse% Mounted on
udev              206174      589     205585     1%  /dev
tmpfs             214516      875     213641    1%  /run
/dev/sda1        6111232  1964087    4147145    33% /
tmpfs             214516       21     214495     1%  /dev/shm
tmpfs             214516        6     214510     1%  /run/lock
tmpfs             214516      17     214499     1%  /sys/fs/cgroup
/dev/sda5       114778112   457235  114320877     1% /home
cgmfs             214516       13     214503     1%  /run/cgmanager/fs
tmpfs             214516       26     214490     1%  /run/user/1000
```

I know that my file system partition is fairly full, but not completely. I am currently unable to delete any files from it though. Whenever I attempt to open a folder as root I get the message Unable To Copy The User's Xauthorization File. This message also pops up if I attempt to launch BleachBit (as root) or Lucky Backup (super user).

---

### Post by G_M_Slater on 2017-02-01
Issue resolved. I deleted a LOT of old linux-image versions. That freed up space in my root partition and now all works normally.

---


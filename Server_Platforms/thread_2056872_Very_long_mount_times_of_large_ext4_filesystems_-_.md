---
title: "Very long mount times of large ext4 filesystems - 12.04.1 LTS"
date: 2012-09-12
forum: Server Platforms
---

### Post by szafran on 2012-09-12
Hi,

I'm having problems with the mount times of larger filesystems (I use ext4).

Info:
```
root@NAS:~# time mount /dev/vdc /mnt/tempik

real	0m49.696s
user	0m0.000s
sys	0m49.339s
root@NAS:~# time mount /dev/vdb1 /mnt/nowy

real	1m26.682s
user	0m0.004s
sys	1m25.949s
root@NAS:~# uname -a
Linux NAS 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Both those devs have ~10TBs. The first one is "normal" 32bit fs, and the second one is a 64bit fs (I'm using standard v1.42 e2fsprogs). Smaller drives (eg. 2TB) are mounted without problems in a reasonable time (0-2secs). On oneiric those big devs are mounted in under a second (2-3 seconds max if the hardware is busy). I need at least one of those devs to be mounted during boot (they're not boot drives, nor root fs - they just contain lots of data that some of my startup apps need), but with those mount times I'm getting timeouts during boot. All filesystems are clean.

Does anyone have an idea what's wrong with precise that it acts this way? And, maybe, how to fix this?

---

### Post by szafran on 2012-09-14
Hello again,

I've resized one of the fs to 16TB, and now the mount times are even more abstract:

```
root@NAS:~# time mount /dev/vdb1 /mnt/nowy

real	4m19.015s
user	0m0.000s
sys	4m17.964s

```

I can even live with the OSs boot time of >4min, but how to configure it to wait for that fs to mount properly instead of giving a timeout error during boot, and giving up the mount process. Is there a way to set that timeout ? (in grub, or maybe fstab?)

---

### Post by szafran on 2012-09-15
Ok. Now I know that the kernel update is the problem here. After installing a clean 12.04.1 the mount times are ok. After doing an apt-get update && apt-get upgrade && apt-get dist-upgrade the kernel gets updated to 3.2.0-30-generic and the mount times go up (from less then a second to over 4min). Anyone knows how to fix that ??

---

### Post by szafran on 2012-09-15
I've reverted to kernel 3.2.0-29-generic, and everything is fine now. I'll wait with kernel updates until it'll be fixed.
If this is some new bug, can someone tell me how to get it to the Ubuntu support, so they know about it ?

---

### Post by SeijiSensei on 2012-09-15
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Xenefungus on 2012-09-17
I can confirm this bug on an up-to-date 12.04 install (Kernel 3.2.0-30). Mount time for a 10TB device is over one minute.

---

### Post by vexorian on 2012-09-17
> **SeijiSensei said:**
> [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
...

---

### Post by redscorp on 2012-09-23
> **szafran said:**
> Hello again,

I've resized one of the fs to 16TB, and now the mount times are even more abstract:

```
root@NAS:~# time mount /dev/vdb1 /mnt/nowy

real	4m19.015s
user	0m0.000s
sys	4m17.964s

```

I can even live with the OSs boot time of >4min, but how to configure it to wait for that fs to mount properly instead of giving a timeout error during boot, and giving up the mount process. Is there a way to set that timeout ? (in grub, or maybe fstab?)

Can confirm similar behavior. See my comments at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054605](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054605) ...

```
root@AGVault:~# time umount /data

real 0m1.031s
user 0m0.000s
sys 0m0.028s
root@AGVault:~# time mount /data

real 3m55.614s
user 0m0.000s
sys 3m37.050s
```

Actually, szafran, if it's you who posted the bug report, you should do also some extra stuff. Se comment #2 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054605/comments/2](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054605/comments/2)

---

### Post by szafran on 2012-09-24
Actually, I didn't officially report any bugs on Ubuntu. Don't even have a Launchpad account (that's the main reason, that I don't report bugs on Ubuntu - I don't want and don't need that account).

As for now I can only confirm what has been said before.

All of above filesystems were created using:
```
mkfs -t ext4 -T big -m 0 -v -b 4096 -L <label> <dev>
```

df -h on the filesystems:
```
/dev/sdf2       459G  198M  459G   1% /mnt/tempik
/dev/md5p1       11T   10T  865G  93% /mnt/mag1
/dev/md5p2       11T  159M   11T   1% /mnt/mag2
```


Mount times on 3.2.0-31-generic kernel (same goes for 3.2.0-30-generic):
```
root@NAS:/mnt# time mount -O noatime /dev/disk/by-label/tempik tempik
real    0m0.299s
user    0m0.004s
sys     0m0.168s

root@NAS:/mnt# time mount -O noatime /dev/disk/by-label/mag1 mag1
real    1m10.703s
user    0m0.004s
sys     1m7.964s

root@NAS:/mnt# time mount -O noatime /dev/disk/by-label/mag2 mag2
real    1m11.026s
user    0m0.000s
sys     1m8.052s
```

And to that there's that jbd2 process running every second or so. Don't really know what it does, but it reads/writes a lot. And therefore overall speeds on those drives go down.

And now for 3.2.0-29-generic kernel:
```
root@NAS:/mnt# time mount /dev/disk/by-label/tempik tempik
real    0m0.088s
user    0m0.000s
sys     0m0.048s

root@NAS:/mnt# time mount /dev/disk/by-label/mag1 mag1
real    0m0.318s
user    0m0.000s
sys     0m0.068s

root@NAS:/mnt# time mount /dev/disk/by-label/mag2 mag2
real    0m0.762s
user    0m0.000s
sys     0m0.384s
```

The jbd2 process is still messing with the drives. So it's not good on this kernel too.
The jbd2 process is messing with small and big filesystems.

Conclusion:
I don't advise to anyone using bigger filesystems to upgrade the kernel over 3.2.0-29-generic - just don't do it 'till it's fixed ;)

---

### Post by vexorian on 2012-09-24
You actually do *need* an account in some bug tracker if you'd like this bug to be fixed. Developers don't usually read these forums.

If you don't like launchpad for some reason, then try posting about it in the kernel's bug tracker or is it a mailing list? I doubt this is something that happens only in the distribution anyway.

---

### Post by szafran on 2012-09-28
This looks like it's fixed in 3.2.0-32-generic. Can someone confirm that ? (I've tested it on a separate VM, so I'd like to confirm before instaling on my NAS/Server).

Thanks in advance.

---

### Post by Xenefungus on 2012-10-18
It is definitely fixed now, yes :)

---


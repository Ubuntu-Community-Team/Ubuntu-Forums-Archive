---
title: "RAID and /dev/mapper"
date: 2010-11-01
forum: Server Platforms
---

### Post by minaev on 2010-11-01
Hello,

I have received a HP server with Ubuntu installed by someone else. There is Smart Array RAID controller installed there with cciss driver. And at the same time, there's device mapper configured:
```
$ ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 59 2010-08-25 19:01 control
brw-rw---- 1 root disk 251,  0 2010-08-25 19:01 okd-root
brw-rw---- 1 root disk 251,  1 2010-08-25 19:01 okd-swap_1
$ ls -l /dev/cciss/
total 0
brw-rw---- 1 root disk 104, 0 2010-08-25 19:01 c0d0
brw-rw---- 1 root disk 104, 1 2010-08-25 19:01 c0d0p1
brw-rw---- 1 root disk 104, 2 2010-08-25 19:01 c0d0p2
brw-rw---- 1 root disk 104, 5 2010-08-25 19:01 c0d0p5
$ mount
/dev/mapper/okd-root on / type ext4 (rw,errors=remount-ro)
...
/dev/cciss/c0d0p1 on /boot type ext2 (rw)
```
Will the performance suffer? Should I reinstall OS or this configuration is acceptable?

Thank you.

---

### Post by minaev on 2010-11-02
Anyone, please?

---

### Post by sherl0k on 2010-11-02
I'd say if it works, keep using it. If you're worried about performance, run some hdparm tests and see what your theoretical maximum throughput is. Then compare it to your real-world application results - whether it be network utilization, or simply watching it through atop/iotop during busy hours.

Personally I go the software route, utilizing btrfs' built-in RAID. I go to start from scratch, though.

---

### Post by minaev on 2010-11-03
Thank you, Sherl0k. What I'm certain about is that hardware RAID is a must on my servers. Its battery-backed cache can provide a higher performance than that of software-only RAID. I was rather thinking about dropping LVM in favor of pure hardware implementation. From what I found in various sources, I thought, yes, as you said, I would better leave it as it is.

Firstly, the performance penalty is negligible. Secondly, LVM allows for more flexible volume management (like, removal of a PV, moving PEs to the free space in the VG). Thirdly, snapshots. And, finally, portability of LVM volumes between incompatible hardware (this won't work for me, I'm afraid, because of the underlying hardware RAID1).

Besides, this LVM over RAID approach seems to be a common thing now and nobody seems to have complained about it :).

---


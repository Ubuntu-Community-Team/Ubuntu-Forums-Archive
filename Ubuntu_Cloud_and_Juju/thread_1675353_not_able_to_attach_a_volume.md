---
title: "not able to attach a volume"
date: 2011-01-25
forum: Ubuntu Cloud and Juju
---

### Post by mcanonic on 2011-01-25
Hi,
form UEC I have downloaded and installed the first image available in the store (Ubuntu 9.10 - Karmic Koala (i386)).

I am able to start an instance and I'm able to enter with ssh. Now I was trying to attach a volume
```

euca-attach-volume -i i-476B092C -d /dev/sdb vol-59CF062D

```
but even if the volume status is "in use":
```

VOLUME  vol-59CF062D     1              cluster1        in-use  2011-01-25T15:28:52.174Z
ATTACHMENT      vol-59CF062D    i-476B092C      /dev/sdb        2011-01-25T16:29:27.848Z

```

once I am in the VM, I cannot see it:
```

ubuntu@172:~$ sudo fdisk -l

Disk /dev/sda: 5416 MB, 5416943616 bytes
4 heads, 32 sectors/track, 82656 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x000b3889

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       32769     2097152+  83  Linux
/dev/sda2           32769       71910     2505000+  83  Linux
/dev/sda3           71910       82656      687799+  82  Linux swap / Solaris

```

I have tried to change the dev where to attach the volume (sdc,sg0,...) with no luck. The dmesg on NC says
```

[17818.591431] sd 8:0:0:1: [sdb] 2097152 512-byte logical blocks: (1.07 GB/1.00 GiB)
[17818.592120] sd 8:0:0:1: [sdb] Write Protect is off
[17818.592126] sd 8:0:0:1: [sdb] Mode Sense: 49 00 00 08
[17818.592512] sd 8:0:0:1: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[17818.593898]  sdb: unknown partition table
[17818.597448] sd 8:0:0:1: [sdb] Attached SCSI disk
[17820.103092] type=1400 audit(1295972973.653:30): apparmor="STATUS" operation="profile_replace" name="libvirt-4560b5a1-833c-18bd-a2b6-cee14fca78a3" pid=10467 comm="apparmor_parser"

```

Any suggestion?

Thanks,
 Massimo

---

### Post by kim0 on 2011-01-25
Hi,
Can you try

sudo partprobe

If that doesn't help. What about rebooting the instance?

Regards

---

### Post by mcanonic on 2011-01-26
Actually the problem seems a known bug:
[https://bugs.launchpad.net/ubuntu/karmic/+source/eucalyptus/+bug/432154](https://bugs.launchpad.net/ubuntu/karmic/+source/eucalyptus/+bug/432154)

I just had to specify /dev/vda and I can see my volume attached to the instance.

Thanks,
 M

---


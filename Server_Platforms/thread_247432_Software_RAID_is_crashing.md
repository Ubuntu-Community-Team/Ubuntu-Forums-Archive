---
title: "Software RAID is crashing"
date: 2006-08-30
forum: Server Platforms
---

### Post by cleentrax on 2006-08-30
I am setting up a home storage server with 4 ata drives in a raid 5 array, and one additional boot drive. I followed this guide [http://www.evileyez.org/quick-and-dirty-linux-software-raid5/]("http://www.evileyez.org/quick-and-dirty-linux-software-raid5/") and it mostly works, but the RAID 5 crashes when it gets about 91% through its resync process. Resync takes about two hours, and so that's my up time. When it crashes and I reboot, resync starts over from scratch.

I can see the raid array, mount it, copy files to it, etc. It just won't stay running!

Edit:

```
$ cat /proc/mdstat
Personalities : [raid5]
md0 : active raid5 hde1[0] hdc1[3] hdb1[2] hdg1[1]
      937705728 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [=========>...........]  resync = 46.7% (146098944/312568576) finish=140.4min speed=19755K/sec
```

```

$ fdisk -l
Disk /dev/hde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/hdg: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/hda: 18.0 GB, 18042716160 bytes
255 heads, 63 sectors/track, 2193 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2100    16868218+  83  Linux
/dev/hda2            2101        2193      747022+   5  Extended
/dev/hda5            2101        2193      746991   82  Linux swap / Solaris

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/md0: 960.2 GB, 960210665472 bytes
2 heads, 4 sectors/track, 234426432 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   b  W95 FAT32

```

---


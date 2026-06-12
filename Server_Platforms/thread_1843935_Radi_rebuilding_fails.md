---
title: "Radi rebuilding fails"
date: 2011-09-14
forum: Server Platforms
---

### Post by Krumpir on 2011-09-14
Hello there.

I have a mirror raid, two partitions, md0 and md1
md0 is 2730944 blocks and works flawlessly.
md1 is 153557184 blocks and constantly restarts the rebuilding process at about 25%...

daemon.log says the following:

```
Sep 14 10:59:33 www mdadm: RebuildStarted event detected on md device /dev/md1
Sep 14 12:04:05 www mdadm: Rebuild20 event detected on md device /dev/md1
Sep 14 12:13:40 www mdadm: RebuildFinished event detected on md device /dev/md1
Sep 14 12:13:40 www mdadm: RebuildStarted event detected on md device /dev/md1
Sep 14 12:54:47 www mdadm: Rebuild20 event detected on md device /dev/md1
Sep 14 13:06:55 www mdadm: RebuildFinished event detected on md device /dev/md1
Sep 14 13:06:56 www mdadm: RebuildStarted event detected on md device /dev/md1
Sep 14 14:15:35 www mdadm: Rebuild20 event detected on md device /dev/md1

```

dmesg says:
```

[    0.000000] Kernel command line: root=/dev/md1 ro quiet splash
[  107.770981] md: linear personality registered for level -1
[  107.778072] md: multipath personality registered for level -4
[  107.784966] md: raid0 personality registered for level 0
[  107.792782] md: raid1 personality registered for level 1
[  109.539954] md: raid6 personality registered for level 6
[  109.539957] md: raid5 personality registered for level 5
[  109.539959] md: raid4 personality registered for level 4
[  109.573231] md: raid10 personality registered for level 10
[  110.238655] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x7040 irq 14
[  110.238664] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x7048 irq 15
[  111.159021] md: md0 stopped.
[  111.429693] md: bind<sda1>
[  111.439962] raid1: raid set md0 active with 1 out of 2 mirrors
[  111.440237] md: md1 stopped.
[  111.486358] md: md1 stopped.
[  111.683065] md: bind<sda2>
[  111.693291] raid1: raid set md1 active with 1 out of 2 mirrors
[  118.777086] Adding 2730936k swap on /dev/md0.  Priority:-1 extents:1 across:2730936k
[  119.403953] EXT3 FS on md1, internal journal


```

Syslog and messages doesn't say anything...

Any ideas?

Greetings from Croatia!

---

### Post by rubylaser on 2011-09-14
What's the output of
```
cat /proc/mdstat
```

Both mirrors are reporting that they're active with 1 of 2 mirror devices. This means each are missing a disk. It sounds like one of your hard drives has failed.

```
[  111.439962] **raid1: raid set md0 active with 1 out of 2 mirrors**
[  111.440237] md: md1 stopped.
[  111.486358] md: md1 stopped.
[  111.683065] md: bind<sda2>
[  111.693291] **raid1: raid set md1 active with 1 out of 2 mirrors**
```

---

### Post by McJagger on 2011-09-15
```
root@www:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[2] sda2[0]
      153557184 blocks [2/1] [U_]
      [===>.................]  recovery = 16.9% (26021440/153557184) finish=128.9min speed=16484K/sec

md0 : active raid1 sdb1[1] sda1[0]
      2730944 blocks [2/2] [UU]

unused devices: <none>

```

---

### Post by rubylaser on 2011-09-15
It it's the same disk that gets kicked out, it sounds like you have some bad sectors.  I'd probably remove that partition from the array, write zeros to that partition, zero the superblock and then add the disk back the array.  If it happened again, I'd replace the disk.

---

### Post by McJagger on 2011-09-24
Thankx for the tip, but the problem is that I can't stop the rebuild... id just starts over and doesn't fail the disk...

---

### Post by Vegan on 2011-09-24
Best bet is to find a replacement disk

---

### Post by rubylaser on 2011-09-24
Well, that's not too bad, just fail the disk, and remove it.
```
mdadm --manage /dev/md1 --fail /dev/sdb2
```
```
mdadm --manage /dev/md1 --remove /dev/sdb2
```
**^^ If that's the bad device.**

Also, you'll need to do that on your other array, because it's using the same disk.
```
mdadm --manage /dev/md0 --fail /dev/sdb1
```
```
mdadm --manage /dev/md0 --remove /dev/sdb1
```

Shut down the machine remove the disk, and you should be able to add a replacement back after that.

---


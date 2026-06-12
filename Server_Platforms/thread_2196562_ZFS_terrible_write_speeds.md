---
title: "ZFS terrible write speeds"
date: 2013-12-30
forum: Server Platforms
---

### Post by de0xyrib0se on 2013-12-30
Hi all,

I have a 2TB mirror (2 x 2TB drives). Write speeds vary greatly and most of the time are depressingly slow (2MB/s), using dd to write 1MB blocks. ZFS is running as [COLOR="#FF0000"]**_kernel module_**[/COLOR].

The pool shows a healthy status, I'm open to suggestions (its as if some buffer maxes out, memory looks ok during writes);

1MB writes;

```

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 0.00893558 s, 1.2 GB/s

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 2.68938 s, 3.9 MB/s

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 0.0293087 s, 358 MB/s

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 0.948158 s, 11.1 MB/s

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 0.00444563 s, 2.4 GB/s

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 0.00442895 s, 2.4 GB/s

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 0.00442018 s, 2.4 GB/s

~# dd if=/dev/zero of=/zp01/users/test.out bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 2.75375 s, 3.8 MB/s

```

The pool status is bellow;

```
  pool: zp01
 state: ONLINE
  scan: none requested
config:

        NAME                        STATE     READ WRITE CKSUM
        zp01                        ONLINE       0     0     0
          mirror-0                  ONLINE       0     0     0
            scsi-35000c50025b7390b  ONLINE       0     0     0
            scsi-35000c50025b74bc7  ONLINE       0     0     0

```

Parameters for the pool are bellow;

```
~# zpool get all zp01
NAME  PROPERTY               VALUE                  SOURCE
zp01  size                   1.81T                  -
zp01  capacity               15%                    -
zp01  altroot                -                      default
zp01  health                 ONLINE                 -
zp01  guid                   15179149365591631903   default
zp01  version                -                      default
zp01  bootfs                 -                      default
zp01  delegation             on                     default
zp01  autoreplace            off                    default
zp01  cachefile              -                      default
zp01  failmode               wait                   default
zp01  listsnapshots          off                    default
zp01  autoexpand             off                    default
zp01  dedupditto             0                      default
zp01  dedupratio             1.00x                  -
zp01  free                   1.54T                  -
zp01  allocated              283G                   -
zp01  readonly               off                    -
zp01  ashift                 0                      default
zp01  comment                -                      default
zp01  expandsize             0                      -
zp01  freeing                0                      default
zp01  feature@async_destroy  enabled                local
zp01  feature@empty_bpobj    active                 local
zp01  feature@lz4_compress   enabled                local

```

---

### Post by tgalati4 on 2013-12-30
It could be instrumentation error.  Install *htop* and watch it in another terminal while you are performing your tests.  How much RAM on this system?  The fast speeds could simply be cache reads/writes (from RAM only), so they give a false impression of fast disk speed.  ZFS can be slow under certain workloads--looks like you found one.  Compare to a simple ext4 drive.

---

### Post by de0xyrib0se on 2013-12-30
I've been watching htop and iotop during writes and memory and CPU load is very low. 8 cores and 16GB of memory are plenty for ZFS. I did notice however a process 'txg_sync', which shows an IO% of 99.99 in iotop with very low actual writes to disk. Seems that is the culprit because if I do smaller size writes, say 5 or 10 meg total its always very fast and 'txg_sync' shows lower IO% on them.

Just to clarify, there is nothing using the mirror besides my test, not like there are a dozen writes concurrent.

---

### Post by de0xyrib0se on 2013-12-30
Somehow sync=standard is being interpreted as 'always on'. Not sure if this is a bug in the Linux port but tried writing with various methods including dd and its always the same.

---

### Post by tgalati4 on 2013-12-30
Is this test through a virtual machine?  I found some instances where vm's and sync don't get along:

[http://forums.freenas.org/threads/some-insights-into-slog-zil-with-zfs-on-freenas.13633/](http://forums.freenas.org/threads/some-insights-into-slog-zil-with-zfs-on-freenas.13633/)

[http://www.nexentastor.org/boards/2/topics/5662](http://www.nexentastor.org/boards/2/topics/5662)

Try booting *freenas* on a USB flash drive and perform your tests.

---

### Post by de0xyrib0se on 2014-01-02
Actually it turned out the problem is not ZFS but the hard drives. They have a throttle based on temperature and the fan right above them had burned out. They were running at >60-65C. Replacing the fan and spacing them out got the temps down to 38-40C and speed is where it should be now at 140MB/s which is their actual throughput.

Seagate SAS drives have this built-in, Hitachi doesn't. My 15K Hitachi will run at full speed at 70C.

---

### Post by tgalati4 on 2014-01-02
You didn't tell us about the smoke.

---


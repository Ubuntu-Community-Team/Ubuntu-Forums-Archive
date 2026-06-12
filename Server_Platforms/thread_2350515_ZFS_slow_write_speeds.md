---
title: "ZFS slow write speeds"
date: 2017-01-25
forum: Server Platforms
---

### Post by PatricF on 2017-01-25
Hi,

I have a HP ProLiant ML350 G6 with two Intel Xeon E5606 CPUs and 64GB of RAM.
I have connected 6x WesternDigital Black 2TB drives in the SATA-connectors on the motherboard.
I made a raidz ZFS pool with all six drives but I'm having a little problem with the write performance.

If I run this: ```
dd if=/dev/zero of=testfile conv=fdatasync bs=384k count=1k
```
I get:

> 
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 5.22462 s, **20.1 MB/s**
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 1.73841 s, **60.3 MB/s**
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 1.41069 s, **74.3 MB/s**
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 1.30766 s, **80.2 MB/s**
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 1.97408 s, **53.1 MB/s**
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 1.20755 s, **86.8 MB/s**
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 1.44293 s, **72.7 MB/s**
root@SERVER:/tank# dd if=/dev/zero of=testfile conv=fdatasync bs=100k count=1k
1024+0 records in
1024+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 3.13647 s, **33.4 MB/s**


First of all it jumps up and down pretty much. Second of all, shouldn't I get more write speed when having 6 drives in raidz or is this normal?
If I run the same dd command on a ext4 formated drive I get around 40-50MB/s.

And when I try to copy files from a faster drive to the zpool I get terrible performance. It's usually around 15MB/s and pauses sometimes, then it can go faster for a while and then pauses again etc.
This is the sector size of every disk: [B]Sector size (logical/physical): 512 bytes / 512 bytes
[/B]This is the block size of every disk (blockdev --getbsz /dev/sdb1):** 4096**
They seem to run in 3.0Gb/s mode: [B]SATA Version is:  SATA 2.6, 6.0 Gb/s (current: 3.0 Gb/s)

[/B]This pool is going to be used with rTorrent. When I download a torrent which I know can get high speed from it can go up to 90MB/s and then it just hangs and drops down to 10MB/s for a while and climbs up to around 30MB where it stays until it's done.
I have a 1Gbit connection btw. If I try it on my other HP drive (hot-swap 900GB 10k rpm non-raid) I get up to around the same top speed but it stays up there until it's done and doesn't hang or anything.

Does anyone know why the pool hangs like that? It is the drives or the controller maybe? Or is is something with ZFS itself?

---

### Post by raja.genupula on 2017-01-25
should I say , you didnt mention what RAID level you are using. 

Because disk writing/reading performance varies as per RAID level. 

Regards
Raja

---

### Post by PatricF on 2017-01-25
raidz1 (RAID-5)
```
zpool create -f tank raidz1 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf
```

---

### Post by raja.genupula on 2017-01-25
Have you enabled compression[lzjb/lz4 ? 

and what is the output of **zpool status **?

---

### Post by PatricF on 2017-01-25
```
root@SERVER:/tank/TV# zpool status
  pool: tank
 state: ONLINE
  scan: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        tank        ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sda     ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sde     ONLINE       0     0     0
            sdf     ONLINE       0     0     0

errors: No known data errors
```

```
[COLOR=#000000]root@SERVER:/tank/TV# zfs get all
[/COLOR]NAME  PROPERTY              VALUE                  SOURCE
tank  type                  filesystem             -
tank  creation              Sun Jan 22 20:47 2017  -
tank  used                  729G                   -
tank  available             8.03T                  -
tank  referenced            729G                   -
tank  compressratio         1.00x                  -
tank  mounted               yes                    -
tank  quota                 none                   default
tank  reservation           none                   default
tank  recordsize            128K                   default
tank  mountpoint            /tank                  default
tank  sharenfs              off                    default
tank  checksum              on                     default
tank  compression           off                    default
tank  atime                 on                     default
tank  devices               on                     default
tank  exec                  on                     default
tank  setuid                on                     default
tank  readonly              off                    default
tank  zoned                 off                    default
tank  snapdir               hidden                 default
tank  aclinherit            restricted             default
tank  canmount              on                     default
tank  xattr                 on                     default
tank  copies                1                      default
tank  version               5                      -
tank  utf8only              off                    -
tank  normalization         none                   -
tank  casesensitivity       sensitive              -
tank  vscan                 off                    default
tank  nbmand                off                    default
tank  sharesmb              off                    default
tank  refquota              none                   default
tank  refreservation        none                   default
tank  primarycache          all                    default
tank  secondarycache        all                    default
tank  usedbysnapshots       0                      -
tank  usedbydataset         729G                   -
tank  usedbychildren        4.64M                  -
tank  usedbyrefreservation  0                      -
tank  logbias               latency                default
tank  dedup                 off                    default
tank  mlslabel              none                   default
tank  sync                  standard               default
tank  refcompressratio      1.00x                  -
tank  written               729G                   -
tank  logicalused           730G                   -
tank  logicalreferenced     730G                   -
tank  filesystem_limit      none                   default
tank  snapshot_limit        none                   default
tank  filesystem_count      none                   default
tank  snapshot_count        none                   default
tank  snapdev               hidden                 default
tank  acltype               off                    default
tank  context               none                   default
tank  fscontext             none                   default
tank  defcontext            none                   default
tank  rootcontext           none                   default
tank  relatime              on                     temporary
tank  redundant_metadata    all                    default
tank  overlay               off                    default[COLOR=#000000]
[/COLOR]
```

---


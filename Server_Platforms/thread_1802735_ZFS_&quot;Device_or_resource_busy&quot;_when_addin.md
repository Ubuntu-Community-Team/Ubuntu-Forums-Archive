---
title: "ZFS &quot;Device or resource busy&quot; when adding spare to multiple zpools"
date: 2011-07-12
forum: Server Platforms
---

### Post by matthewthacker on 2011-07-12
Running (trying anyway) ZFS on Ubuntu Server Natty and I can't seem to figure out how to add a hot spare to multiple pools. I've used up the depth and breadth of my google-fu and cannot find any help. Anyone got any ideas on this?

Thanks! 

Here's the gist:
```
root>zpool create tank1 -f raidz /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS2ZMCY /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS320R8 /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS320SF /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS35ZF3 /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS3G816
root>zpool create tank2 -f raidz /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS3G9YV /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS44KQ8 /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS49YRT /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4AS8W /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4AZYH
root>zpool add tank1 spare -f /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K 
root>zpool add tank2 spare -f /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K 
cannot open '/dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K': Device or resource busy

```

Some more info:
```
root>zpool upgrade
This system is currently running ZFS pool version 28.

All pools are formatted using this version.
root>zfs upgrade
This system is currently running ZFS filesystem version 5.

All filesystems are formatted with the current version.
root>zpool status
  pool: tank1
 state: ONLINE
 scan: none requested
config:

        NAME                                 STATE     READ WRITE CKSUM
        tank1                                ONLINE       0     0     0
          raidz1-0                           ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS2ZMCY  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS320R8  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS320SF  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS35ZF3  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS3G816  ONLINE       0     0     0
        spares
          scsi-SATA_ST31500341AS_9VS4BA2K    AVAIL   

errors: No known data errors

  pool: tank2
 state: ONLINE
 scan: none requested
config:

        NAME                                 STATE     READ WRITE CKSUM
        tank2                                ONLINE       0     0     0
          raidz1-0                           ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS3G9YV  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS44KQ8  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS49YRT  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS4AS8W  ONLINE       0     0     0
            scsi-SATA_ST31500341AS_9VS4AZYH  ONLINE       0     0     0

errors: No known data errors
root>zfs get all
NAME   PROPERTY              VALUE                  SOURCE
tank1  type                  filesystem             -
tank1  creation              Tue Jul 12  8:45 2011  -
tank1  used                  125K                   -
tank1  available             5.36T                  -
tank1  referenced            33.6K                  -
tank1  compressratio         1.00x                  -
tank1  mounted               yes                    -
tank1  quota                 none                   default
tank1  reservation           none                   default
tank1  recordsize            128K                   default
tank1  mountpoint            /tank1                 default
tank1  sharenfs              off                    default
tank1  checksum              on                     default
tank1  compression           off                    default
tank1  atime                 on                     default
tank1  devices               on                     default
tank1  exec                  on                     default
tank1  setuid                on                     default
tank1  readonly              off                    default
tank1  zoned                 off                    default
tank1  snapdir               hidden                 default
tank1  aclinherit            restricted             default
tank1  canmount              on                     default
tank1  xattr                 on                     default
tank1  copies                1                      default
tank1  version               5                      -
tank1  utf8only              off                    -
tank1  normalization         none                   -
tank1  casesensitivity       sensitive              -
tank1  vscan                 off                    default
tank1  nbmand                off                    default
tank1  sharesmb              off                    default
tank1  refquota              none                   default
tank1  refreservation        none                   default
tank1  primarycache          all                    default
tank1  secondarycache        all                    default
tank1  usedbysnapshots       0                      -
tank1  usedbydataset         33.6K                  -
tank1  usedbychildren        91.1K                  -
tank1  usedbyrefreservation  0                      -
tank1  logbias               latency                default
tank1  dedup                 off                    default
tank1  mlslabel              none                   default
tank1  sync                  standard               default
tank2  type                  filesystem             -
tank2  creation              Tue Jul 12  8:45 2011  -
tank2  used                  120K                   -
tank2  available             5.36T                  -
tank2  referenced            33.6K                  -
tank2  compressratio         1.00x                  -
tank2  mounted               yes                    -
tank2  quota                 none                   default
tank2  reservation           none                   default
tank2  recordsize            128K                   default
tank2  mountpoint            /tank2                 default
tank2  sharenfs              off                    default
tank2  checksum              on                     default
tank2  compression           off                    default
tank2  atime                 on                     default
tank2  devices               on                     default
tank2  exec                  on                     default
tank2  setuid                on                     default
tank2  readonly              off                    default
tank2  zoned                 off                    default
tank2  snapdir               hidden                 default
tank2  aclinherit            restricted             default
tank2  canmount              on                     default
tank2  xattr                 on                     default
tank2  copies                1                      default
tank2  version               5                      -
tank2  utf8only              off                    -
tank2  normalization         none                   -
tank2  casesensitivity       sensitive              -
tank2  vscan                 off                    default
tank2  nbmand                off                    default
tank2  sharesmb              off                    default
tank2  refquota              none                   default
tank2  refreservation        none                   default
tank2  primarycache          all                    default
tank2  secondarycache        all                    default
tank2  usedbysnapshots       0                      -
tank2  usedbydataset         33.6K                  -
tank2  usedbychildren        86.3K                  -
tank2  usedbyrefreservation  0                      -
tank2  logbias               latency                default
tank2  dedup                 off                    default
tank2  mlslabel              none                   default
tank2  sync                  standard               default
root>uname -a
Linux 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

Even and strace if it'll help:
```
root>strace zpool add tank1 spare -f /dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K 2>&1
execve("/usr/sbin/zpool", ["zpool", "add", "tank1", "spare", "-f", "/dev/disk/by-id/scsi-SATA_ST3150"...], [/* 22 vars */]) = 0
brk(0)                                  = 0x724000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c7f000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=18270, ...}) = 0
mmap(NULL, 18270, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6b44c7a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libspl.so.0", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`+\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=22648, ...}) = 0
mmap(NULL, 2122128, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b4485a000
mprotect(0x7f6b4485f000, 2093056, PROT_NONE) = 0
mmap(0x7f6b44a5e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4000) = 0x7f6b44a5e000
mmap(0x7f6b44a60000, 400, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6b44a60000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libavl.so.0", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\7\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10016, ...}) = 0
mmap(NULL, 2105376, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b44657000
mprotect(0x7f6b44659000, 2093056, PROT_NONE) = 0
mmap(0x7f6b44858000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7f6b44858000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libefi.so.0", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\r\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=18864, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c79000
mmap(NULL, 2114232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b44452000
mprotect(0x7f6b44456000, 2093056, PROT_NONE) = 0
mmap(0x7f6b44655000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0x7f6b44655000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libnvpair.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2004\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=59560, ...}) = 0
mmap(NULL, 2154840, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b44243000
mprotect(0x7f6b44250000, 2097152, PROT_NONE) = 0
mmap(0x7f6b44450000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd000) = 0x7f6b44450000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libunicode.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\10\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=325440, ...}) = 0
mmap(NULL, 2420800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b43ff3000
mprotect(0x7f6b44042000, 2093056, PROT_NONE) = 0
mmap(0x7f6b44241000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4e000) = 0x7f6b44241000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libuutil.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@%\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=39752, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c78000
mmap(NULL, 2135400, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b43de9000
mprotect(0x7f6b43df1000, 2097152, PROT_NONE) = 0
mmap(0x7f6b43ff1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8000) = 0x7f6b43ff1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libzpool.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\206\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=746912, ...}) = 0
mmap(NULL, 2892248, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b43b26000
mprotect(0x7f6b43bd8000, 2097152, PROT_NONE) = 0
mmap(0x7f6b43dd8000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xb2000) = 0x7f6b43dd8000
mmap(0x7f6b43ddc000, 49624, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6b43ddc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libzfs.so.0", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300s\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=220720, ...}) = 0
mmap(NULL, 2316104, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b438f0000
mprotect(0x7f6b43925000, 2093056, PROT_NONE) = 0
mmap(0x7f6b43b24000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x34000) = 0x7f6b43b24000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360>\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=543104, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c77000
mmap(NULL, 2638136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b4366b000
mprotect(0x7f6b436ef000, 2093056, PROT_NONE) = 0
mmap(0x7f6b438ee000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x83000) = 0x7f6b438ee000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\r\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14696, ...}) = 0
mmap(NULL, 2109720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b43467000
mprotect(0x7f6b43469000, 2097152, PROT_NONE) = 0
mmap(0x7f6b43669000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f6b43669000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/librt.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220!\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31752, ...}) = 0
mmap(NULL, 2129000, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b4325f000
mprotect(0x7f6b43266000, 2093056, PROT_NONE) = 0
mmap(0x7f6b43465000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f6b43465000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libuuid.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\24\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=18880, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c76000
mmap(NULL, 2113928, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b4305a000
mprotect(0x7f6b4305e000, 2093056, PROT_NONE) = 0
mmap(0x7f6b4325d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0x7f6b4325d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P \0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=96816, ...}) = 0
mmap(NULL, 2191920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b42e42000
mprotect(0x7f6b42e59000, 2093056, PROT_NONE) = 0
mmap(0x7f6b43058000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f6b43058000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\\\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=140254, ...}) = 0
mmap(NULL, 2217000, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b42c24000
mprotect(0x7f6b42c3c000, 2097152, PROT_NONE) = 0
mmap(0x7f6b42e3c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18000) = 0x7f6b42e3c000
mmap(0x7f6b42e3e000, 13352, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6b42e3e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\360\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1638120, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c75000
mmap(NULL, 3749080, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6b42890000
mprotect(0x7f6b42a1a000, 2093056, PROT_NONE) = 0
mmap(0x7f6b42c19000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x189000) = 0x7f6b42c19000
mmap(0x7f6b42c1e000, 21720, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6b42c1e000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c74000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c72000
arch_prctl(ARCH_SET_FS, 0x7f6b44c72b80) = 0
mprotect(0x7f6b42c19000, 16384, PROT_READ) = 0
mprotect(0x7f6b42e3c000, 4096, PROT_READ) = 0
mprotect(0x7f6b43058000, 4096, PROT_READ) = 0
mprotect(0x7f6b4325d000, 4096, PROT_READ) = 0
mprotect(0x7f6b43465000, 4096, PROT_READ) = 0
mprotect(0x7f6b43669000, 4096, PROT_READ) = 0
mprotect(0x7f6b438ee000, 4096, PROT_READ) = 0
mprotect(0x7f6b43b24000, 4096, PROT_READ) = 0
mprotect(0x7f6b43dd8000, 4096, PROT_READ) = 0
mprotect(0x7f6b43ff1000, 4096, PROT_READ) = 0
mprotect(0x7f6b44241000, 4096, PROT_READ) = 0
mprotect(0x7f6b44450000, 4096, PROT_READ) = 0
mprotect(0x7f6b44655000, 4096, PROT_READ) = 0
mprotect(0x7f6b44858000, 4096, PROT_READ) = 0
mprotect(0x7f6b44a5e000, 4096, PROT_READ) = 0
mprotect(0x617000, 4096, PROT_READ)     = 0
mprotect(0x7f6b44c81000, 4096, PROT_READ) = 0
munmap(0x7f6b44c7a000, 18270)           = 0
set_tid_address(0x7f6b44c72e50)         = 4698
set_robust_list(0x7f6b44c72e60, 0x18)   = 0
futex(0x7fff5100fecc, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x7fff5100fecc, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, 7f6b44c72b80) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0x7f6b42c29740, [], SA_RESTORER|SA_SIGINFO, 0x7f6b42c33c60}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x7f6b42c297d0, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7f6b42c33c60}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
futex(0x7f6b4366a0e0, FUTEX_WAKE_PRIVATE, 2147483647) = 0
brk(0)                                  = 0x724000
brk(0x745000)                           = 0x745000
open("/usr/lib//libshare.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/locale-archive", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1534640, ...}) = 0
mmap(NULL, 1534640, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6b44afb000
close(3)                                = 0
open("/proc/modules", O_RDONLY)         = 3
fstat(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44c7e000
read(3, "zfs 1017037 2 - Live 0xffffffffa"..., 1024) = 1024
close(3)                                = 0
munmap(0x7f6b44c7e000, 4096)            = 0
open("/dev/zfs", O_RDWR)                = 3
open("/etc/mtab", O_RDONLY)             = 4
open("/etc/dfs/sharetab", O_RDONLY)     = -1 ENOENT (No such file or directory)
ioctl(3, 0x5a05, 0x7fff510077f0)        = 0
lstat("/dev", {st_mode=S_IFDIR|0755, st_size=6160, ...}) = 0
lstat("/dev/disk", {st_mode=S_IFDIR|0755, st_size=100, ...}) = 0
lstat("/dev/disk/by-id", {st_mode=S_IFDIR|0755, st_size=4780, ...}) = 0
lstat("/dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K", {st_mode=S_IFLNK|0777, st_size=9, ...}) = 0
readlink("/dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K", "../../sdv", 4095) = 9
lstat("/dev/sdv", {st_mode=S_IFBLK|0660, st_rdev=makedev(65, 80), ...}) = 0
open("/dev/sdv", O_RDWR|O_EXCL|O_DIRECT) = -1 EBUSY (Device or resource busy)
stat("/dev/sdv", {st_mode=S_IFBLK|0660, st_rdev=makedev(65, 80), ...}) = 0
stat("/dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K", {st_mode=S_IFBLK|0660, st_rdev=makedev(65, 80), ...}) = 0
open("/dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K", O_RDONLY) = 5
fstat(5, {st_mode=S_IFBLK|0660, st_rdev=makedev(65, 80), ...}) = 0
mmap(NULL, 266240, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44aba000
pread(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 262144, 0) = 262144
pread(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 262144, 262144) = 262144
munmap(0x7f6b44aba000, 266240)          = 0
brk(0x769000)                           = 0x769000
ioctl(3, 0x5a05, 0x7fff51003410)        = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 6
fstat(6, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6b44afa000
read(6, "# Locale name alias data base.\n#"..., 4096) = 2570
read(6, "", 4096)                       = 0
close(6)                                = 0
munmap(0x7f6b44afa000, 4096)            = 0
open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/zfs-linux-user.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
close(5)                                = 0
open("/dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K", O_WRONLY|O_EXCL) = -1 EBUSY (Device or resource busy)
open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "cannot open '/dev/disk/by-id/scs"..., 87cannot open '/dev/disk/by-id/scsi-SATA_ST31500341AS_9VS4BA2K': Device or resource busy
) = 87
close(3)                                = 0
close(4)                                = 0
exit_group(1)                           = ?
```

---


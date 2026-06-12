---
title: "ZFS low write bandwidth [SOLVED]"
date: 2014-09-06
forum: Server Platforms
---

### Post by totor55 on 2014-09-06
Hi All

I have installed a home server with ZFS.

I have very low write bandwidth, slowly grows, but remains very low (K's).

I have searched quite a lot on the net and forums about this but I have had no luck, so I am looking  for some help.

I will edit this post on an on-going basis with answers to all questions asked so that nobody needs to reread the entire thread.

Sysinfo:
```

SYSTEM INFORMATION
    Running Ubuntu Linux, the Ubuntu 14.04 (trusty) release.
    GNOME: 3.8.4 (Ubuntu 2014-03-17)
    Kernel version: 3.13.0-35-generic (#62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014)
    GCC: 4.8 (x86_64-linux-gnu)
    Xorg: 1.15.1 (16 April 2014  01:36:29PM)
    Hostname: serveur
    Uptime: 1 days 2 h 38 min


CPU INFORMATION
    GenuineIntel, Intel(R) Core(TM) i7-4770T CPU @ 2.50GHz
    Number of CPUs: 8
    CPU clock currently at 2501.000 MHz with 8192 KB cache
    Numbering: family(6) model(60) stepping(3)
    Bogomips: 5009.05
    Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm


MEMORY INFORMATION
    Total memory: 15732 MB
    Total swap: 38383 MB


STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  WDC WD40EFRX-68W 
    SCSI device -  scsi1
        Vendor:  ATA      
        Model:  WDC WD40EFRX-68W 
    SCSI device -  scsi2
        Vendor:  ATA      
        Model:  WDC WD40EFRX-68W 
    SCSI device -  scsi3
        Vendor:  ATA      
        Model:  WDC WD40EFRX-68W 
HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
        Subsystem: ASUSTeK Computer Inc. Device 8534
    PCI bridge(s)
        Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
        Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
        Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
    ISA bridge
        Intel Corporation Z87 Express LPC Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 8534
GRAPHIC CARD
SOUND CARD
NETWORK
    Network controller
        Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
        Subsystem: ASUSTeK Computer Inc. Device 855c
    Ethernet controller
        Intel Corporation Ethernet Connection I217-V (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 859f

```

Interestingly sysinfo does not show the SDD that I am booting from, which is connected via a PCI SATA extension card (as is the DVD player).

I list the full zfs attributes, but the most important part are: no dedup, no compression.

```

NAME                 USED  AVAIL  REFER  MOUNTPOINT
donnees              540G  9.84T   232K  /donnees
donnees/helene       198K  9.84T   198K  /donnees/helene
donnees/jerome       448G  9.84T   215K  /donnees/jerome
donnees/jerome/OS    448G  9.84T   448G  /donnees/jerome/OS
donnees/videos      91.5G  9.84T  31.6G  /donnees/videos
donnees/videos/15p  60.0G  9.84T  60.0G  /donnees/videos/15p
  pool: donnees
 state: ONLINE
  scan: scrub repaired 0 in 0h31m with 0 errors on Sat Sep  6 14:29:34 2014
config:


    NAME                        STATE     READ WRITE CKSUM
    donnees                     ONLINE       0     0     0
      raidz1-0                  ONLINE       0     0     0
        wwn-0x50014ee25f8d6030  ONLINE       0     0     0
        wwn-0x50014ee2b4361cf1  ONLINE       0     0     0
        wwn-0x50014ee25ee03f87  ONLINE       0     0     0
        wwn-0x50014ee2b4e348c8  ONLINE       0     0     0


errors: No known data errors
NAME                PROPERTY              VALUE                  SOURCE
donnees             type                  filesystem             -
donnees             creation              Sun Jul 13 14:43 2014  -
donnees             used                  540G                   -
donnees             available             9.84T                  -
donnees             referenced            232K                   -
donnees             compressratio         1.00x                  -
donnees             mounted               yes                    -
donnees             quota                 none                   default
donnees             reservation           none                   default
donnees             recordsize            128K                   default
donnees             mountpoint            /donnees               default
donnees             sharenfs              off                    default
donnees             checksum              on                     default
donnees             compression           off                    default
donnees             atime                 on                     default
donnees             devices               on                     default
donnees             exec                  on                     default
donnees             setuid                on                     default
donnees             readonly              off                    default
donnees             zoned                 off                    default
donnees             snapdir               hidden                 default
donnees             aclinherit            restricted             default
donnees             canmount              on                     default
donnees             xattr                 on                     default
donnees             copies                1                      default
donnees             version               5                      -
donnees             utf8only              off                    -
donnees             normalization         none                   -
donnees             casesensitivity       sensitive              -
donnees             vscan                 off                    default
donnees             nbmand                off                    default
donnees             sharesmb              off                    default
donnees             refquota              none                   default
donnees             refreservation        none                   default
donnees             primarycache          all                    default
donnees             secondarycache        all                    default
donnees             usedbysnapshots       0                      -
donnees             usedbydataset         232K                   -
donnees             usedbychildren        540G                   -
donnees             usedbyrefreservation  0                      -
donnees             logbias               latency                default
donnees             dedup                 off                    default
donnees             mlslabel              none                   default
donnees             sync                  standard               default
donnees             refcompressratio      1.00x                  -
donnees             written               232K                   -
donnees             logicalused           540G                   -
donnees             logicalreferenced     16.5K                  -
donnees             snapdev               hidden                 default
donnees             acltype               off                    default
donnees             context               none                   default
donnees             fscontext             none                   default
donnees             defcontext            none                   default
donnees             rootcontext           none                   default
donnees             relatime              off                    default
donnees/helene      type                  filesystem             -
donnees/helene      creation              Mon Sep  1 23:18 2014  -
donnees/helene      used                  198K                   -
donnees/helene      available             9.84T                  -
donnees/helene      referenced            198K                   -
donnees/helene      compressratio         1.00x                  -
donnees/helene      mounted               yes                    -
donnees/helene      quota                 none                   default
donnees/helene      reservation           none                   default
donnees/helene      recordsize            128K                   default
donnees/helene      mountpoint            /donnees/helene        default
donnees/helene      sharenfs              off                    default
donnees/helene      checksum              on                     default
donnees/helene      compression           off                    default
donnees/helene      atime                 on                     default
donnees/helene      devices               on                     default
donnees/helene      exec                  on                     default
donnees/helene      setuid                on                     default
donnees/helene      readonly              off                    default
donnees/helene      zoned                 off                    default
donnees/helene      snapdir               hidden                 default
donnees/helene      aclinherit            restricted             default
donnees/helene      canmount              on                     default
donnees/helene      xattr                 on                     default
donnees/helene      copies                1                      default
donnees/helene      version               5                      -
donnees/helene      utf8only              off                    -
donnees/helene      normalization         none                   -
donnees/helene      casesensitivity       sensitive              -
donnees/helene      vscan                 off                    default
donnees/helene      nbmand                off                    default
donnees/helene      sharesmb              off                    default
donnees/helene      refquota              none                   default
donnees/helene      refreservation        none                   default
donnees/helene      primarycache          all                    default
donnees/helene      secondarycache        all                    default
donnees/helene      usedbysnapshots       0                      -
donnees/helene      usedbydataset         198K                   -
donnees/helene      usedbychildren        0                      -
donnees/helene      usedbyrefreservation  0                      -
donnees/helene      logbias               latency                default
donnees/helene      dedup                 off                    default
donnees/helene      mlslabel              none                   default
donnees/helene      sync                  standard               default
donnees/helene      refcompressratio      1.00x                  -
donnees/helene      written               198K                   -
donnees/helene      logicalused           15K                    -
donnees/helene      logicalreferenced     15K                    -
donnees/helene      snapdev               hidden                 default
donnees/helene      acltype               off                    default
donnees/helene      context               none                   default
donnees/helene      fscontext             none                   default
donnees/helene      defcontext            none                   default
donnees/helene      rootcontext           none                   default
donnees/helene      relatime              off                    default
donnees/jerome      type                  filesystem             -
donnees/jerome      creation              Tue Aug  5 20:38 2014  -
donnees/jerome      used                  448G                   -
donnees/jerome      available             9.84T                  -
donnees/jerome      referenced            215K                   -
donnees/jerome      compressratio         1.00x                  -
donnees/jerome      mounted               yes                    -
donnees/jerome      quota                 none                   default
donnees/jerome      reservation           none                   default
donnees/jerome      recordsize            128K                   default
donnees/jerome      mountpoint            /donnees/jerome        default
donnees/jerome      sharenfs              off                    default
donnees/jerome      checksum              on                     default
donnees/jerome      compression           off                    default
donnees/jerome      atime                 on                     default
donnees/jerome      devices               on                     default
donnees/jerome      exec                  on                     default
donnees/jerome      setuid                on                     default
donnees/jerome      readonly              off                    default
donnees/jerome      zoned                 off                    default
donnees/jerome      snapdir               hidden                 default
donnees/jerome      aclinherit            restricted             default
donnees/jerome      canmount              on                     default
donnees/jerome      xattr                 on                     default
donnees/jerome      copies                1                      default
donnees/jerome      version               5                      -
donnees/jerome      utf8only              off                    -
donnees/jerome      normalization         none                   -
donnees/jerome      casesensitivity       sensitive              -
donnees/jerome      vscan                 off                    default
donnees/jerome      nbmand                off                    default
donnees/jerome      sharesmb              on                     local
donnees/jerome      refquota              none                   default
donnees/jerome      refreservation        none                   default
donnees/jerome      primarycache          all                    default
donnees/jerome      secondarycache        all                    default
donnees/jerome      usedbysnapshots       0                      -
donnees/jerome      usedbydataset         215K                   -
donnees/jerome      usedbychildren        448G                   -
donnees/jerome      usedbyrefreservation  0                      -
donnees/jerome      logbias               latency                default
donnees/jerome      dedup                 off                    local
donnees/jerome      mlslabel              none                   default
donnees/jerome      sync                  standard               default
donnees/jerome      refcompressratio      1.00x                  -
donnees/jerome      written               215K                   -
donnees/jerome      logicalused           448G                   -
donnees/jerome      logicalreferenced     18.5K                  -
donnees/jerome      snapdev               hidden                 default
donnees/jerome      acltype               off                    default
donnees/jerome      context               none                   default
donnees/jerome      fscontext             none                   default
donnees/jerome      defcontext            none                   default
donnees/jerome      rootcontext           none                   default
donnees/jerome      relatime              off                    default
donnees/jerome/OS   type                  filesystem             -
donnees/jerome/OS   creation              Tue Aug  5 21:42 2014  -
donnees/jerome/OS   used                  448G                   -
donnees/jerome/OS   available             9.84T                  -
donnees/jerome/OS   referenced            448G                   -
donnees/jerome/OS   compressratio         1.00x                  -
donnees/jerome/OS   mounted               yes                    -
donnees/jerome/OS   quota                 none                   default
donnees/jerome/OS   reservation           none                   default
donnees/jerome/OS   recordsize            128K                   default
donnees/jerome/OS   mountpoint            /donnees/jerome/OS     default
donnees/jerome/OS   sharenfs              off                    default
donnees/jerome/OS   checksum              on                     default
donnees/jerome/OS   compression           off                    default
donnees/jerome/OS   atime                 on                     default
donnees/jerome/OS   devices               on                     default
donnees/jerome/OS   exec                  on                     default
donnees/jerome/OS   setuid                on                     default
donnees/jerome/OS   readonly              off                    default
donnees/jerome/OS   zoned                 off                    default
donnees/jerome/OS   snapdir               hidden                 default
donnees/jerome/OS   aclinherit            restricted             default
donnees/jerome/OS   canmount              on                     default
donnees/jerome/OS   xattr                 on                     default
donnees/jerome/OS   copies                1                      default
donnees/jerome/OS   version               5                      -
donnees/jerome/OS   utf8only              off                    -
donnees/jerome/OS   normalization         none                   -
donnees/jerome/OS   casesensitivity       sensitive              -
donnees/jerome/OS   vscan                 off                    default
donnees/jerome/OS   nbmand                off                    default
donnees/jerome/OS   sharesmb              on                     inherited from donnees/jerome
donnees/jerome/OS   refquota              none                   default
donnees/jerome/OS   refreservation        none                   default
donnees/jerome/OS   primarycache          all                    default
donnees/jerome/OS   secondarycache        all                    default
donnees/jerome/OS   usedbysnapshots       0                      -
donnees/jerome/OS   usedbydataset         448G                   -
donnees/jerome/OS   usedbychildren        0                      -
donnees/jerome/OS   usedbyrefreservation  0                      -
donnees/jerome/OS   logbias               latency                default
donnees/jerome/OS   dedup                 off                    local
donnees/jerome/OS   mlslabel              none                   default
donnees/jerome/OS   sync                  standard               default
donnees/jerome/OS   refcompressratio      1.00x                  -
donnees/jerome/OS   written               448G                   -
donnees/jerome/OS   logicalused           448G                   -
donnees/jerome/OS   logicalreferenced     448G                   -
donnees/jerome/OS   snapdev               hidden                 default
donnees/jerome/OS   acltype               off                    default
donnees/jerome/OS   context               none                   default
donnees/jerome/OS   fscontext             none                   default
donnees/jerome/OS   defcontext            none                   default
donnees/jerome/OS   rootcontext           none                   default
donnees/jerome/OS   relatime              off                    default
donnees/videos      type                  filesystem             -
donnees/videos      creation              Mon Sep  1 23:18 2014  -
donnees/videos      used                  91.5G                  -
donnees/videos      available             9.84T                  -
donnees/videos      referenced            31.6G                  -
donnees/videos      compressratio         1.00x                  -
donnees/videos      mounted               yes                    -
donnees/videos      quota                 none                   default
donnees/videos      reservation           none                   default
donnees/videos      recordsize            128K                   default
donnees/videos      mountpoint            /donnees/videos        default
donnees/videos      sharenfs              off                    default
donnees/videos      checksum              on                     default
donnees/videos      compression           off                    default
donnees/videos      atime                 on                     default
donnees/videos      devices               on                     default
donnees/videos      exec                  on                     default
donnees/videos      setuid                on                     default
donnees/videos      readonly              off                    default
donnees/videos      zoned                 off                    default
donnees/videos      snapdir               hidden                 default
donnees/videos      aclinherit            restricted             default
donnees/videos      canmount              on                     default
donnees/videos      xattr                 on                     default
donnees/videos      copies                1                      default
donnees/videos      version               5                      -
donnees/videos      utf8only              off                    -
donnees/videos      normalization         none                   -
donnees/videos      casesensitivity       sensitive              -
donnees/videos      vscan                 off                    default
donnees/videos      nbmand                off                    default
donnees/videos      sharesmb              off                    default
donnees/videos      refquota              none                   default
donnees/videos      refreservation        none                   default
donnees/videos      primarycache          all                    default
donnees/videos      secondarycache        all                    default
donnees/videos      usedbysnapshots       0                      -
donnees/videos      usedbydataset         31.6G                  -
donnees/videos      usedbychildren        60.0G                  -
donnees/videos      usedbyrefreservation  0                      -
donnees/videos      logbias               latency                default
donnees/videos      dedup                 off                    default
donnees/videos      mlslabel              none                   default
donnees/videos      sync                  standard               default
donnees/videos      refcompressratio      1.00x                  -
donnees/videos      written               31.6G                  -
donnees/videos      logicalused           91.5G                  -
donnees/videos      logicalreferenced     31.6G                  -
donnees/videos      snapdev               hidden                 default
donnees/videos      acltype               off                    default
donnees/videos      context               none                   default
donnees/videos      fscontext             none                   default
donnees/videos      defcontext            none                   default
donnees/videos      rootcontext           none                   default
donnees/videos      relatime              off                    default
donnees/videos/15p  type                  filesystem             -
donnees/videos/15p  creation              Mon Sep  1 23:37 2014  -
donnees/videos/15p  used                  60.0G                  -
donnees/videos/15p  available             9.84T                  -
donnees/videos/15p  referenced            60.0G                  -
donnees/videos/15p  compressratio         1.00x                  -
donnees/videos/15p  mounted               yes                    -
donnees/videos/15p  quota                 none                   default
donnees/videos/15p  reservation           none                   default
donnees/videos/15p  recordsize            128K                   default
donnees/videos/15p  mountpoint            /donnees/videos/15p    default
donnees/videos/15p  sharenfs              off                    default
donnees/videos/15p  checksum              on                     default
donnees/videos/15p  compression           off                    default
donnees/videos/15p  atime                 on                     default
donnees/videos/15p  devices               on                     default
donnees/videos/15p  exec                  on                     default
donnees/videos/15p  setuid                on                     default
donnees/videos/15p  readonly              off                    default
donnees/videos/15p  zoned                 off                    default
donnees/videos/15p  snapdir               hidden                 default
donnees/videos/15p  aclinherit            restricted             default
donnees/videos/15p  canmount              on                     default
donnees/videos/15p  xattr                 on                     default
donnees/videos/15p  copies                1                      default
donnees/videos/15p  version               5                      -
donnees/videos/15p  utf8only              off                    -
donnees/videos/15p  normalization         none                   -
donnees/videos/15p  casesensitivity       sensitive              -
donnees/videos/15p  vscan                 off                    default
donnees/videos/15p  nbmand                off                    default
donnees/videos/15p  sharesmb              off                    default
donnees/videos/15p  refquota              none                   default
donnees/videos/15p  refreservation        none                   default
donnees/videos/15p  primarycache          all                    default
donnees/videos/15p  secondarycache        all                    default
donnees/videos/15p  usedbysnapshots       0                      -
donnees/videos/15p  usedbydataset         60.0G                  -
donnees/videos/15p  usedbychildren        0                      -
donnees/videos/15p  usedbyrefreservation  0                      -
donnees/videos/15p  logbias               latency                default
donnees/videos/15p  dedup                 off                    default
donnees/videos/15p  mlslabel              none                   default
donnees/videos/15p  sync                  standard               default
donnees/videos/15p  refcompressratio      1.00x                  -
donnees/videos/15p  written               60.0G                  -
donnees/videos/15p  logicalused           60.0G                  -
donnees/videos/15p  logicalreferenced     60.0G                  -
donnees/videos/15p  snapdev               hidden                 default
donnees/videos/15p  acltype               off                    default
donnees/videos/15p  context               none                   default
donnees/videos/15p  fscontext             none                   default
donnees/videos/15p  defcontext            none                   default
donnees/videos/15p  rootcontext           none                   default
donnees/videos/15p  relatime              off                    default

```

The scenario when the write are slow are:
- using the samba share
- copying from a USB key
- copying from the SSD
which I hope rules out network and samba, especially when copying into /donnees/videos that is not samba share enabled.

for example at present:
```

[FONT=courier new]jerome@serveur:~$ sudo zpool iostat[/FONT]
[FONT=courier new]               capacity     operations    bandwidth[/FONT]
[FONT=courier new]pool        alloc   free   read  write   read  write[/FONT]
[FONT=courier new]----------  -----  -----  -----  -----  -----  -----[/FONT]
[FONT=courier new]donnees      743G  13.8T     47      5  5.74M   271K[/FONT]

```

cpu usage remains very low (<4%)

I am not sure how I can see the actual memory usage, just that the swap is not growing.

- I believe I am using the native zfs, not fuse 
```
 apt-get install ubuntu-zfs
```

- my HDD are cool (one post was from high temp HDDs)

- I have tried some optimisation, but I am not convinced of what I did to draw any conclusion; the net effect was still negligable; I remain open to suggestions on that front.

Any help most appreciated.

---

### Post by totor55 on 2014-09-15
Does not look like any one can help.

My current investigation:
Oracle ZFS documentation indicates that optimum is 3drives not 4
Also better would be 2x2 mirrored drives, so I will try this and see if I get better performance.

---

### Post by totor55 on 2014-09-29
Ok, if this is of interest to anyone

Could not find anything useful: tried adding log file on SSD, tried an L2ARC, but was running out of space on SSD for it.

Ultimately, had some recurrent and more frequent crashes, all pointing to the startech PCI SATA card.
Decided to go for a proper card: LSI, with a SAS fan-out cable to my four drives.

So setup changed to:
M2 card on Mob 256MB for OS
CDROM and 2 SSD on MOB controller
4 x4TB drives on LSI card

I am re-installing Ubuntu.
ZFS config changed to one vdev (I think?) of 2x2 mirrors
will create a ZIL on the M2 card as it is small;
Likely not to oversize the L2ARC as I have read it needs to be in line with memory available (ARC limit set to 8GB).
So more thanl likely will create another zfs storage on the SDD.

I am thinking that I might first make one of the drives a simple mount to test performance using ext4, before creating the zfs storage and testing the perf with zfs, then testing on the SSD zfs.

any comments, suggestion welcome

---

### Post by tgalati4 on 2014-09-29
I was going to suggest the SATA card and testing with simple ext4 performance so that you have a baseline to compare it to.

Why exactly do you need ZFS for a home server?  With many standard RAID configurations available (both in hardware and software) what does ZFS give you?  It seems overkill for most home server use cases.

If you really need disk speed, then consider [RAID0]("http://en.wikipedia.org/wiki/RAID0") (data striped across two drives) and don't worry about data reliability and bit rot.

ZFS is not designed for performance, rather large scaleability, data integrity and protection from bit rot.  Perhaps set up 2 RAID's:  RAID0 for speed and ZFS for weekly *rsync*.

What are your expectations for write speed?

What is the speed of one of your spinners?

```
sudo hdparm -tT /dev/sdc
```

---

### Post by totor55 on 2014-10-02
Answering your questions and then giving an update:

Agreed with your baseline, these are my tests:
large file copied across from an ext4 on hdd to an ext4 on hdd
same file copied across from an ext4 on hdd to a zpool on hdd
same file copied across from an ext4 on hdd to a zpool on sdd

ZFS on home server:
the (only) answer is bit rot [secondary answer is learning...and having (*my definition of*) fun]
note that I have experienced bit rot first hand with family photos, wife was not impressed...

my desktop has a config with Raid0 for OS - programs, and raid1 for data
This project is for a NAS of sorts, used by the whole family

expectations of write speed:
complete above test (file around 3,678Mb ) under a minute

Spinners: (all four drives identical)
[FONT=courier new]/dev/sdc:[/FONT]
[FONT=courier new] Timing cached reads:   30418 MB in  2.00 seconds = 15226.24 MB/sec[/FONT]
[FONT=courier new] Timing buffered disk reads: 396 MB in  3.00 seconds = 131.78 MB/sec[/FONT]

Now for status:
From this blog:
[*[http://louwrentius.com/things-you-should-consider-when-building-a-zfs-nas.html](http://louwrentius.com/things-you-should-consider-when-building-a-zfs-nas.html)*]("http://louwrentius.com/things-you-should-consider-when-building-a-zfs-nas.html")
I discarded creating ZIL or cache.

I created the zpool with hdd mirrored 2 by 2
I created a second pool with the two SSD
I disabled sync writes (same author, different page)


The bad things:
All four hdd go through one controller... minor issue really compared to the rest...
I did not know at the time, but ... my Mobo does not support ECC ram... noooooooooooooo...... oh well, in due time will convert this to a desktop and change mobo... in the meantime makes the exercise a bit pointless.

The good thing
The copying now completes under a minute. Interstingly the SSD is about 1/3 faster...

The funny thing
I now need to overhaul my home network which I think is the current bottleneck: using the ISP router as switch, thinking they were GB, but  they are 100 only...

Conclusions:
Interesting journey, where I wish I had known at the start what I know now... (ECC ram)
ZFS performance is not a/the problem
Simplicity of use (and zfs is so easy to set-up) hides complexity
Internet is (a little bit of) a curse as well as (a lot of ) a blessing: between outdated information, information lacking context (Solaris only...), it is difficult to find information (the curse), but at least the information (and the open source software) is there (the blessing).

Any comment (preferably positive) welcome.

---

### Post by tgalati4 on 2014-10-03
Performance testing often reveals bottlenecks that you have not thought of.  Using a true server (like old Dell PowerEdge servers which are cheap and plentiful) gives you ECC RAM, dual power supplies, and a really, really fast data bus.  You could set up a nice zpool on a real server and then your bottlenecks would be everything else, your router, your cabling, your network topology, etc.

Searching the web for answers is a difficult endeavor because your configuration is unique.  Absolutely no one else has your hardware and software configuration.  So any advice that you find on the web are suggestions.  If you find a command for 12.04, it may or may not work for 14.04.  If you find an *hdparm* tweak that improves disk speed, it might work on someone else's disk drive, and not yours.  If you find the perfect ZFS setup, it might only work for Solaris (where it was developed).  ZFS under linux works, but it is not bulletproof.

I have a 188 MHz (overclocked) Pentium 1 running a few terabyte zpool on freenas.  It has been running for 621 days continuously.  So you can run ZFS on some pretty meager hardware.  Is it slow, yes, sort of, but for serving files to wireless tablets and laptops, it does just fine.  

So ZFS performance depends on a lot of things.  Testing baseline performance of various components is important before making conclusions on file system performance.

---


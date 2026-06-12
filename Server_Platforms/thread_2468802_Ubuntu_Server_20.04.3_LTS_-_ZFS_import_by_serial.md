---
title: "Ubuntu Server 20.04.3 LTS - ZFS import by serial"
date: 2021-11-10
forum: Server Platforms
---

### Post by dlim60194 on 2021-11-10
Hardware: Raspberry Pi 4 Model B Rev 1.4 - 8 GB RAM
OS: Ubuntu Server 20.04.3 LTS
Kernel: Linux fs 5.4.0-1045-raspi #49-Ubuntu SMP PREEMPT Wed Sep 29 17:49:16 UTC 2021 aarch64 aarch64 aarch64 GNU/Linux


I'm setting up ZFS on a fresh install of Ubuntu Server for Raspberry Pi. It's a currently just a test setup. There's no production data at risk, so I can completely wipe and restart with a fresh install as needed.


I'm setting up an 8 x 6 TB raidz2 pool using 6 TB SATA drives in (2) four-bay SATA/USB3 docks.


I have no problem creating the pool using /dev/sda .. /dev/sdh


```
# zpool create pool1 raidz2 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh
# zpool status pool1
  pool: pool1
 state: ONLINE
  scan: resilvered 36K in 0 days 00:00:00 with 0 errors on Wed Nov 10 17:02:44 2021
config:


        NAME        STATE     READ WRITE CKSUM
        pool1       ONLINE       0     0     0
          raidz2-0  ONLINE       0     0     0
            sda     ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sde     ONLINE       0     0     0
            sdf     ONLINE       0     0     0
            sdg     ONLINE       0     0     0
            sdh     ONLINE       0     0     0



```

Once created, I am able to read/write some test data - disk benchmarking with sysbench, for example.


The physical drives don't get consistently assigned to /dev/sd* device files across reboots, so I want to have disks assigned to the pool by serial number, so I have a custom udev rule:


/lib/udev/rules.d/10-local.rules
```
KERNEL=="sd[a-h]", SUBSYSTEM=="block", PROGRAM="get_disk_serial.sh %k", SYMLINK+="disk/by-serial/%c"



```After boot, /dev/disk/by-serial looks like:


```
# ls -l /dev/disk/by-serial/
total 0
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80J0VVG -> ../../sdg
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80JB4KG -> ../../sda
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80JEAHG -> ../../sdh
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80JLDTG -> ../../sdf
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80JLDXG -> ../../sdb
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80JT3WG -> ../../sdd
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80JT4SG -> ../../sdc
lrwxrwxrwx 1 root root 9 Nov 10 17:02 WD-C80JWWGG -> ../../sde



```I should be able to export pool1 and then reimport using the links in /dev/disk/by-serial. I get the following:


```
# zpool export pool1
# zpool import -d /dev/disk/by-serial pool1
cannot import 'pool1': no such pool available



```Any ideas on how to troubleshoot/solve this. At first glance, this looks like it might be a problem with the zpool command handling the -d option, rather than some issue with how the physical disks are linked in /dev/disk/by-serial. I could be wrong.

---

### Post by MAFoElffen on 2021-11-13
But your "by-serial" are just alias'es by creating symlinks for the actual devices right? I'm not sure that works at a lower level of how "zpool import" looks at the devices with the -d flag... I could be wrong, but my guess.

What happens if you try:
```
sudo zpool export pool1
sudo zpool import -d /dev/disk/by-id pool1   # these UUID's are created by default on "zpool create"
sudo zpool import -c /etc/zfs/zpool.cache
sudo zpool status pool1

```

---


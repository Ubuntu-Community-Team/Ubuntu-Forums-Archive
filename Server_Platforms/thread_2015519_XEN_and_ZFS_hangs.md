---
title: "XEN and ZFS hangs"
date: 2012-07-03
forum: Server Platforms
---

### Post by kissgyula on 2012-07-03
I try to build a XEN host with native ZFS storage. Native ZFS installs successfully, and created raidz pool fine. After that installed the XCP-XAPI followed the instructions at [wiki.xen.org]("http://wiki.xen.org/wiki/XCP_toolstack_on_a_Debian-based_distribution").

The XEN installing fine, but after reboot any operations on the ZFS mount hangs/freezing. There are no syslog entries, errors. The only thing is 4 process (txg_sync, z_null_iss/0, zfs and txg_quiesce), eatin all CPU power.

I find some articles, that suggest to install the latest daily ZFS build, but it seems the stable and the daily ppa are the same.

With the standard (non-XEN) kernel ZFS is working fine.

It is happend with anyone else? How can I find mor information about this problem?

# uname -a
Kernel: Linux server 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

# dkms status
blktap, 2.0.91, 3.2.0-26-generic, x86_64: installed
openvswitch, 1.4.0, 3.2.0-25-generic, x86_64: installed
openvswitch, 1.4.0, 3.2.0-26-generic, x86_64: installed
spl, 0.6.0.65, 3.2.0-26-generic, x86_64: installed
zfs, 0.6.0.65, 3.2.0-25-generic, x86_64: installed
zfs, 0.6.0.65, 3.2.0-26-generic, x86_64: installed

# zpool status
[sudo] password for kiss:
  pool: data
 state: ONLINE
 scan: none requested
config:

        NAME                                         STATE     READ WRITE CKSUM
        data                                         ONLINE       0     0     0
          raidz1-0                                   ONLINE       0     0     0
            scsi-SATA_SAMSUNG_HD204UIS2H7J90B614909  ONLINE       0     0     0
            scsi-SATA_SAMSUNG_HD204UIS2H7J90B614910  ONLINE       0     0     0
            scsi-SATA_SAMSUNG_HD204UIS2H7J90B614957  ONLINE       0     0     0

errors: No known data errors

---

### Post by dblade on 2012-10-11
I'm having the same issue (same 3 processes and IO hang) on Debian Wheezy, 3.2 kernel under Xen 4.2.

Did you ever figure anything out?

I performed an additional test with zfs_arc_max set to 512MB and it remained slow under Xen.  On bare metal and with same zfs_arc_max setting the performance is fast.

---


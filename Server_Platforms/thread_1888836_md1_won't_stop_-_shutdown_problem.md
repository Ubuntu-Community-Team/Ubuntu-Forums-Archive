---
title: "md1 won't stop - shutdown problem"
date: 2011-11-30
forum: Server Platforms
---

### Post by ClientAlive on 2011-11-30
I'm not really sure where to begin. I'm posting here because the machine is inteded to become a server. It's a fresh Gentoo install. I've got posts up all over the internet but not getting any responses so I thought I'd take a chance here. I'd appreciate it if anyone can help.

When I do a

```

shutdown now

```

it begins to shut down but then gives me a message to do [something...] to enter repair mode or press ctrl+D to continue. Pressing ctrl+D takes me back to the log in screen. I can, after logging in again, force a shutdown with the -h flag but I need to get this worked out.

my /var/log/rc.log shows the offending entry

```

 Shutting down RAID devices (mdadm) ... 
 mdadm: stopped /dev/md3 
 mdadm: stopped /dev/md2 
 mdadm: stopped /dev/md0 
 [B]mdadm: failed to stop array /dev/md1: Device or resource busy 
 Perhaps a running process, mounted filesystem or active volume group? 
  [ !! ] 
  * ERROR: mdraid failed to stop [/B]
  * Stopping udevd ... 
  [ ok ]

```

There is also another entry the comes before that one in sequence that stand out to me also but not sure if there is a connection.

```

* Unmounting filesystems 
  *   Unmounting /var/tmp ... 
  [ ok ] 
  *   Unmounting /var ... 
  [ ok ] 
  *   Unmounting /tmp ... 
  [ ok ] 
  *   Unmounting /opt ... 
  [ ok ] 
  *   Unmounting /home ... 
  [ ok ] 
  *   Unmounting /usr ... 
  [ ok ]

```

compared to the output of lvscan (and I know just by looking at it) there are only 6 of my total 8 logical volumes being listed as taken down. The two that are missing from the above list are portage and distfiles.

For what it's worth I'll paste some various system info below. If any other info is needed I'd be happy to provide. Please, can someone help me sort this out?

Oh, sorry, I should have mentioned - md0 is /boot; md1 is /; md2 is swap on raid 1; and md3 is where my logical volumes reside.

X ---------------------------------------------------------------------- X


```

/*System Information*/


=> File: /var/log/rc.log:

rc shutdown logging started at Thu Nov 24 06:24:13 2011

 * Stopping local
 [ ok ]
 * Stopping vixie-cron ...
 [ ok ]
 * Saving random seed ...
 [ ok ]
 * Deactivating swap devices ...
 [ ok ]
 * Stopping sshd ...
 [ ok ]
 * Unmounting network filesystems ...
 [ ok ]
 * Stopping syslog-ng ...
 [ ok ]
 * Bringing down interface eth0
 *   Stopping dhcpcd on eth0 ...
 [ ok ]
 *   Removing addresses
* Bringing down interface lo
 *   Removing addresses
 * Unmounting loop devices
 * Unmounting filesystems
 *   Unmounting /var/tmp ...
 [ ok ]
 *   Unmounting /var ...
 [ ok ]
 *   Unmounting /tmp ...
 [ ok ]
 *   Unmounting /opt ...
 [ ok ]
 *   Unmounting /home ...
 [ ok ]
 *   Unmounting /usr ...
 [ ok ]
 * Shutting down the Logical Volume Manager
 *   Shutting Down logical volumes  ...
 [ ok ]
 *   Shutting Down volume groups  ...
  0 logical volume(s) in volume group "sysgrp" now active
[ ok ]
 * Finished Shutting down the Logical Volume Manager
 * Shutting down RAID devices (mdadm) ...
mdadm: stopped /dev/md3
mdadm: stopped /dev/md2
mdadm: stopped /dev/md0
mdadm: failed to stop array /dev/md1: Device or resource busy
Perhaps a running process, mounted filesystem or active volume group?
 [ !! ]
 * ERROR: mdraid failed to stop
 * Stopping udevd ...
 [ ok ]

rc shutdown logging stopped at Thu Nov 24 06:24:17 2011


rc boot logging started at Mon Nov 28 00:47:43 2011

 * Setting system clock using the hardware clock [Local Time] ...
 [ ok ]
 * Autoloaded 0 module(s)
 * Starting up RAID devices ...

 [ !! ]
 * Setting up the Logical Volume Manager ...
 [ ok ]
 * Checking local filesystems  ...
/dev/md1: clean, 1690/262144 files, 77015/1048560 blocks
/dev/md0: clean, 33/25584 files, 10229/102336 blocks
/dev/mapper/sysgrp-usr: clean, 225130/524288 files, 576351/2097152 blocks
/dev/mapper/sysgrp-portage: clean, 149008/200704 files, 353962/2097152 blocks
/dev/mapper/sysgrp-distfiles: clean, 41/4096 files, 25578/1048576 blocks
/dev/mapper/sysgrp-home: clean, 18/6742016 files, 471210/26959872 blocks
/dev/mapper/sysgrp-opt: clean, 12/262144 files, 51311/1048576 blocks
/dev/mapper/sysgrp-tmp: clean, 13/393216 files, 27760/1572864 blocks
/dev/mapper/sysgrp-var: clean, 4175/393216 files, 68563/1572864 blocks
/dev/mapper/sysgrp-vtmp: clean, 14/262144 files, 18512/1048576 blocks
 [ ok ]
 * Remounting root filesystem read/write ...
 [ ok ]
 * Updating /etc/mtab ...
 [ ok ]
 * Mounting local filesystems ...
 [ ok ]
 * Configuring kernel parameters ...
 [ ok ]
 * Creating user login records ...
 [ ok ]
 * Cleaning /var/run ...
 [ ok ]
 * Wiping /tmp directory ...
 [ ok ]
 * Setting hostname to shine ...
 [ ok ]
 * Setting terminal encoding [UTF-8] ...
 [ ok ]
 * Setting keyboard mode [UTF-8] ...
[ ok ]
 * Loading key mappings [us] ...
 [ ok ]
 * Bringing up interface lo
 *   127.0.0.1/8 ...
 [ ok ]
 *   Adding routes
 *     127.0.0.0/8 via 127.0.0.1 ...
 [ ok ]
 * Mounting USB device filesystem [usbfs] ...
 [ ok ]
 * Mounting misc binary format filesystem ...
 [ ok ]
 * Activating swap devices ...
 [ ok ]
 * Initializing random number generator ...
 [ ok ]

rc boot logging stopped at Mon Nov 28 00:47:51 2011


rc default logging started at Mon Nov 28 00:47:51 2011

 * Bringing up interface eth0
 *   dhcp ...
 *     Running dhcpcd ...
dhcpcd[1936]: version 5.2.12 starting
dhcpcd[1936]: eth0: rebinding lease of 192.168.0.11
dhcpcd[1936]: eth0: acknowledged 192.168.0.11 from 192.168.0.1
dhcpcd[1936]: eth0: checking for 192.168.0.11
dhcpcd[1936]: eth0: leased 192.168.0.11 for 604800 seconds
dhcpcd[1936]: forked to background, child pid 1968
 [ ok ]
 *     received address 192.168.0.11/24
 [ ok ]
 * Mounting network filesystems ...
 [ ok ]
 * Starting syslog-ng ...
 [ ok ]
 * Starting sshd ...
 [ ok ]
 * Doing udev cleanups
 * Starting vixie-cron ...
 [ ok ]
 * Starting local
 [ ok ]

rc default logging stopped at Mon Nov 28 00:47:57 2011


=> Output of cat /proc/mdstat:

Personalities : [raid1] [raid6] [raid5] [raid4] 
md3 : active raid5 sdc3[2] sdb3[1] sda3[0]
      143510528 blocks level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid1 sdc5[2] sdb5[1] sda5[0]
      4194240 blocks [3/3] [UUU]
      
md2 : active raid1 sdc6[2] sdb6[1] sda6[0]
      2095040 blocks [3/3] [UUU]
      
md0 : active raid1 sdc1[2] sdb1[1] sda1[0]
      102336 blocks [3/3] [UUU]
      
unused devices: <none>


=> Output of pvscan:

 PV /dev/md3   VG sysgrp   lvm2 [136.86 GiB / 16.00 MiB free]
  Total: 1 [136.86 GiB] / in use: 1 [136.86 GiB] / in no VG: 0 [0   ]


=> Output pf vgscan:

 Reading all physical volumes.  This may take a while...
  Found volume group "sysgrp" using metadata type lvm2


=> Output of lvscan:

 ACTIVE            '/dev/sysgrp/usr' [8.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/portage' [2.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/distfiles' [4.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/opt' [4.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/var' [6.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/vtmp' [4.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/tmp' [6.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/home' [102.84 GiB] inherit


=> File: /etc/fstab:

# <fs>    <mountpoint>   <type>   <opts>       <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/md0               /boot          ext2     noauto,noatime   1 2
/dev/md1               /              ext3     noatime          0 1
/dev/md2               swap           swap     sw,pri=1         0 0
/dev/cdrom             /mnt/cdrom     auto     noauto,ro        0 0
/dev/sysgrp/usr        /usr           ext3     noatime          1 2
/dev/sysgrp/portage    /usr/portage   ext2     noatime          1 2
/dev/sysgrp/distfiles  /usr/portage/distfiles  ext2  noatime    1 2
/dev/sysgrp/home       /home          ext3     noatime          1 2
/dev/sysgrp/opt        /opt           ext3     noatime          1 2
/dev/sysgrp/tmp        /tmp           ext2     noatime          1 2
/dev/sysgrp/var        /var           ext3     noatime          1 2
/dev/sysgrp/vtmp       /var/tmp       ext2     noatime          1 2


/sbin/mdadm --query --examine /dev/md1
mdadm: No md superblock detected on /dev/md1.


/sbin/mdadm --query --detail /dev/md1
/dev/md1:
        Version : 0.90
  Creation Time : Mon Nov  7 23:38:41 2011
     Raid Level : raid1
     Array Size : 4194240 (4.00 GiB 4.29 GB)
  Used Dev Size : 4194240 (4.00 GiB 4.29 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Nov 28 18:44:27 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : e846c432:ea00aa1b:cb201669:f728008a
         Events : 0.18

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5






ls -al /dev | grep md
drwxr-xr-x  2 root root        60 Nov 28 18:43 .mdadm
drwxr-xr-x  2 root root        80 Nov 28 18:43 md
brw-rw----  1 root disk    9,   0 Nov 28 18:43 md0
brw-rw----  1 root disk    9,   1 Nov 28 18:43 md1
brw-rw----  1 root disk    9,   2 Nov 28 18:43 md2
brw-rw----  1 root disk    9,   3 Nov 28 18:43 md3
lrwxrwxrwx  1 root root         3 Nov 28 18:43 root -> md1

```

---

### Post by ClientAlive on 2011-12-05
bump

:)

Anybody?

---


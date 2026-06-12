---
title: "Multipath issues after upgrade from 11.04 to 11.10"
date: 2011-11-11
forum: Server Platforms
---

### Post by rogerappl on 2011-11-11
I have a HP Blade Server with an HP MSA2000fc attached.

In 11.04 - I had clean boots without errors when I upgraded 
I have the following errors on boot:

fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
/dev/sda1 was not cleanly unmounted, check forced.
/dev/mapper/ubuntudb-root: clean, 79228/7897088 files, 4212838/31574016 blocks
udevd[412]: inotify_add_watch(6, /dev/dm-2, 10) failed: No such file or directory


fsck from util-linux 2.19.1
/dev/mapper/3600c0ff000109abe3d25e64d01000000-part1: recovering journal
/dev/sda1: 233/124496 files (6.9% non-contiguous), 63535/248832 blocks
mountall: fsck /boot [395] terminated with status 1
rpcbind: Cannot open '/run/rpcbind/rpcbind.xdr' file for reading, errno 2 (No such file or directory)

rpcbind: Cannot open '/run/rpcbind/portmap.xdr' file for reading, errno 2 (No such file or directory)

/dev/mapper/3600c0ff000109abe3d25e64d01000000-part1: Clearing orphaned inode 35540609 (uid=1001, gid=1001, mode=0100640, size=0)
/dev/mapper/3600c0ff000109abe3d25e64d01000000-part1: Clearing orphaned inode 35539087 (uid=1001, gid=1001, mode=0100640, size=0)
/dev/mapper/3600c0ff000109abe3d25e64d01000000-part1: clean, 51470/78127104 files, 9985243/312498380 blocks
Error: : Inappropriate ioctl for device
cciss TUR  failed in CCISS_GETLUNINFO: Inappropriate ioctl for device
Error: : Inappropriate ioctl for device
cciss TUR  failed in CCISS_GETLUNINFO: Inappropriate ioctl for device
 * Discovering and coalescing multipaths...       [128G 
[122G[ OK ]
 * Starting AppArmor profiles       [128G 
[122G[ OK ]
/etc/rc2.d/S20multipath: 4: defaults: not found
/etc/rc2.d/S20multipath: 5: udev_dir: not found
/etc/rc2.d/S20multipath: 6: polling_interval: not found
/etc/rc2.d/S20multipath: 7: user_friendly_names: not found
/etc/rc2.d/S20multipath: 8: getuid_callout: not found
/etc/rc2.d/S20multipath: 9: Syntax error: "}" unexpected
 * Stopping Failsafe Boot Delay[122G[ OK ]
 * Stopping System V initialisation compatibility[122G[ OK ]
 * Starting System V runlevel compatibility[122G[ OK ]
 * Stopping automatic crash report generation[122G[[31mfail[39;49m]
 * Starting save kernel messages[122G[ OK ]
 * Starting CPU interrupts balancing daemon[122G[ OK ]
 * Starting regular background program processing daemon[122G[ OK ]
 * Starting deferred execution scheduler[122G[ OK ]
Error: : Inappropriate ioctl for device
cciss TUR  failed in CCISS_GETLUNINFO: Invalid argument
 * Starting multipath daemon multipathd       [128G 
[122G[ OK ]
Starting the database...
Error: : Inappropriate ioctl for device
cciss TUR  failed in CCISS_GETLUNINFO: Inappropriate ioctl for device
/etc/profile: line 35: ulimit: open files: cannot modify limit: Operation not permitted
/home/oracle/.bash_profile: line 18: ulimit: pipe size: cannot modify limit: Invalid argument
 * Stopping save kernel messages[122G[ OK ]
Processing Database instance "zitastmp": log file /media/msa1/u01/app/oracle/product/11.2.0/dbhome/startup.log
Processing Database instance "zitas": log file /media/msa1/u01/app/oracle/product/11.2.0/dbhome/startup.log
touch: cannot touch `/var/lock/subsys/dbora': No such file or directory
 * Starting MD monitoring service mdadm --monitor       [128G 
[122G[ OK ]
 * Stopping System V runlevel compatibility[122G[ OK ]

I get connected to the MSA fine and everything works OK - so this is not critical.

I have verified this:
rpcbind: Cannot open '/run/rpcbind/rpcbind.xdr' file for reading, errno 2 (No such file or directory)
  and it is true.

Oracle is up and running fine as well despite this:
Error: : Inappropriate ioctl for device
cciss TUR  failed in CCISS_GETLUNINFO: Inappropriate ioctl for device
/etc/profile: line 35: ulimit: open files: cannot modify limit: Operation not permitted
/home/oracle/.bash_profile: line 18: ulimit: pipe size: cannot modify limit: Invalid argument

I suspect that there are changes that have made the .bash_profile redundant and I have seen them in the sysctl.conf file.

However the 
Error: : Inappropriate ioctl for device
 cciss TUR  failed in CCISS_GETLUNINFO: Inappropriate ioctl for device
 seems directly related to the multipath config as they are the defaults.

Any ideas - I have inherited these systems and would like to get them cleaned up and 100% (they are production systems).  Not much info out there on multipath on Ubuntu.
As you can see the recover on the MSA works fine as well (sorry - the system crashed due to power - so a little extra in the log - but it makes a point - the MSA is working fine).  I have mdadm installed - but do not see any purpose in it - can I safely remove it without interfering with the multipath?  There are no arrays on the system.

So far everything is fine and I am pleased with the results of the upgrade.

---

### Post by dapperdanny77 on 2011-11-11
oh - bad things happen there

I would try to start the system with a rescue cd - Ubuntu CD Images should provide a rescue mode.  (use a 11.10 boot cd to have the same kernel using the same drivers)
Then see if your RAID system is recognized correctly maybe the 11.10 kernel has problems with your hardware.

It's also possible, that the device naming has changed with the new kernel and entries in /etc/fstab don't match 

just a first guess ...

---

### Post by afrodeity on 2012-01-23
[http://unix.stackexchange.com/questions/13437/rpcbind-warning-on-boot](http://unix.stackexchange.com/questions/13437/rpcbind-warning-on-boot)

---


---
title: "ZFS on Linux autoexpand with VMware disks"
date: 2013-08-12
forum: Server Platforms
---

### Post by Patrick_Senignen on 2013-08-12
Okay... I'm going to try and explain this the best I can.

I am running a 64-bit, 12.04.2 virtual guest in VMware.  I have installed ZFS on Linux from the PPA repo.  

I add a second, 100 GB, hard disk in vSphere, reboot the VM, and can successfully create a zpool with the autoexpand option enabled.
 ```
zpool create -f -o autoexpand=on tank /dev/sdb
```

This creates both an sdb1 and sdb9 partition

What I cannot figure out is how to expand that disk to 200 GB and have the ZFS pool auto expand.

Is this simply a matter of using 'parted' or 'gdisk' to expand the sdb1 partition and running ```
zpool online -e tank /dev/sdb
```

I know that I can add another hard disk ```
zpool add tank /dev/sdc
``` to expand the pool, but I'd rather be able to just grow the one VM disk.

Please let me know if I'm being daft or leaving out any info you need... And Thanks in Advance!

---

### Post by hawkmage on 2013-08-12
I have used auto-expand on a RAIDZ volume where there are multiple drives but not on a single drive that gets resized.  With the multiple drives once all of the drives in the RAIDZ volume are replaced with larger ones the expansion happens.  

I assume that you used the ppa:zfs-native/stable repository to install ZFS.

---


---
title: "Change ZFS pool to use ID instead of disk assignment"
date: 2012-11-24
forum: Server Platforms
---

### Post by LedFoot74 on 2012-11-24
Hi,

I've built my zpool to use disk assignment (/dev/sda etc) 

I've also since read and experienced that this is a bad move and that I should have used /dev/disk/by-id instead.

Does anyone know how to convert an existing zpool to use /dev/disk/by-id?

Also can you tell mehow to figure out a disk ID? I cant find details anywhere!

Here is my current pool:

```
       NAME        STATE     READ WRITE CKSUM
        zfs2        ONLINE       0     0     0
          raidz2-0  ONLINE       0     0     0
            sda     ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sde     ONLINE       0     0     0
            sdf     ONLINE       0     0     0
            sdg     ONLINE       0     0     2
            sdh     ONLINE       0     0     2

errors: No known data errors

```

---

### Post by dajhorn on 2012-11-24
Do this to convert the pool:

# zpool export zfs2
# zpool import -d /dev/disk/by-id zfs2

The change is stored in the binary /etc/zfs/zpool.cache configuration file.

---

### Post by LedFoot74 on 2012-11-24
Ok,

So I managed to export zfs2 successfully (after I worked out that I couldn't do it while in the zfs2 directory!)

When I try to import I get the following message:

root@server:/# zpool import -d /dev/disk/by-id zfs2
cannot import 'zfs2': more than one matching pool
import by numeric ID instead

Is there something else I need to clean up before importing?

---

### Post by LedFoot74 on 2012-11-24
I just worked it out!

I used the numeric ID on the import instead and this worked, zpool status showed that the disks were listed by their ID instead! Woot! I did this by running the zpool import command to se the avaialable pools and chose the non faulted and higher numeric ID.

# zpool import -d /dev/disk/by-id 5784957380277850

when I use the zpool import command, there is a leftover zfs2 from a previous faulted state. How do I get rid of this?

the pool:

```
root@server:/# zpool import
   pool: zfs2
     id: 94738228726143326
  state: UNAVAIL
 status: One or more devices contains corrupted data.
 action: The pool cannot be imported due to damaged devices or data.
   see: http://zfsonlinux.org/msg/ZFS-8000-5E
 config:

        zfs2        UNAVAIL  insufficient replicas
          raidz2-0  UNAVAIL  insufficient replicas
            sda     UNAVAIL
            sdb     UNAVAIL
            sdc     UNAVAIL
            sdd     UNAVAIL
            sde     UNAVAIL
            sdf     UNAVAIL
            sdg     UNAVAIL
            sdh     UNAVAIL
```

---

### Post by dajhorn on 2012-11-24
It sounds like you created a new zpool over top of an old zpool.

First, just try to export the ghost pool by number.

Second, if that doesn't stick, then clear partition 9 at the end of each pool member.  Double-check that this partition is much smaller than partition 1, which contains the actual pool data.  Have a backup too.

Run something like `dd if=/dev/zero of=/dev/sda9` or use an alternative like `gparted`, but be very careful that you don't typo and damage important data.

---

### Post by LedFoot74 on 2012-11-26
Tried to export by the ghost numeric ID but did not have any luck. It's not doing any harm so probably just going to leave as it is. When I do an upgrade down the track I'll reuildit completely and make it go away then.

Dajhorn: thanks for your help in getting me out of a sticky situation back there. Much appreciated!!

---


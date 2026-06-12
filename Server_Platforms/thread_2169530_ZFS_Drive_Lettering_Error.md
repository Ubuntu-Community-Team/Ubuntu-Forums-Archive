---
title: "ZFS Drive Lettering Error"
date: 2013-08-22
forum: Server Platforms
---

### Post by michael28 on 2013-08-22
I created my ZFS pool using:

$ sudo zpool create test raidz sda sdb sdc sdd sde sdf

There are 6x2tb drives on that pool for storage capacity for me of 10tb.

Later, I added a Raid card with two new drives for my Ubuntu installation.
Those drives took on sda and sdb.

Now, when I run zpool status, I get:
> root@michaelnas:/# zpool status
  pool: nfs
 state: UNAVAIL
status: One or more devices could not be used because the label is missing 
    or invalid.  There are insufficient replicas for the pool to continue
     functioning.
action: Destroy and re-create the pool from
    a backup source.
   see: [http://www.sun.com/msg/ZFS-8000-5E](http://www.sun.com/msg/ZFS-8000-5E)
  scrub: none requested
config:


    NAME        STATE     READ WRITE CKSUM
    nfs         UNAVAIL      0     0     0  insufficient replicas
       raidz1-0  UNAVAIL      0     0     0  insufficient replicas
        sda     UNAVAIL      0     0     0  corrupted data
         sdb     UNAVAIL      0     0     0  corrupted data
        sdc     ONLINE       0     0     0
        sdd     ONLINE       0     0     0
         sde     ONLINE       0     0     0
        sdf     ONLINE       0     0     0



Or, when I run blkid, I get:
> root@michaelnas:/# sudo blkid
/dev/sda1: UUID="24c826da-2c84-4b26-a058-d8bcb5d82024" TYPE="ext4" 
/dev/sda5: UUID="37fac19f-1db1-4ba0-a660-d6177a54714e" TYPE="swap" 
 /dev/sdb1: UUID="24c826da-2c84-4b26-a058-d8bcb5d82024" TYPE="ext4" 
/dev/sdb5: UUID="37fac19f-1db1-4ba0-a660-d6177a54714e" TYPE="swap" 
/dev/sdc: LABEL="nfs" UUID="14008380709944265909" UUID_SUB="9564455886327542960" TYPE="zfs_member" 
 /dev/sdd: LABEL="nfs" UUID="14008380709944265909" UUID_SUB="12299717333085135659" TYPE="zfs_member" 
/dev/sde: LABEL="nfs" UUID="14008380709944265909" UUID_SUB="10507233321646142380" TYPE="zfs_member" 
 /dev/sdf: LABEL="nfs" UUID="14008380709944265909" UUID_SUB="10054919623811085658" TYPE="zfs_member" 
/dev/sdg: LABEL="nfs" UUID="14008380709944265909" UUID_SUB="15711096024533942398" TYPE="zfs_member" 
 /dev/sdh: LABEL="nfs" UUID="14008380709944265909" UUID_SUB="5558340207139158787" TYPE="zfs_member" 



So, is there anyway that I can change the zfs mount to go from sda sdb, etc to by-device-id without trashing the data?

Thank you!

---

### Post by michael28 on 2013-08-22
Figured it out!

All I had to do was type: 
# zpool export tank
# zpool import tank

Then it exported the zpool's cache and imported the zfs with their device-id's!!!

---


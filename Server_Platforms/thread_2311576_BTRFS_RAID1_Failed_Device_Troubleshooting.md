---
title: "BTRFS RAID1 Failed Device Troubleshooting"
date: 2016-01-28
forum: Server Platforms
---

### Post by laz0rrrgore on 2016-01-28
Hello,

For a new project I'm looking into building a server where data storage is handled (for the most part) by BTRFS in a RAID1 Array. The setup should look something like this when finalized:

```

1 SSD (sda)
2 2TB HDD (sdb & sdc, BTRFS Raid 1, A)
2 4TB HDD (sdd & sde, BTRFS Raid 1, B)

/dev/sda to be mounted at /

A to be mounted at /home

B to be mounted at /home/jail (which is for jailed users with ssh/sftp access) with grpquota active

```


Well so Ubuntu Server doesn't really mount the whole BTRFS Volume, instead there is just a mountpoint for /dev/sdb ... /dev/sdc (or the Volume as such) is handled by BTRFS.

So how would I handle a situation in which /dev/sdb fails?
BTRFS won't let you remove it from the Volume because a RAID1 Volume demands for at least 2 Drives.
A failed /dev/sdb would thus not be mounted by the System anymore even if the data is still on /dev/sdc.

_Question 1_: Is there a possibilty to mount a BTRFS Volume not as /dev/sdb, but with an identifier for the whole Volume so the mountpoints would still work in case of a drive-failure? (Would I have to use Subvolumes for this?)

_Question 2_: If the drive fails would it be correct to proceed by converting the RAID1 Volume to a standard BTRFS Volume, then removing the failed drive and after exchanging it for a new one to reconvert the Volume to RAID1?
```

btrfs balance start -dconvert=raid0 -mconvert=raid0 /home
btrfs device remove /dev/sdb /home                           #This would of course only work if /home is still mounted, which is not sure as the system mounted /dev/sdb to /home

#Then after exchanging the defective device
btrfs device add /dev/sdf /home
btrfs balance start -dconvert=raid1 -mconvert=raid1 /home


```


Just want to make sure to figure out such troubleshooting cases before i actually set up the server, to be able to keep the system running and react quickly and properly in such a case.

---

### Post by laz0rrrgore on 2016-01-28
I just found an answer to my Question 1:

so it's not a problem to just label the volume while creating it and then using this Label for mounting in /etc/fstab. Alternatively you can use the UUID (which will be the same for all devices associated with the Volume):

```

sudo su

#create BTRFS RAID1 Volume with the Label "labelname"
mkfs.btrfs -m raid1 -d raid1 -L labelname  /dev/sdb /dev/sdc

#to get UUID, just run blkid. This should now output the same UUID for /dev/sdb & /dev/sdc
blkid

#then, in /etc/fstab, just use the Labelname to create a mountpoint for the Volume
nano /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
LABEL=labelname    /home    btrfs   noatime,usrquota,grpquota     0 0

# for this to work, I think it's important that initrd runs btrfs device scan

```


This answers my 1st Question. (Thanks to this guide: [https://www.linux.com/learn/tutorials/767332-howto-manage-btrfs-storage-pools-subvolumes-and-snapshots-on-linux-part-1](https://www.linux.com/learn/tutorials/767332-howto-manage-btrfs-storage-pools-subvolumes-and-snapshots-on-linux-part-1) )
For the 2nd Question (how to handle a failed device), i'm still in the dark.

---


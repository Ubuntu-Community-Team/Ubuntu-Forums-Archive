---
title: "nfs export problem configuration not correct"
date: 2011-01-04
forum: Server Platforms
---

### Post by jamesbon on 2011-01-04
I am trying to export a partition on USB disk  attached to my computer as nfs volume.
at client machine I tried
>  mount -t nfs4 -o proto=tcp,port=2049 servername:/media/vol2 /mnt/nfs/
mount.nfs4: access denied by server while mounting servername:/media/vol2
after this I checked permissions of USB hard disk on the nfs server
(this USB is partitioned into 2)
one is a FAT partition and another is NTFS ( I am trying to mount the
NTFS partition rw on nfs)
> 
ls -l /media/
total 26
drwxrwxrwx 2 bond bond  2048 2010-02-12 04:12 USBDISK
drwx------ 7 bond bond  4096 1970-01-01 05:30 vol1
drwx------ 1 bond bond 20480 2011-01-03 17:43 vol2
Is this the problem?

---

### Post by samosamo on 2011-01-05
The problem is not filesystem permissions.  Don't worry about chmod yet.

Try using IP instead of client's name in /etc/exports
Try simplifying your mount command to "mount -t nfs 192.168.1.xxx:/exports/share /mnt/share"

---

### Post by jamesbon on 2011-01-05
Here is the /etc/exports file entry on nfs server

>     /media/vol2        192.168.1.0/24(rw,sync,no_subtree_check)

On the client machine I tried to mount the above nfs volume 

>     mount -t nfs 192.168.1.19:/media/vol2 /mnt/nfs

Things worked well upto here.

But I was not able to go inside the mounted volume at the client machine.

Hence I checked the permissions on the folder on nfs server they were as follows

>     drwx------ 1 bond bond 20480 2011-01-03 17:43 vol2

and the share mounted on client machine which was above only had following permissions

>     drwx------ 1 client_hostname client_hostname 20480 2011-01-03 17:43 vol2

Considering this to be source of problem I tried to change the permissions at the server

>     chmod -R 755 /media/vol2 

but this attempt failed.
Does any one has any clue as what might be the issue?
It appears to be some file system problem.




I checked by mount command the type of file system on USB disk

>     /dev/sdb2 on /media/vol1 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
    /dev/sdb5 on /media/vol2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
    /dev/sr1 on /media/HPLAUNCHER type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)

and the > /var/log/syslog shows


>     Jan  6 10:24:12 bond ntfs-3g[2278]: Mounted /dev/sdb5 (Read-Write, label "vol2", NTFS 3.1)
    Jan  6 10:24:12 bond ntfs-3g[2278]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
    Jan  6 10:24:12 bond ntfs-3g[2278]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdb5,blkdev,blksize=4096,default_permissions
    Jan  6 10:24:12 bond ntfs-3g[2278]: Global ownership and permissions enforced, configuration type 1

Where I see ntfs-3g driver in use for the above volume which I want to export on nfs.Can this be the source of my problems? Or I need to check some thing else?

I notice the output of mount command

> /dev/sdb5 on /media/vol2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,**default_permissions**)

Is there a way I can enforce to load changed permissions on the said USB and change this default behavior.
What could be the problem?

---

### Post by samosamo on 2011-01-06
I should have asked you this first just to rule out that the NFS config is correct: Are you able to share an export on an ext3/ext4 filesystem without any problems?

I don't have any experience sharing USB mounted devices, maybe someone else can help

---

### Post by nanog on 2011-08-26
windows file systems are not posix compliant. see my post here:

[http://ubuntuforums.org/showpost.php?p=11190024&postcount=5](http://ubuntuforums.org/showpost.php?p=11190024&postcount=5)

---


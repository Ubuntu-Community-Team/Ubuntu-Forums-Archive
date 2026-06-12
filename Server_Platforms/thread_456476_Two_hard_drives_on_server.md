---
title: "Two hard drives on server"
date: 2007-05-27
forum: Server Platforms
---

### Post by FastZ on 2007-05-27
Hey guys.  I have two hard drives on my server and they are both formatted as Ext3.  How can I use both hard drives to share files via my FTP site?  The second drive was previously NTFS and I just reformatted it as Ext3 and the icon on the desktop went away afterwards.  Now I can't find it.  It's an extra 150Gb that I'd like to use for storage and sharing of files across my LAN and to my laptop when I'm away from home.  Anybody got any ideas?

---

### Post by dfreer on 2007-05-27
post output of:
df -h
sudo fdisk -l
ls -l /media/
ls -l /mnt/

and your files:
/etc/fstab
/etc/mtab

---

### Post by nix4me on 2007-05-27
do a df -h.  That should show you the drive.  Then just mount it in the /etc/fstab dir.

Or, you could install gparted and use it to mount the drive.

nix4me

---

### Post by FastZ on 2007-06-04
df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             228G  149G   68G  69% /
varrun                316M  272K  315M   1% /var/run
varlock               316M     0  316M   0% /var/lock
procbususb            316M  100K  316M   1% /proc/bus/usb
udev                  316M  100K  316M   1% /dev
devshm                316M     0  316M   0% /dev/shm

```

sudo fdisk -l
```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30166   242308363+  83  Linux
/dev/hda2           30167       30401     1887637+   5  Extended
/dev/hda5           30167       30401     1887606   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321   83  Linux

```

ls -l /media/
```
total 12
lrwxrwxrwx 1 root root    6 2006-11-13 18:40 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-11-13 18:40 cdrom0
lrwxrwxrwx 1 root root    7 2006-11-13 18:40 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2006-11-13 18:40 floppy0
drwxr-xr-x 2 root root 4096 2006-11-14 16:30 NTFSDrive

```
The drive used to be called NTFSDrive.  Then I reformatted it to Ext3.

ls -l /mnt/
```
total 0

```

FSTAB
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5368b52c-f8d1-4a4d-a147-013699f64d11 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=79472065-b864-4da9-a47d-15256773ad2a none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/NTFSDrive   ntfs-3g   defaults,locale=en_US.utf8  0      0

```

MTAB
```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```

Sorry I was late getting this posted.  I've been busy with school and work.

---

### Post by bukwirm on 2007-06-04
In your fstab, you need to correct the line with your second drive - the type needs to be ext3, and the options should probably just be the defaults. This will cause the drive to be mounted at /media/NTFSDrive, as before. If you want to mount it somewhere else, you'll need to change the mount point.

---


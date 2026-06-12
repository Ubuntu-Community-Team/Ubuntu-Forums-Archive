---
title: "Mount External Hard-Disk in read only mode"
date: 2009-05-28
forum: System76 Support
---

### Post by DieUbunt on 2009-05-28
Hi,

I have Ubuntu Jaunty and I need to mount external hard-disk in reading mode only.
Could you suggest me a pratical method to do that automatically.
Is It possible to setup any option that it does that?
Thanks in advance;)

---

### Post by Boondoklife on 2009-05-28
if you want to do it in the fstab just give it the ro option

---

### Post by DieUbunt on 2009-05-28
> **maletek said:**
> if you want to do it in the fstab just give it the ro option
In fstab I don't find any information about new hard-disk.
I have found only in mtab

Thanks

This is information that I have found in /etc/mtab  :

/dev/sdb1 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

---

### Post by sahabcse on 2009-05-28
Try below command 

sudo mount -t ntfs-3g -o umask=222 /dev/sdb1 /media/mountpoint

for more info follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by Boondoklife on 2009-05-28
you will have to put the entry into fstab, it is simple```
/dev/sdb1 /media/disk ext3 ro 0 0
```

replace the ext3 with the filesytem used on the disk

---

### Post by DieUbunt on 2009-05-28
> **maletek said:**
> you will have to put the entry into fstab, it is simple```
/dev/sdb1 /media/disk ext3 ro 0 0
```replace the ext3 with the filesytem used on the disk

I tried with no success

---

### Post by Boondoklife on 2009-05-28
can you post your fstab

---

### Post by DieUbunt on 2009-05-28
> **maletek said:**
> can you post your fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID= XXXXXXXXXXXXXXXXXXXXXXXX                         /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID= XXXXXXXXXXXXXXXXXXXXXXXX                         none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/PACKARDBELL vfat ro,umask=0222 0 0

---

### Post by Boondoklife on 2009-05-28
> **DieUbunt said:**
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID= XXXXXXXXXXXXXXXXXXXXXXXX                         /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID= XXXXXXXXXXXXXXXXXXXXXXXX                         none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/PACKARDBELL vfat ro,umask=0222 0 0


have you made the mount point /media/PACKARDBELL ?
```
sudo mkdir /media/PACKARDBELL
```

---

### Post by DieUbunt on 2009-05-28
> **maletek said:**
> have you made the mount point /media/PACKARDBELL ?
```
sudo mkdir /media/PACKARDBELL
```
Yes but now I have the msg :

Impossible mounting volume PACKARDBELL

---

### Post by Boondoklife on 2009-05-28
> **DieUbunt said:**
> Yes but now I have the msg :

Impossible mounting volume PACKARDBELL


where are you seeing said message? and are you sure the filesystem is vfat? what did you format the drive with?

---

### Post by DieUbunt on 2009-05-28
> **maletek said:**
> where are you seeing said message? and are you sure the filesystem is vfat? what did you format the drive with?
its pendrive usb.
I took this information ( vfat ) from mtab.
I have the message by pop-up window:

only root can mount dev/sdb1 on /media/PACKARDBELL

Now gave me also this msg :

Impossible mounting <PACKARDBELL>
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

---

### Post by Boondoklife on 2009-05-28
this is normal as mounting is a superuser thing, you can try to get around this by adding user as an option in fstab. but do keep in mind if that is the case then there is nothing stoping the user from unmounting it.

---

### Post by DieUbunt on 2009-05-28
> **maletek said:**
> this is normal as mounting is a superuser thing, you can try to get around this by adding user as an option in fstab. but do keep in mind if that is the case then there is nothing stoping the user from unmounting it.
So what must I do to modify fstab in that way?
How could I umount later that volume?
thanks

---

### Post by DieUbunt on 2009-05-28
> **maletek said:**
> this is normal as mounting is a superuser thing, you can try to get around this by adding user as an option in fstab. but do keep in mind if that is the case then there is nothing stoping the user from unmounting it.
:D Perfect
I have resulted inserting in fstab the row :

/dev/sdb1 /media/PACKARDBELL vfat user,ro,umask=0222 0 0

Good
It's that I wanted
Thanks a lot

---

### Post by Boondoklife on 2009-05-28
> **DieUbunt said:**
> its pendrive usb.
I took this information ( vfat ) from mtab.
I have the message by pop-up window:

only root can mount dev/sdb1 on /media/PACKARDBELL

Now gave me also this msg :

Impossible mounting <PACKARDBELL>
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
this is because it is not there to begin with and when you plug it in dbus tries to mount it and the drive name is already taken.

ok let's go about this another way that may be more user friendly to you, get rid of that line in the fstab. then put the drive in and wait for it to mount and show up on the desktop. from there right click on it and goto the drive tab and click on settings. from there add ro as an option and see what you get.

---

### Post by DieUbunt on 2009-05-29
> **maletek said:**
> this is because it is not there to begin with and when you plug it in dbus tries to mount it and the drive name is already taken.

ok let's go about this another way that may be more user friendly to you, get rid of that line in the fstab. then put the drive in and wait for it to mount and show up on the desktop. from there right click on it and goto the drive tab and click on settings. from there add ro as an option and see what you get.
Thanks a lot 
Now It works fine and I know a little more about fstab and mtab functionality

Bye bye:D

---


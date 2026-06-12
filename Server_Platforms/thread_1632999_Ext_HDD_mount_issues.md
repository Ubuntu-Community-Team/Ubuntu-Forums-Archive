---
title: "Ext HDD mount issues"
date: 2010-11-28
forum: Server Platforms
---

### Post by yettiman2208 on 2010-11-28
I have an external hfsplus formatted HDD which does not have journaling enabled.

The drive has full read and write abilities from the linux box, but only after I unmount and remount the drive. 

Whenever the machine restarts, I have to manually unmount the drive and then remount with these settings.(even root does not have rw access upon bootup)

```
sudo umount /dev/sdb1
sudo mount -t hfsplus -o rw,force /dev/sdb1 /media/WD
```

I am fairly sure it is an issue with the fstab (i think)
But I am fairly noobish in a lot of this stuff.

this is the fstab at the moment.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=06c77706-4d3e-4d83-9f90-1ea652fb1043 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=2c75daaf-e480-4197-8fe3-b0a7bd31d31e none            swap    sw           $
/dev/sdb1 /media/WD hfsplus rw,user,auto,uid=1000,gid=1000 0 0


any assistance would be much appreciated!

-a large yetti

---

### Post by HermanAB on 2010-11-29
Howdy,

/media is used for removable media not defined in fstab.
/mnt is used for fixed media defined in fstab.

---

### Post by yettiman2208 on 2010-11-29
Oh I see,

so I should remove the fstab entry and then just set up a script to run the sudo mount options that I am looking for at every boot?

-a large yetti

---

### Post by yettiman2208 on 2010-11-30
Sorry for the bump.

But does anyone have any ideas on this?

Do I need to change my fstab settings in order to do this?

---


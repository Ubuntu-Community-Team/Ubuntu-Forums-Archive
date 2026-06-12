---
title: "should a usb drive mount differently from an internal drive in fstab?"
date: 2009-12-18
forum: Server Platforms
---

### Post by mendo on 2009-12-18
i am attempting to mount an external usb drive with the exact same options in fstab as an internal drive that behaves wonderfully.  here's the entries for the internal and external drives, respectively:

/dev/sda1  /mnt/data               vfat  users,auto,exec,umask=000
/dev/sdc1  /media/external/backup  vfat  users,auto,exec,umask=000

the samba shares for both disks are identical.

what gives??

thanks.

---

### Post by mendo on 2009-12-20
nevermind.  the usb drive was unplugged.  sorry.

---


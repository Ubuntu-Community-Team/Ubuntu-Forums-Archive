---
title: "stopping fsck from running at boot constantly"
date: 2009-07-17
forum: Server Platforms
---

### Post by Vegan on 2009-07-17
I had a file system error, fixed \, but fsck continually wants to run at every boot which slows the process badly. Any way to change that behavior?

---

### Post by shizzy-t on 2009-07-17
You could edit /etc/fstab and change the last option for / from a 1 to 0.  This would tell fsck to skip the device.  

UUID=00000000000  /  ext3    defaults,errors=remount-ro 0       1
to
UUID=00000000000  /  ext3    defaults,errors=remount-ro 0       0

---

### Post by shredkingj on 2009-07-17
To stop fsck on boot on a volume, edit /etc/fstab.  The sixth column is where you configure that.  Set the value to 0.

Example:

/dev/sda3 /var ext3 acl,user_xattr 1 **0**

---


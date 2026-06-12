---
title: "scsi_id in udev rule not working properly"
date: 2010-05-15
forum: Server Platforms
---

### Post by Xhosa on 2010-05-15
I'm trying to use scsi_id to create a symlink with udev when I connect to an iscsi target.

My udev rule looks as follows:

```
BUS=="scsi", SYSFS{vendor}=="IET", SYSFS{model}=="VIRTUAL-DISK", KERNEL=="sd*", PROGRAM="/lib/udev/scsi_id --whitelisted --page=0x80 --device=/dev/%k", SYMLINK+="iscsi-%c{3}"
```


If I connect to a target with an iscsi lun with a serial number of 'hosta' then running udevadm test /sys/block/8:16 returns (among other things):

```
udevadm_test: DEVLINKS=/dev/block/8:16 /dev/disk/by-id/scsi-14945540000000000686f7374615f69736373690000000000 /dev/disk/by-path/ip-192.168.1.1:3260-iscsi-iqn.2010-05.com.example:target-lun-0 /dev/disk/by-uuid/02ee4b44-5954-4102-b4f4-7f962010059d /dev/iscsi-hosta
```

Which shows the symlink /dev/iscsi-hosta being created.  However this rule doesn't trigger properly when I disconnect and reconnect the device, and I end up with /dev/iscsi-

Any ideas?

EDIT: SOLVED!

As it turns out, /dev/%k isn't created until after these rules run.  Looking at some other examples, it appears that I need to use --device=$tempnode in the scsi_id line, and then it works. :)

---


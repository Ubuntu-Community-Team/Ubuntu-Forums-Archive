---
title: "Auto-Mounting Hotplugged USB HDD"
date: 2010-06-07
forum: Server Platforms
---

### Post by stefanadelbert on 2010-06-07
I have an Ubunutu Server (9.10) running and I've setup a bunch of daily backups in cron. The idea would be to rsync the backups with a USB HDD, if it is present.

I used to use usbmount to automatically mount a USB HDD when it was hotplugged, but usbmount seems to be deprecated now. I've tried to find the alternative and it seems to be a mixture of udev rules and fstab. A lot of what I've found seems to be old (potentially outdated) and I'm really confused now as to what I should be doing.

Some of what I've been looking at:
[LIST]
[*][http://reactivated.net/writing_udev_rules.html#sysfstree]("http://reactivated.net/writing_udev_rules.html#sysfstree")
[*][http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/]("http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/")
[*][http://www.disa.nu/pub/doc/sles10/usr/share/doc/manual/sles-admin_en/sec.udev.debug.html]("http://www.disa.nu/pub/doc/sles10/usr/share/doc/manual/sles-admin_en/sec.udev.debug.html")
[/LIST]

I've tried to setup a udev rule, but don't see the new device appearing under /dev when hotplugging. However, the device could be mounted from /dev/sdb1 after hotplugging:

[FONT="Courier New"] fdisk -l[/FONT]
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
```

I've tried [FONT="Courier New"]udevadm monitor[/FONT], but I can't tell if my rule is actually being run or if it matches the USB HDD.

My rule is ([FONT="Courier New"]/etc/udev/rules.d/010-usbhdd.rule[/FONT]):
```
SUBSYSTEM="scsi", ATTRS{vendor}="WD", ATTRS{model}="5000BEV External", NAME="usb/%k", SYMLINK="usb-backup"
```

[COLOR="Green"]Am I correct to expect [FONT="Courier New"]/dev/usb/usb-backup[/FONT] to appear? How do I even start debugging udev rule matching? Am I going about this the wrong way?[/COLOR]

Any help would be hugely appreciated.

Thanks
Stef



 lsusb
```
Bus 001 Device 012: ID 1058:0704 Western Digital Technologies, Inc.
```

 udevadm info -q all -n /dev/sdb1
```
P: /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/host14/target14:0:0/14:0:0:0/block/sdb/sdb1
N: sdb1
W: 27
S: block/8:17
S: disk/by-id/usb-WD_5000BEV_External_57442D57584E3530394C3131353238-0:0-part1
S: disk/by-path/pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0-part1
S: disk/by-uuid/edf6af26-69c6-4d05-a26a-7ccb43abe720
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/host14/target14:0:0/14:0:0:0/block/sdb/sdb1
E: MAJOR=8
E: MINOR=17
E: DEVNAME=/dev/sdb1
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_VENDOR=WD
E: ID_VENDOR_ENC=WD\x20\x20\x20\x20\x20\x20
E: ID_VENDOR_ID=1058
E: ID_MODEL=5000BEV_External
E: ID_MODEL_ENC=5000BEV\x20External
E: ID_MODEL_ID=0704
E: ID_REVISION=1.75
E: ID_SERIAL=WD_5000BEV_External_57442D57584E3530394C3131353238-0:0
E: ID_SERIAL_SHORT=57442D57584E3530394C3131353238
E: ID_TYPE=disk
E: ID_INSTANCE=0:0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usb-storage
E: ID_PATH=pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0
E: ID_FS_UUID=edf6af26-69c6-4d05-a26a-7ccb43abe720
E: ID_FS_UUID_ENC=edf6af26-69c6-4d05-a26a-7ccb43abe720
E: ID_FS_SEC_TYPE=ext2
E: ID_FS_VERSION=1.0
E: ID_FS_TYPE=ext3
E: ID_FS_USAGE=filesystem
E: DEVLINKS=/dev/block/8:17 /dev/disk/by-id/usb-WD_5000BEV_External_57442D57584E3530394C3131353238-0:0-part1 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/edf6af26-69c6-4d05-a26a-7ccb43abe720

```

---

### Post by arrange on 2010-06-07
Just out of curiosity: why do you think that "usbmount seems to be deprecated now"?

---

### Post by stefanadelbert on 2010-06-07
I went to the usbmount [project homepage]("http://usbmount.alioth.debian.org/") and there is a notice at the top of the page reading:
> Warning: The original author does not have enough time any more to actively maintain the USBmount package. It is therefore currently unmaintained.
Also, according to the history on the same page, the last activity on the project was:
> Version 0.0.14.1 (27-Jan-2007, latest release)...
which was over 3 years ago.

Am I wrong to assume that work stopped on the project a long time ago? Through other reading, which I can't track down anymore, I made the assumption that the project has been deprecated.

---

### Post by arrange on 2010-06-07
I don't know, but it looks like it is maintained in Ubuntu...

[http://changelogs.ubuntu.com/changelogs/pool/universe/u/usbmount/usbmount_0.0.19.1ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/u/usbmount/usbmount_0.0.19.1ubuntu1/changelog)
[http://packages.ubuntu.com/lucid/usbmount](http://packages.ubuntu.com/lucid/usbmount)

---

### Post by stefanadelbert on 2010-06-07
This is good news!

Many thanks
Stefan

---

### Post by stefanadelbert on 2010-06-07
I've managed to get things working now after a bit of hacking about. usbmount is broken in 9.10 because vol_id was replaced by blkid, it seems (see [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/usbmount/+bug/478487")).

usbmount is a relatively simple project (see [package details]("http://packages.ubuntu.com/lucid/usbmount")) in that it comprises scripts, config files and rule files (all flat files). So I chose to do a manual upgrade from the installed 0.0.17 to the latest 0.0.19.1. 0.0.19.1 is part of Ubuntu 10.04, so I could have done a dist-upgrade (9.10->10.04), but chose to upgrade just the package instead.

I then needed to undo the manual udev hacking I had done and remove the fstab reference to the USB drive and usbmount worked once again. Note that usbmount logs to syslog and can be configured to give more output for debugging by editing the config file.

```
vim /etc/usbmount/usbmount.conf [edit VERBOSE=...]
tail -f /var/log/syslog
```

I'm going to change my scripts over from using /media/usb0 to using the symlink in /var/run/usbmount rather. I think it'll be more reliable that way, because usbmount could end up mounting other devices at /media/usb0.

Hope this has helped someone.

---


---
title: "Help with UDEV rule on iscsi target"
date: 2009-09-04
forum: Server Platforms
---

### Post by TheR on 2009-09-04
Background: Learning KVM and iscsi on Ubuntu

I don't like the idea when iscsi drives are attached on target system, devices get names /dev/sdb, /dev/sdc. In virtual environment you get easly 100 targets and how about when I don't need that LUN 26 on drive iqn.2100-05.ozs.si:disks.sas anymore. Will my device /dev/sdbb still be there or will it be at /dev/sdba. And it is ugly anyway.

Partial solution can be found in /dev/disk/by-path/ where device is assigned by iscsi server name and lun.
ip-192.168.1.221:3260-iscsi-iqn.2100-05.si.ozs:diski.sas-lun-0
ip-192.168.1.221:3260-iscsi-iqn.2100-05.si.ozs:diski.sas-lun-0-part1
ip-192.168.1.221:3260-iscsi-iqn.2100-05.si.ozs:diski.sas-lun-0-part2
But this is ugly too. And doesn't tell much about what does one device contain.

On iscsi server I have LVM with logical volume names like wwwportal, dns1, dns2, windowsAD ..... and what I would like is  name devices on target with similar names /dev/iscsi/wwwportal, /dev/iscsi/dns1 ..... and the same way I will also name my KVM machines.

I know it can be done with udev rule calling extern script which would have to include some kind of conversion table which would return name for disk and lun. I also know that table must be edited each time new disk is added. But that is just about everything I know.

Can you help me with this please.
1. udev rule and into which file to put it
2. skeleton of shell script which would be called by rule


by
TheR

---


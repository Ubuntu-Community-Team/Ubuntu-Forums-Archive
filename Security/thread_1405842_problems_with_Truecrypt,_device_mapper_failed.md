---
title: "problems with Truecrypt, device mapper failed"
date: 2010-02-13
forum: Security
---

### Post by ernest_francis on 2010-02-13
Hi,

I am running Ubuntu 9.10 x64 (clean install) with TrueCrypt 6.3a I have an Aspire 5940G
and am using a Lian Li EX30 external enclosure box.

I am trying to mount a Truecrupt volume from the box and when I select /dev/sdb which is the device I wish to mount I get the following error:

device-mapper: resume ioctl failed: Invalid argument
Command failed

Yesterday I was mounting the volume with no problem. Now I have another encrypted hard disk and it mounts with no problem using the external box.

FDISK on the non mounting HD gives the following:
Disk /dev/sdb: 750.2 GB, 750155292160 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08645a3f

Disk /dev/sdb doesn't contain a valid partition table


FDISK on the mounting HD gives the following:
Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fb569b5

They are both samsung HDD, exactly the same ?

The disk utility cannot retrieve the SMART info for either of them.


Any extra info please ask, I am a newbie so if you want me to get info out of any logs etc, please be precise on how to retrieve it, many thanks.

Ernest

---

### Post by ernest_francis on 2010-02-13
This is weird. When I connect the EX-30 via the USB cable to the laptop I cannot mount one of the external hd's but when I use the e-sata cable I can.

Any ideas? As I do need to use the usb cable as without the usb i cannot see the other two hds on the ex-30 as they are raided ?

Thanks
Ernest

---

### Post by chewearn on 2010-02-13
Okay, not sure if this will solve your problem.

I noticed you created the truecrypt volume on the harddisk device, i.e. /dev/sdb.  I always create the volume on the first partition, i.e. /dev/sdb1.

In other words, your harddisk lacks a primary partition.

---


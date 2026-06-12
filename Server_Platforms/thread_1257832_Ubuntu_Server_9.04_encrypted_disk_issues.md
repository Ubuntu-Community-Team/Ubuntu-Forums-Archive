---
title: "Ubuntu Server 9.04 encrypted disk issues"
date: 2009-09-04
forum: Server Platforms
---

### Post by lostforwords88 on 2009-09-04
Hello,

Recently upgraded my server from slackware to Ubuntu 9.04 server for reasons I'm not sure of now. Anyway, things mostly seem to be working except for one vital part. I have 3 external hard disks. Each of them can be attached via esata or USB. 2 500GB drives and 1 1000Gb drive. They each are encrypted via cryptsetup. The 500's mount fine, but the 1000Gb drive does not.

Here is what I've dug up so far:

from dmesg:

```
[    4.401868] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EAVS-00D 01.0 PQ: 0 ANSI: 5
[    4.402165] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.402227] sd 2:0:0:0: [sdc] Write Protect is off
[    4.402233] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.402332] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.402549] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.402610] sd 2:0:0:0: [sdc] Write Protect is off
[    4.402616] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.402714] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.402726]  sdc: [COLOR=Red]**unknown partition table**[/COLOR]
[    4.420130] sd 2:0:0:0: [sdc] Attached SCSI disk
```fdisk -l

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976762583+  ee  GPT

```When trying to mount via cryptsetup:

```
cryptsetup luksOpen /dev/sdc1 sdc1
Command failed: Device /dev/sdc1 doesn't exist or access denied.
```

/dev/sdc1 doesn't exist. So I manually create it. Then run cryptsetup again:

```
cryptsetup luksOpen /dev/sdc1 sdc1
Command failed: Can't open device /dev/sdc1 for exclusive read-only access.
```


All this worked fine on slackware on the same box. I installed 9.04 on my desktop machine just as a test, and got the same issue when trying to do anything with the disk over USB or eSATA. I've tried several different version of cryptsetup. I think the issue stems from the dmesg entry complaining about "unknown partition table". But why would it work on one OS and not another if it was an issue with the disks partition table? I've even run a couple live CDs (slax) that were able to access it. I've done a bug search via google and couldn't find anything exactly describing it.

Any ideas?

Thanks,

---

### Post by HermanAB on 2009-09-04
The root of the problem is certainly the "sdc: unknown partition table" message. Whether it is a bug in Slackware, Ubuntu or a hardware failure is hard to determine.  The only solution I can think of is to read the disk with a Slackware CD or virtual machine and copy the data to another disk formatted with Ubuntu.

---


---
title: "Errors after adding HDD(s)"
date: 2010-01-26
forum: Server Platforms
---

### Post by G1ZmO65 on 2010-01-26
I have added 3 250GB HDDs to my server but have encountered problems

I formatted the drives ext3 with gparted then added the following to fstab

```
/dev/sdb     /media/250GB1   ext3   defaults   0   2
/dev/sdc     /media/250GB2   ext3   defaults   0   2
/dev/sdd     /media/250GB3   ext3   defaults   0   2
```

The output of "lshw -C disk" is

```
  *-disk:0
       description: ATA Disk
       product: Maxtor 6Y080L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y25LSKVC
       size: 76GiB (81GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d119d119
  *-disk:1
       description: ATA Disk
       product: WDC WD2500JB-32F
       vendor: Western Digital
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 15.0
       serial: WD-WMAEP1048965
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000422be
  *-disk:2
       description: ATA Disk
       product: WDC WD2500JB-32F
       vendor: Western Digital
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/sdc
       version: 15.0
       serial: WD-WMAEP1046561
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c1c07
  *-disk:3
       description: ATA Disk
       product: WDC WD2500JB-32F
       vendor: Western Digital
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/sdd
       version: 15.0
       serial: WD-WMAEP1063870
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00079435
```


On doing "mount -a" I get:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Can anyone point me in the right direction?

Many thanks

Paul

---

### Post by FuturePilot on 2010-01-26
You have to specify the partition number. If you only put 1 partition on each disk, it will be

```
/dev/sdb**1** /media/250GB1   ext3   defaults   0   2
/dev/sdc**1** /media/250GB2   ext3   defaults   0   2
/dev/sdd**1** /media/250GB3   ext3   defaults   0   2
```

---

### Post by G1ZmO65 on 2010-01-27
Ah! Will try this when I get home from work tonight as my ssh login isnt working doh!

Cheers

Paul

---

### Post by G1ZmO65 on 2010-02-03
Sorry I forgot to get back to you to say thanks for this info.

Works perfectly now.

Thanks again :)

Paul

---


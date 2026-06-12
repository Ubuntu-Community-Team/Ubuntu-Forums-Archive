---
title: "How to find physical disk in failed md array"
date: 2011-02-24
forum: Server Platforms
---

### Post by geraldbrandt on 2011-02-24
Hi,

I have a RAID6 md array, and one drive has failed.  mdstat tells me it's /dev/sdc.

How do I find out which physical disk this is?  I don't want to end up pulling the wrong one.

Gerald

---

### Post by joberly on 2011-02-24
You need to find out what the UUID is,

```
ls /dev/disk/by-uuid
```

Then you can use a tool like lshw to determine what disk the UUID belongs to.

For example, lshw tells me

```
*-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@6:0.0.0,1
                   logical name: /dev/sdd1
                   version: 1.0
                   serial: 86a9acea-2b12-4c71-9199-470fa7a80556
                   size: 931GiB
                   capacity: 931GiB

```

Therefore, I know that sdd1 belongs to that UUID  (serial: as shown here)

It will also tell me what drive it is, so I can be sure to pull the correct one:

```
 *-disk:2
                description: ATA Disk
                product: WDC WD1001FALS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@6:0.0.0
                logical name: /dev/sdd
                version: 05.0
                serial: WD-WCATR5089705
                size: 931GiB (1TB)

```

In this case, you can physically match the serial # with what's on the drive. (Or just use the model number/name if they are different vendors.)

---

### Post by YesWeCan on 2011-02-25
Or...
Go to System/Administration/Disk Utility and it will show you all info for each disk.

---

### Post by rubylaser on 2011-02-25
Here's how I do it from the cli
```
lshw -businfo -C disk
```

---


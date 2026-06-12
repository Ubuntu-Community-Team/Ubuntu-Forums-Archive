---
title: "(raid) When a disk dies..."
date: 2008-05-21
forum: Server Platforms
---

### Post by mikedehaan on 2008-05-21
I've noticed in Fiesty and Gutsy that device names are not exactly static as they once were.  IDE names like hda are switching to sda, but this doesn't seem to be something you can rely on.  I've recently built a raid array on a gutsy server and I'm worried about what will happen when a drive dies.

In previous versions of ubuntu (and other linux distros) hda meant the master device on the primary channel while hdb was the slave on the primary channel.  This made it easy to trace which physical device needed to be replace in a raid configuration.  Is this possible today with the device names changing on boot?  

I've also noticed that in 8.04 the device names will re-adjust upon boot.  Example: prior to boot I have two devices sda, sdb.  After reboot my sda device fails to power up.  In this case sdb would become sda upon boot.

Adding to my uniquely identifying drive problem, the UUID's seem to match on both drives.  I've tried both the 'vol_id' command and the 'blkid' command.

```
# blkid /dev/sda
/dev/sda: UUID="c2b492f0-d448-a93b-6afb-c1b4b68b5d8b" TYPE="mdraid"
# blkid /dev/sdb
/dev/sdb: UUID="c2b492f0-d448-a93b-6afb-c1b4b68b5d8b" TYPE="mdraid"
```

```

# vol_id /dev/sda
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=f092b4c2:3ba948d4:b4c1fb6a:8b5d8bb6
ID_FS_UUID_ENC=f092b4c2:3ba948d4:b4c1fb6a:8b5d8bb6
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
# vol_id /dev/sdb
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=f092b4c2:3ba948d4:b4c1fb6a:8b5d8bb6
ID_FS_UUID_ENC=f092b4c2:3ba948d4:b4c1fb6a:8b5d8bb6
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

Any ideas on how I should be identifying a dead drive in my server's chassis?

Thanks.

---

### Post by windependence on 2008-05-21
First of all hda is an ATA drive and sda is either a SCSI drive or sometimes a SATA drive. These are just types of drives detected by the system, they don't arbitrarily change when you boot. Neither do the other devices UNLESS like you said, one of the drives is not recognized during boot. Windoze does the same basic thing. So if you have sda and sdb and then sda cannot be recognized by the system at boot or is removed, sdb becomes sda in your fstab.

In a "real" RAID configuration your disks become one volume and are named accordingly. Say you have 3 drives in RAID 5. All three disks become collectively /dev/sda. The only way you would know the drive is bad is if you run monitoring software, or if your drive has an error light like most SCSI drives do. I am talking about hardware RAID here as i do not recommend software RAID, and one of the reasons is exactly what you are telling me, it's very hard to rebuild the array exactly as it was.

-Tim

---

### Post by mikedehaan on 2008-05-21
Unfortunately, the device names were changing arbitrarily upon boot when I was running Feisty.  I didn't understand what was going on until I found the following post by Wolki:

[http://ubuntuforums.org/showthread.php?t=532823&page=3](http://ubuntuforums.org/showthread.php?t=532823&page=3)

I've since upgraded to Gutsy, but now ALL hard drive devices are using the SCSI/SATA naming convention.  This wouldn't be a problem if device names were static (linking device names to physical devices/channels), but they're not.  I'm now using UUID's in my fstab though apparently the UUID of each drive in my raid is identical.  Not exactly something I could use to uniquely identify my drive.

I have another system running CentOS (an old version) with an IDE raid.  In this system, I am able to write the device name on a post-it and stick it on the physical drive if I wanted.  If one of the drives in the middle of the hd* naming scheme died, that name didn't appear and was not re-used by another device.  Therefore when I saw a degraded raid and hdi was missing, I could easily trace the IDE cable to the drive and swap it out.

I realize my concern is null/void in a hardware raid.  Unfortunately, real hardware raid cards are quite expensive, and software raids have done well for my in the past (save for this new development).  I'm sure my problem is not unique as configuring software raids is a very common practice.  I'm hoping someone will shed some light on the recovery process.

In the meantime, the work around I plan on using is to query the device's serial number using hdparm.  This should allow me to determine which drive is bad by process of elimination.

```
hdparm -I /dev/sda | grep "Serial Number" | awk '{print substr($0, 22)}'
```

Any thoughts as to whether or not this is a good idea?

Thanks.

---


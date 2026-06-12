---
title: "RAID 5 - static device name assignment"
date: 2008-07-14
forum: Server Platforms
---

### Post by lenchen on 2008-07-14
Hi,

I'm using a RAID 5 built up of three partitions on separate drives. After rebooting it often occurs that the device names change, e.g. from

md5 : active raid5 sda7[0] sdc7[2] sdb7[1]

to

md5 : active raid5 sde7[0] sdf7[2] sdg7[1]

RAID functionality is usually not affected by this but it poses some problems for me because - among other things - several of my monitoring scripts use the drives' device names.

Is it possible to make the device names static (the cause for the changing hard drive device names is the card reader, which grabs sde, sdf, sdg and sdh one time and sda, sdb, sdc and sdd next time - so a corresponding question would be how to assign the card reader slots static device names).

/etc/fstab:

# /dev/md5 (encrypted using dm-crypt with luks)
/dev/mapper/md5 /home ext3 noauto 0 0

/etc/mdadm/mdadm.config:

ARRAY /dev/md5 level=raid5 num-devices=3 UUID=d81a69da:7684046d:90f27b59:1cd14845

After bootup I do the following:

cryptsetup luksOpen /dev/md5 md5
mount /dev/mapper/md5 /home

Thanks

Lena

---

### Post by Krupski on 2008-07-15
> **lenchen said:**
> Hi,

I'm using a RAID 5 built up of three partitions on separate drives. After rebooting it often occurs that the device names change, e.g. from

md5 : active raid5 sda7[0] sdc7[2] sdb7[1]

to

md5 : active raid5 sde7[0] sdf7[2] sdg7[1]

RAID functionality is usually not affected by this but it poses some problems for me because - among other things - several of my monitoring scripts use the drives' device names.

Is it possible to make the device names static (the cause for the changing hard drive device names is the card reader, which grabs sde, sdf, sdg and sdh one time and sda, sdb, sdc and sdd next time - so a corresponding question would be how to assign the card reader slots static device names).


I had a similar problem. I solved it by referring to drives "by-id". Look at this:

```

root@storage:/# ls /dev/disk/by-id | sort
**ata-Sony_NCFC4G_011910H0207P2150**
ata-Sony_NCFC4G_011910H0207P2150-part1
ata-Sony_NCFC4G_011910H0207P2150-part2
ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948
ata-WDC_WD10EACS-00D6B0_WD-WCAU40433302
**edd-int13_dev80**
edd-int13_dev80-part1
edd-int13_dev80-part2
md-uuid-8684a70e:b387a3aa:a4949914:14f104a3
**scsi-1ATA_Sony_NCFC4G_011910H0207P2150**
scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part1
scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part2
scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40312948
scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40433302

```

I bold highlighted every name that represents my boot/root drive. Although the boot drive sometimes shows up as /dev/sda and sometimes /dev/sdc, the "by-id" names ALWAYS stay the same.

So, just execute "ls /dev/disk/by-id | sort" and find the ID name of the device(s) you care about and use THOSE names in your script instead.

By the way, these names also work in FSTAB and MENU.LST (from GRUB).

Be sure to use the whole name... like this example:

[B]/dev/disk/by-id/ata-Sony_NCFC4G_011910H0207P2150
[/B]
...or this...:

[B]/dev/disk/by-id/edd-int13_dev80
[/B]

(note that the lines above are MY devices - you have to find out what YOUR device names are).

Good luck!

-- Roger

---


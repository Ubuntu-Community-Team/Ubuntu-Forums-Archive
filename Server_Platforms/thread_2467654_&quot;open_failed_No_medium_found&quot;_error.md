---
title: "&quot;open failed: No medium found&quot; error?"
date: 2021-10-03
forum: Server Platforms
---

### Post by Heeter on 2021-10-03
Hi all,

I have a Dell R610 with H700 Raid controller and 6 x 600gigs in a RAID10 config. By the looks of the physical side of the server, everything is running smoothly.

But I have this showing up:

```

root@serv:/opt# pvdisplay
  /dev/sdb: open failed: No medium found
  /dev/sdd: open failed: No medium found
  /dev/sdb: open failed: No medium found
  /dev/sdd: open failed: No medium found
  --- Physical volume ---
  PV Name               /dev/sdc5
  VG Name               LVG
  PV Size               1.63 TiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              428354
  Free PE               0
  Allocated PE          428354
  PV UUID               7MPj3o-CtcI-caG0-2fmm-JQDJ-yZ3G-11SfX1
   
root@serv:/opt#

```

I dont understand why these "open failed: No medium found" are showing up, and if I can clear them? I am presuming this is leftover from the 18LTS to 20LTS upgrade server took a few days ago, but cannot say for sure, or if its part of the LVM

I do have an external backup drive automounted:
```

/dev/sda1: LABEL="SERV_BACKUP" UUID="a66c203c-2938-490a-9b4e-221eb8f3dff8" TYPE="ext4" PARTUUID="0350c369-01"

```

Dont think that is the issue, there are no cd drives on the unit

Regards

---

### Post by MAFoElffen on 2021-10-06
It would be helpful to all others if they could see what is going on with your system and hardware. Such as running the system-info report in my signature. It will query the system ,including the disks, fstab file and a mounts.

That would give you and others a good picture. It will also paste the report to a pastebin, which you can post the link in your post, to show those results.

Just from the things you said, I am guessing you have 4 disks, RAID1 of at least 2 disks, and LVM... But have no idea how those are laid out, or what disks are involved in what.

---

### Post by Heeter on 2021-10-06
> **MAFoElffen said:**
> It would be helpful to all others if they could see what is going on with your system and hardware. Such as running the system-info report in my signature. It will query the system ,including the disks, fstab file and a mounts.

That would give you and others a good picture. It will also paste the report to a pastebin, which you can post the link in your post, to show those results.

Just from the things you said, I am guessing you have 4 disks, RAID1 of at least 2 disks, and LVM... But have no idea how those are laid out, or what disks are involved in what.

Hey thank you for getting back to me, I will try out your script and report back

---


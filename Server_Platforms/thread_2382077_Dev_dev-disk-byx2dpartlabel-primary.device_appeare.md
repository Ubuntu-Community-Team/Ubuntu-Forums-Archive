---
title: "Dev dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths"
date: 2018-01-08
forum: Server Platforms
---

### Post by jason63 on 2018-01-08
Ubuntu 16.04.1

syslog is filled with hundreds of these per day 


```
Jan  8 16:47:48 ubuntu-server systemd[1]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata5/host5/target5:0:0/5:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:1f.2/ata6/host6/target6:0:0/6:0:0:0/block/sdf/sdf1Jan  8 16:47:48 ubuntu-server systemd[1702]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata6/host6/target6:0:0/6:0:0:0/block/sdf/sdf1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host3/target3:0:0/3:0:0:0/block/sdc/sdc1
Jan  8 16:47:48 ubuntu-server systemd[1]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata5/host5/target5:0:0/5:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host3/target3:0:0/3:0:0:0/block/sdc/sdc1
Jan  8 16:47:48 ubuntu-server systemd[1702]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata6/host6/target6:0:0/6:0:0:0/block/sdf/sdf1 and /sys/devices/pci0000:00/0000:00:1f.2/ata5/host5/target5:0:0/5:0:0:0/block/sde/sde1
Jan  8 16:47:48 ubuntu-server systemd[1702]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata6/host6/target6:0:0/6:0:0:0/block/sdf/sdf1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host3/target3:0:0/3:0:0:0/block/sdc/sdc1
Jan  8 16:47:48 ubuntu-server systemd[1]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata5/host5/target5:0:0/5:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host3/target3:0:0/3:0:0:0/block/sdc/sdc1
Jan  8 16:47:48 ubuntu-server systemd[1702]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata6/host6/target6:0:0/6:0:0:0/block/sdf/sdf1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host3/target3:0:0/3:0:0:0/block/sdc/sdc1
Jan  8 16:47:48 ubuntu-server systemd[1]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata5/host5/target5:0:0/5:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host3/target3:0:0/3:0:0:0/block/sdc/sdc1
Jan  8 16:47:48 ubuntu-server systemd[1]: dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device: Dev dev-disk-by\x2dpartuuid-7b0a167a\x2db0cf\x2d4129\x2db8e9\x2d772fa29f0163.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata5/host5/target5:0:0/5:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:1f.2/ata6/host6/target6:0:0/6:0:0:0/block/sdf/sdf1
```


etc ... etc..



blkid output reveals that the raid5 array all share the same UUID (they always have). This has not been an issue in the past and I only save 7 days worth of logs so I can't pinpoint when this started. Perhaps a few weeks ago when I saw and mdadm update?

blkid output

```

/dev/sda1: UUID="5aad22f9-c314-0691-4478-04e47cbe7064" UUID_SUB="ea178cb1-3514-3332-5d53-837815b83c15" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTLABEL="RAIDDISK-1" PARTUUID="d28634c9-8efd-4e52-94bb-b72f2d0324b1"
/dev/sdc1: UUID="5aad22f9-c314-0691-4478-04e47cbe7064" UUID_SUB="608f49fa-4cf3-2804-c1b9-6336533cd956" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTLABEL="RAIDDISK-2" PARTUUID="7b0a167a-b0cf-4129-b8e9-772fa29f0163"
/dev/sdd1: UUID="5aad22f9-c314-0691-4478-04e47cbe7064" UUID_SUB="d66eef15-0016-686f-8544-e9aa5a01e7e5" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTLABEL="RAIDDISK-3" PARTUUID="c1c68d22-142f-4b4c-bc83-98023fedd333"
/dev/sde1: UUID="5aad22f9-c314-0691-4478-04e47cbe7064" UUID_SUB="87b135b2-8ddc-8103-2c2c-267ad2c1fa13" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTLABEL="RAIDDISK-4" PARTUUID="7b0a167a-b0cf-4129-b8e9-772fa29f0163"
/dev/sdf1: UUID="5aad22f9-c314-0691-4478-04e47cbe7064" UUID_SUB="69246ca8-554e-1121-2450-da62b32b7cc7" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTLABEL="RAIDDISK-5" PARTUUID="7b0a167a-b0cf-4129-b8e9-772fa29f0163"

```

The raid5 array works fine and is not degraded. Easily hits 105 MB/s over samba share.


What is causing this issue? I've seen somewhere that disks in raid arrays are given the same UUID? I've also noticed that 3 of the 5 disks in the array have the same PARTUUID.

What would have cause this or, what might have changed (upgraded) that would now flag this as an issue?


Thanks in advance guys!

---

### Post by DuckHook on 2018-01-08
*Thread moved to **Server Platforms** as the more appropriate forum.*

---


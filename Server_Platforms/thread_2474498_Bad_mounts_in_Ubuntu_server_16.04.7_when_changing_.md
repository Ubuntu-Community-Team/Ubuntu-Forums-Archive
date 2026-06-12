---
title: "Bad mounts in Ubuntu server 16.04.7 when changing to AHCI from IDE in BIOS"
date: 2022-05-01
forum: Server Platforms
---

### Post by Windowsxpnomore on 2022-05-01
Ubuntu Server 16.04.7 
current BIOS is IDE.
disks are 
```

$ df -H
Filesystem                    Size  Used Avail Use% Mounted on
udev                          4.2G     0  4.2G   0% /dev
tmpfs                         826M   13M  814M   2% /run
/dev/mapper/MediaServer-root   62G  9.1G   50G  16% /
tmpfs                         4.2G     0  4.2G   0% /dev/shm
tmpfs                         5.3M     0  5.3M   0% /run/lock
tmpfs                         4.2G     0  4.2G   0% /sys/fs/cgroup
/dev/sde1                     3.0T  2.3T  566G  80% /mnt/BackupDisk
/dev/sdd1                     3.0T  2.4T  403G  86% /mnt/Data1
/dev/sdc1                     3.0T  2.5T  391G  87% /mnt/BackupDisk1
/dev/sdb1                     3.0T  2.3T  583G  80% /mnt/Data
/dev/sda1                     239M  162M   65M  72% /boot
cgmfs                         103k     0  103k   0% /run/cgmanager/fs
tmpfs                         826M     0  826M   0% /run/user/1000


```
I changed the BIOS to use AHCI and rebooted.
```

Apr 29 18:48:19 MediaServer kernel: [    0.794877] ahci 0000:00:1f.2: version 3.0
Apr 29 18:48:19 MediaServer kernel: [    0.798296] [drm] Initialized drm 1.1.0 20060810
Apr 29 18:48:19 MediaServer kernel: [    0.806869] alx 0000:02:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [94:de:80:60:46:9f]
Apr 29 18:48:19 MediaServer sensors[762]: Physical id 0:  +48.0°C  (high = +85.0°C, crit = +105.0°C)
Apr 29 18:48:19 MediaServer kernel: [    0.811213] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1f impl SATA mode
Apr 29 18:48:19 MediaServer kernel: [    0.812554] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
Apr 29 18:48:19 MediaServer kernel: [    0.824800] alx 0000:02:00.0 eth1: renamed from eth0
Apr 29 18:48:19 MediaServer kernel: [    0.843737] scsi host0: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.844738] scsi host1: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.845691] scsi host2: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.846627] scsi host3: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.847561] scsi host4: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.848466] scsi host5: ahci
Apr 29 18:48:19 MediaServer sensors[762]: Core 0:         +43.0°C  (high = +85.0°C, crit = +105.0°C)
Apr 29 18:48:19 MediaServer kernel: [    0.849319] ata1: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16100 irq 25
Apr 29 18:48:19 MediaServer kernel: [    0.850152] ata2: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16180 irq 25
Apr 29 18:48:19 MediaServer kernel: [    0.850978] ata3: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16200 irq 25
Apr 29 18:48:19 MediaServer kernel: [    0.851803] ata4: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16280 irq 25
Apr 29 18:48:19 MediaServer kernel: [    0.852622] ata5: SATA max UDMA/133 abar m2048@0xf7e16000 port 0xf7e16300 irq 25
Apr 29 18:48:19 MediaServer kernel: [    0.853430] ata6: DUMMY
Apr 29 18:48:19 MediaServer kernel: [    0.867232] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Apr 29 18:48:19 MediaServer kernel: [    0.867241] ahci 0000:05:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
Apr 29 18:48:19 MediaServer kernel: [    0.867767] scsi host6: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.867869] scsi host7: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.867960] scsi host8: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.868055] scsi host9: ahci
Apr 29 18:48:19 MediaServer kernel: [    0.868114] ata7: SATA max UDMA/133 abar m2048@0xf7c40000 port 0xf7c40100 irq 26
Apr 29 18:48:19 MediaServer kernel: [    0.868124] ata8: SATA max UDMA/133 abar m2048@0xf7c40000 port 0xf7c40180 irq 26
Apr 29 18:48:19 MediaServer kernel: [    0.868133] ata9: SATA max UDMA/133 abar m2048@0xf7c40000 port 0xf7c40200 irq 26
Apr 29 18:48:19 MediaServer kernel: [    0.868142] ata10: SATA max UDMA/133 abar m2048@0xf7c40000 port 0xf7c40280 irq 26
..
Apr 29 18:48:19 MediaServer kernel: [    1.171207] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.171295] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.171336] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.171389] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.171421] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.172106] ata4.00: ATA-9: WDC WD30EFRX-68EUZN0, 82.00A82, max UDMA/133
Apr 29 18:48:19 MediaServer kernel: [    1.172152] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 29 18:48:19 MediaServer kernel: [    1.172334] ata5.00: ATA-9: WDC WD30EFRX-68EUZN0, 80.00A80, max UDMA/133
Apr 29 18:48:19 MediaServer kernel: [    1.172369] ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 29 18:48:19 MediaServer kernel: [    1.172534] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Apr 29 18:48:19 MediaServer kernel: [    1.172573] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT1._GTF] (Node ffff8802169c3d20), AE_NOT_FOUND (20150930/psparse-542)
Apr 29 18:48:19 MediaServer kernel: [    1.172641] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Apr 29 18:48:19 MediaServer kernel: [    1.172674] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT2._GTF] (Node ffff8802169c3d98), AE_NOT_FOUND (20150930/psparse-542)
Apr 29 18:48:19 MediaServer kernel: [    1.172737] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Apr 29 18:48:19 MediaServer kernel: [    1.172779] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT3._GTF] (Node ffff8802169c3e10), AE_NOT_FOUND (20150930/psparse-542)
Apr 29 18:48:19 MediaServer kernel: [    1.172877] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Apr 29 18:48:19 MediaServer kernel: [    1.172908] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT4._GTF] (Node ffff8802169c3e88), AE_NOT_FOUND (20150930/psparse-542)
Apr 29 18:48:19 MediaServer kernel: [    1.172986] ata3.00: ATA-8: HGST HDN724030ALE640, MJ8OA5E0, max UDMA/133
Apr 29 18:48:19 MediaServer kernel: [    1.173016] ata3.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 29 18:48:19 MediaServer kernel: [    1.173050] ata2.00: ATA-8: HGST HDN724030ALE640, MJ8OA5E0, max UDMA/133
Apr 29 18:48:19 MediaServer kernel: [    1.173072] ata2.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 29 18:48:19 MediaServer kernel: [    1.173100] ata4.00: configured for UDMA/133
Apr 29 18:48:19 MediaServer kernel: [    1.173226] ata5.00: configured for UDMA/133
Apr 29 18:48:19 MediaServer kernel: [    1.178318] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT2._GTF] (Node ffff8802169c3d98), AE_NOT_FOUND (20150930/psparse-542)
Apr 29 18:48:19 MediaServer kernel: [    1.179990] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
Apr 29 18:48:19 MediaServer kernel: [    1.181185] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT1._GTF] (Node ffff8802169c3d20), AE_NOT_FOUND (20150930/psparse-542)
Apr 29 18:48:19 MediaServer kernel: [    1.182465] ata1.00: ATA-8: WDC WD5000BPKX-00HPJT0, 01.01A01, max UDMA/133
Apr 29 18:48:19 MediaServer smartd[709]: Drive: DEVICESCAN, implied '-a' Directive on line 21 of file /etc/smartd.conf
Apr 29 18:48:19 MediaServer kernel: [    1.184130] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 29 18:48:19 MediaServer kernel: [    1.186359] ata3.00: configured for UDMA/133
Apr 29 18:48:19 MediaServer kernel: [    1.187160] ata10: SATA link down (SStatus 0 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.187190] ata8: SATA link down (SStatus 0 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.187222] ata9: SATA link down (SStatus 0 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.187254] ata7: SATA link down (SStatus 0 SControl 300)
Apr 29 18:48:19 MediaServer kernel: [    1.192746] ata2.00: configured for UDMA/133

```

However the disks are "screwed" - that is to say 
/mnt/Data and /mnt/Data1 are mounted on different drives but BOTH point to the same data on /mnt/Data. a ls - /mnt/Data and of /mnt/Data1 shows the same contents of /mnt/Data. 
likewise 
ls /mnt/BackupDisk and /mnt/BackupDisk1 point to the same data on /mnt/BackupDisk1

I unmounted /mnt/BackupDisk1 only for the mounts to /mnt/Data and /mnt/Data1 to disappear.
with that I rebooted the server and changed back in the BIOS the setting to IDE and rebooted again.
Everything is fine again. that is to say /mnt/Data and /mnt/Data1 point to different and correct data contents etc.

I see a lot of this today though with IDE setting

```

May  1 11:57:21 MediaServer systemd[8238]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb
May  1 11:57:21 MediaServer systemd[1316]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb/sdb1
May  1 11:57:21 MediaServer systemd[8238]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb/sdb1
May  1 11:57:21 MediaServer systemd[8238]: dev-disk-by\x2dpartlabel-primary.device: Dev dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1 and /sys/devices/pci0000:00/0000:00:1f.5/ata3/host2/target2:0:0/2:0:0:0/block/sde/sde1
May  1 11:57:21 MediaServer systemd[1316]: dev-disk-by\x2dpartlabel-primary.device: Dev dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1 and /sys/devices/pci0000:00/0000:00:1f.5/ata3/host2/target2:0:0/2:0:0:0/block/sde/sde1
May  1 11:57:21 MediaServer systemd[8238]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc
May  1 11:57:21 MediaServer systemd[8238]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
May  1 11:57:21 MediaServer systemd[1]: dev-disk-by\x2dpartlabel-primary.device: Dev dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.5/ata3/host2/target2:0:0/2:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
May  1 11:57:21 MediaServer systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
May  1 11:57:21 MediaServer systemd[1316]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd
May  1 11:57:21 MediaServer systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd
May  1 11:57:21 MediaServer systemd[1316]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:1/1:0:1:0/block/sdd/sdd1
May  1 11:57:22 MediaServer systemd[1316]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda
May  1 11:57:22 MediaServer systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda
May  1 11:57:22 MediaServer systemd[1]: dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device: Dev dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:1/0:0:1:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1

sudo blkid
/dev/sdb1: UUID="b1e53181-cea5-4d59-a158-24f04c6c01de"  TYPE="ext4" PARTLABEL="Data"  PARTUUID="c2bda4aa-88dd-4f66-8939-76cd818e88dd"
/dev/sdc1:  UUID="4dabf6d5-dfcf-408b-a0dc-78a1a9d98f67" TYPE="ext4"  PARTLABEL="primary" PARTUUID="f5c5bc09-ac19-45d6-af63-6fdff545dd74"
/dev/sde1:  UUID="f11506de-57ff-4aa4-a685-6f104d5598d7" TYPE="ext4"  PARTLABEL="primary" PARTUUID="bef3d0ab-7c1c-4878-9e12-09c46f1f0c0e"
/dev/sdd1: UUID="76aa86e0-268e-4035-bbe4-af79a601f610" TYPE="ext4" PARTUUID="807faf72-23d9-4e1e-9d16-ab06b86b4c60"
/dev/sda1: UUID="50b5c091-2751-4974-9ba9-acfa8f05b939" TYPE="ext2" PARTUUID="0000b407-01"
/dev/sda5: UUID="R6mSX7-4AE1-uh7s-I3i0-afdf-g8wE-ex29b5" TYPE="LVM2_member" PARTUUID="0000b407-05"
/dev/mapper/MediaServer-root: UUID="eeff2e62-6d52-459f-857d-859e838b56c2" TYPE="ext4"
/dev/mapper/MediaServer-swap_1: UUID="9175ce59-ce94-4687-bca8-30caa37eed60" TYPE="swap"


```

Any idea what is wrong and how I can change to AHCI ?

---

### Post by TheFu on 2022-05-01
Do you realize that 16.04 standard support ended over a year ago? If you have registered this system for extended support, contact Canonical.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

As such, the only recommendation I have is to backup any data you don't want to lose and install either 20.04 or 22.04 (if you are brave) with AHCI enabled in the BIOS.  Be certain to capture the fstab lines for the non-OS partitions/file systems, so those can be easily but back. The UUIDs for them shouldn't change, but the UUIDs for the OS file systems/partitions will almost certainly change.

---

### Post by Windowsxpnomore on 2022-05-03
@TheFu - you did actually solve my problem. (although I havent upgraded to 18.04 or 20.04 yet). I looked at the fstab and saw that is wasnt using the UUID for the disks, reading up it seems that ubuntu now uses UUID as default. anyway I changed to fstab  
from 
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/MediaServer-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=50b5c091-2751-4974-9ba9-acfa8f05b939 /boot           ext2    defaults        0       2
#/dev/mapper/MediaServer-swap_1    swap    swap    sw    0    0
# /dev/md0    /mnt/data    ext4    defaults    0    0
/dev/sde1    /mnt/BackupDisk    ext4    defaults    0    0
/dev/sdc1    /mnt/BackupDisk1    ext4    defaults    0    0
/dev/sdd1     /mnt/Data1    ext4    defaults    0    0
/dev/sdb1    /mnt/Data    ext4    defaults    0    0

```
to
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/MediaServer-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=50b5c091-2751-4974-9ba9-acfa8f05b939 /boot           ext2    defaults        0       2
#/dev/mapper/MediaServer-swap_1    swap    swap    sw    0    0
# /dev/md0    /mnt/data    ext4    defaults    0    0
UUID=f11506de-57ff-4aa4-a685-6f104d5598d7    /mnt/BackupDisk ext4    defaults        0       0
UUID=4dabf6d5-dfcf-408b-a0dc-78a1a9d98f67     /mnt/BackupDisk1        ext4    defaults        0       0
UUID=76aa86e0-268e-4035-bbe4-af79a601f610    /mnt/Data1      ext4    defaults        0       0
UUID=b1e53181-cea5-4d59-a158-24f04c6c01de    /mnt/Data       ext4    defaults        0       0

```
and the mounts good.
changing the BIOS to AHCI and the mounts are still good whereas beforehand they were screwed..

---

### Post by TheFu on 2022-05-03
> **Windowsxpnomore said:**
> @TheFu - you did actually solve my problem. (although I havent upgraded to 18.04 or 20.04 yet). I looked at the fstab and saw that is wasnt using the UUID for the disks, reading up it seems that ubuntu now uses UUID as default.


The first time I was forced to change to UUIDs was around 2001.

UUIDs have been the default since **before** Ubuntu started.  It is amazing this is the first time you've run into any issue.  The order that devices (/dev/sda, b, c, d, ....) are found by the kernel is NOT guaranteed and hasn't been for over 15 yrs.

UUIDs where the first solution created by programmers that wasn't hardware dependent.  We could always specify partitions by the slot/controller/path/port# since the beginning. That is commonly used in enterprises or they use a WWN - world-wide-number, which has been part of disks for many decades.  Enterprise servers can have hundreds of disks connected to a server.  End-users found UUIDs easier.

Anyway, rather than using UUIDs, we can use the partition LABELs that we've set.  gparted can let us add labels to most partitions ... or file systems (that were they are really).  Then, instead of 
```
UUID=xxxxx-xxxxxx-xxx-x-x-x-x-x---x  ..... 
```
we can use 
```
LABEL=Human-Name  .... 
```
in the fstab line. The only mandate is that the LABEL be set and unique compared to all file systems in the system.

We can see all the different aliases we can use under /dev/disk/by-*/ ... there are multiple options.  Here's a system with just 2 physical disks:
```
$ find /dev/disk -type l  |wc -l
60
```
There are 60 different names for all the different file systems on that system. BTW, it has less than 1TB total storage. Some examples that I could use to mount would be 
```
./by-id/[COLOR="#008000"]wwn-0x500a07511faa44ad-part1[/COLOR]
./by-id/wwn-0x500a07511faa44ad-part2
   or
./by-id/ata-Micron_1100_MTFDDAV512TBN_17411FAA44AD-part1
./by-id/ata-Micron_1100_MTFDDAV512TBN_17411FAA44AD-part2

```
Those out be mounted using 
```
/dev/disk/by-id/[COLOR="#008000"]wwn-0x500a07511faa44ad-part1[/COLOR]  /mount/point  ext4  defaults 0 2

```
See the relationship?

There are some types of advanced storage things that I didn't cover, like LVM.  LVM = Logical Volume Manager.  What that is, is well beyond what you need here.


One last thing.  There are 6 fields in the fstab file.  The last field is how fsck should be parallelized.  1 should be used for the OS file systems.  2 should be used for data partitions. 0 should only be used for non-native file systems or network storage.  The fstab manpage has more, but it isn't very complicated.  So, for NTFS use a 0.  This running of fsck, say monthly, during boot is important to catch issues before they become huge.

---

### Post by Windowsxpnomore on 2022-05-04
Many thanks.
This server was built in 2013 with 12.04 upgraded to 14.04 and then in a matter of days to 16.04 where it is today. All the disks have been replaced since then (having failed) the longest disk is from Aug/2015. This shows only 33 power cycles on smart data. It worked every boot, until it failed consistently (on boot) with the change to AHCI, for upgrade of system disk (that is the oldest disk) to SSD and yes, it will move to 18.04 and then 20.04.

many thanks for you UUID explanation.

---

### Post by TheFu on 2022-05-04
Things work, until they don't.  That's sorta how stuff works, right?  For a HDD, startup is the most dangerous part of their lifetimes.

AHCI has been the standard for about a decade. It is a little odd hearing about any issues in 2022 related to something the rest of the world removed from in 2012 or earlier.  

Do you have IDE HDDs still too?
I have some IDE HDDs, but they don't connect to computers without using a USB converter cable or enclosure.  For a while, I was buying 300G - 320G Seagate Barracuda HDDs. None of them have failed.  1 is in a system, spinning, right now as scratch storage. SMART reports what appears to be a cable problem. The other 5+ HDDs are in old devices like a TiVo or mediagate video playback box - neither have been used in years.  When video went hidef, the mediagate just couldn't handle that.

---

### Post by slickymaster on 2022-05-04
*Thread moved to **Server Platforms**.*

---


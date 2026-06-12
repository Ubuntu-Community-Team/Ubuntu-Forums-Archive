---
title: "udev+mdadm incremental assembly feeling a little nondeterministic"
date: 2010-12-01
forum: Server Platforms
---

### Post by dtfinch on 2010-12-01
This is low priority since it only happens on random boots on a system I don't expect to reboot much and there are obvious workarounds but this mystery has been bothering me today.

I rebooted a server after adding a second raid 1, and it neglected to add the last drive, even though it worked fine on a second identical server, and on subsequent reboots. It's like maybe it just skipped a udev add event, or tried adding it but but failed without logging an error.

Relevant portions of dmesg log:```
[   21.284775] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   21.286483] sd 4:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   21.302105] sd 4:0:1:0: Attached scsi generic sg4 type 0
[   21.303742] sd 4:0:1:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   21.306818] sd 4:0:2:0: Attached scsi generic sg5 type 0
[   21.308522] sd 4:0:2:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   21.311941] sd 4:0:3:0: Attached scsi generic sg6 type 0
[   21.313472] sd 4:0:3:0: [sdf] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   21.314173] sd 4:0:0:0: [sdc] Write Protect is off
[   21.314177] sd 4:0:0:0: [sdc] Mode Sense: 73 00 00 08
[   21.316926] sd 4:0:2:0: [sde] Write Protect is off
[   21.316930] sd 4:0:2:0: [sde] Mode Sense: 73 00 00 08
[   21.318300] sd 4:0:2:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.319086] sd 4:0:3:0: [sdf] Write Protect is off
[   21.319089] sd 4:0:3:0: [sdf] Mode Sense: 73 00 00 08
[   21.320542] sd 4:0:3:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.325836]  sde:
[   21.327716] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.328978]  sdf:
[   21.331076] sd 4:0:1:0: [sdd] Write Protect is off
[   21.331080] sd 4:0:1:0: [sdd] Mode Sense: 73 00 00 08
[   21.344287] sd 4:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.368294]  sdc:
[   21.384910]  sdd: sdc1
[   21.406347]  sdd1
[   21.447552] sd 4:0:0:0: [sdc] Attached SCSI disk
[   21.494204] sd 4:0:1:0: [sdd] Attached SCSI disk
[   21.782320]  sde1
[   21.793745]  sdf1
[   21.796229] sd 4:0:2:0: [sde] Attached SCSI disk
[   21.807902] sd 4:0:3:0: [sdf] Attached SCSI disk
[   21.894913] md: bind<sdc1>
[   21.920562] md: bind<sdd1>
[   21.922764] raid1: raid set md0 active with 2 out of 2 mirrors
[   21.922791] md0: detected capacity change from 0 to 999996522496
[   21.925970]  md0: unknown partition table
[   22.055945] md: bind<sde1>
```Booting halted at this point (waiting to mount). There should have been a "md: bind<sdf1>", but it never happened.

I then skipped mounting and did a manual "mdadm --assemble /dev/md1 --scan", and it came up correctly.```
[ 1057.449591] md: md1 stopped.
[ 1057.449604] md: unbind<sde1>
[ 1057.472635] md: export_rdev(sde1)
[ 1058.081966] md: bind<sdf1>
[ 1058.082163] md: bind<sde1>
[ 1058.083402] raid1: md1 is not clean -- starting background reconstruction
[ 1058.083406] raid1: raid set md1 active with 2 out of 2 mirrors
[ 1058.083431] md1: detected capacity change from 0 to 999996522496
[ 1058.085481] md: resync of RAID array md1
[ 1058.085484] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[ 1058.085487] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[ 1058.085494] md: using 128k window, over a total of 976559104 blocks.
[ 1058.085496] md: resuming resync of md1 from checkpoint.
[ 1060.058175]  md1: unknown partition table
```
My /etc/mdadm/mdadm.conf:```
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=c29818b0:ca4a3739:00db787c:2b137912
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=00.90 UUID=460b2781:0b69cd5e:0199cfb5:b3121f14
```output of blkid:```
/dev/sdb1: UUID="74269bf4-d2bb-45eb-bb3d-c39ced9f84ff" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda1: LABEL="bootsd" UUID="dbcb1f09-859c-4944-b77d-c798359e5271" TYPE="ext4"
/dev/sde1: UUID="460b2781-0b69-cd5e-0199-cfb5b3121f14" TYPE="linux_raid_member"
/dev/sdf1: UUID="460b2781-0b69-cd5e-0199-cfb5b3121f14" TYPE="linux_raid_member"
/dev/sdc1: UUID="c29818b0-ca4a-3739-00db-787c2b137912" TYPE="linux_raid_member"
/dev/sdd1: UUID="c29818b0-ca4a-3739-00db-787c2b137912" TYPE="linux_raid_member"
/dev/md0: UUID="RdxsjK-TedI-TSVk-XB51-ji7f-X3rL-f8w7E0" TYPE="LVM2_member"
/dev/md1: UUID="N4UGfv-hbqf-zuqb-1rea-qgkO-v18b-v91c6P" TYPE="LVM2_member"
/dev/mapper/vg0-store: UUID="167f2e6e-eba3-4709-8080-a15c6890807f" TYPE="ext4"
```
/lib/udev/rules.d/85-mdadm.rules is unchanged from the default (SUBSYSTEM=="block", ACTION=="add|change", ENV{ID_FS_TYPE}=="linux_raid*", RUN+="/sbin/mdadm --incremental $env{DEVNAME}").

On the next reboot it came up just fine, with the only significant difference in the dmesg log being that it added sdf1 and activated md1.```
...
[   22.398787] md: bind<sdf1>
[   22.401585] raid1: raid set md1 active with 2 out of 2 mirrors
[   22.401610] md1: detected capacity change from 0 to 999996522496
[   22.403001]  md1: unknown partition table
```

Other probably non-relevant details:
It's a Dell PowerEdge R710 rackmount server.
The system boots off an sd card (gives me nightmares), with /var/log, /tmp and such on tmpfs to minimize writes.
The 4 sata raid drives are connected to an LSI SAS 1068E controller. They are configured as two raid 1's, concatenated using LVM. For some odd reason (another mystery for another time), they are consistently not detected until almost exactly 21 seconds into boot, like there's a 20 second timeout somewhere.

---


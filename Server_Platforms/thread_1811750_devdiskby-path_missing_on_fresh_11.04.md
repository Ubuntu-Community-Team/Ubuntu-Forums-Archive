---
title: "/dev/disk/by-path missing on fresh 11.04"
date: 2011-07-25
forum: Server Platforms
---

### Post by UloPe on 2011-07-25
Hi,

On a freshly installed Ubuntu server 11.04 I noticed that the /dev/disk/by-path directory (and of course it's contents) are missing:

```
root@xfiles2:~# ls -lA /dev/disk/
total 0
drwxr-xr-x 2 root root 1040 2011-07-25 16:06 by-id
drwxr-xr-x 2 root root   60 2011-07-25 16:06 by-uuid

```

Here is a sample output of udevadm test:
```
root@xfiles2:~# udevadm test $(udevadm info -q path -n /dev/sde)
run_command: calling: test
udevadm_test: version 167
parse_file: reading '/lib/udev/rules.d/40-fuse-utils.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/42-qemu-usb.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/55-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-floppy.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-zpool.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-zvol.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-mobile-action.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/65-mdadm-blkid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-acl.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-hid2hci.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-net-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-probe_mtd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-tty-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-graphics-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-sound-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-drivers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-keyboard-configuration.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-mdadm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-regulatory.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keyboard-force-release.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keymap.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/dev/.udev/rules.d/root.rules' as rules file
udev_rules_new: rules use 23868 bytes tokens (1989 * 12 bytes), 16286 bytes buffer
udev_rules_new: temporary index used 16000 bytes (800 * 20 bytes)
udev_device_new_from_syspath: device 0x7f5a13ae9180 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde'
udev_device_new_from_syspath: device 0x7f5a13af4ff0 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde'
udev_device_read_db: device 0x7f5a13af4ff0 filled with db file data
udev_rules_apply_to_event: GROUP 6 /lib/udev/rules.d/50-udev-default.rules:68
udev_device_new_from_syspath: device 0x7f5a13af5370 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0'
udev_device_new_from_syspath: device 0x7f5a13af5da0 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4'
udev_device_new_from_syspath: device 0x7f5a13af6140 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4'
udev_device_new_from_syspath: device 0x7f5a13af6430 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4'
udev_device_new_from_syspath: device 0x7f5a13af6700 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0'
udev_device_new_from_syspath: device 0x7f5a13af6a50 has devpath '/devices/pci0000:00/0000:00:04.0/0000:02:00.0'
udev_device_new_from_syspath: device 0x7f5a13af6da0 has devpath '/devices/pci0000:00/0000:00:04.0'
udev_device_new_from_syspath: device 0x7f5a13af70d0 has devpath '/devices/pci0000:00'
udev_rules_apply_to_event: IMPORT 'ata_id --export /dev/sde' /lib/udev/rules.d/60-persistent-storage.rules:30
util_run_program: 'ata_id --export /dev/sde' started
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_TYPE=disk'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_BUS=ata'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_MODEL=Hitachi_HDS5C3020ALA632'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_MODEL_ENC=Hitachi\x20HDS5C3020ALA632\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_REVISION=ML6OA508'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_SERIAL=Hitachi_HDS5C3020ALA632_ML0220F30U311D'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_SERIAL_SHORT=ML0220F30U311D'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_WRITE_CACHE=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_WRITE_CACHE_ENABLED=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_HPA=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_HPA_ENABLED=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_PM=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_PM_ENABLED=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_SECURITY=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_SECURITY_ENABLED=0'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=504'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_SMART=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_SMART_ENABLED=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_PUIS=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_PUIS_ENABLED=0'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_APM=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_FEATURE_SET_APM_ENABLED=0'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_DOWNLOAD_MICROCODE=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_SATA=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_SATA_SIGNAL_RATE_GEN2=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_SATA_SIGNAL_RATE_GEN1=1'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_ATA_ROTATION_RATE_RPM=5940'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_WWN=0x5000cca369cb68aa'
util_run_program: '/lib/udev/ata_id' (stdout) 'ID_WWN_WITH_EXTENSION=0x5000cca369cb68aa'
util_run_program: 'ata_id --export /dev/sde' returned with exitcode 0
udev_rules_apply_to_event: LINK 'disk/by-id/ata-Hitachi_HDS5C3020ALA632_ML0220F30U311D' /lib/udev/rules.d/60-persistent-storage.rules:36
udev_rules_apply_to_event: PROGRAM 'scsi_id --whitelisted --replace-whitespace -p0x80 -d/dev/sde' /lib/udev/rules.d/60-persistent-storage.rules:44
util_run_program: 'scsi_id --whitelisted --replace-whitespace -p0x80 -d/dev/sde' started
util_run_program: '/lib/udev/scsi_id' (stdout) 'SATA_Hitachi_HDS5C30_ML0220F30U311D'
util_run_program: 'scsi_id --whitelisted --replace-whitespace -p0x80 -d/dev/sde' returned with exitcode 0
udev_rules_apply_to_event: LINK 'disk/by-id/scsi-SATA_Hitachi_HDS5C30_ML0220F30U311D' /lib/udev/rules.d/60-persistent-storage.rules:44
udev_rules_apply_to_event: IMPORT 'path_id /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde' /lib/udev/rules.d/60-persistent-storage.rules:53
util_run_program: 'path_id /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde' started
util_run_program: 'path_id /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde' returned with exitcode 1
udev_rules_apply_to_event: IMPORT '/sbin/blkid -o udev -p /dev/sde' /lib/udev/rules.d/60-persistent-storage.rules:66
util_run_program: '/sbin/blkid -o udev -p /dev/sde' started
util_run_program: '/sbin/blkid' (stdout) 'ID_PART_TABLE_TYPE=gpt'
util_run_program: '/sbin/blkid -o udev -p /dev/sde' returned with exitcode 0
udev_rules_apply_to_event: LINK 'disk/by-id/wwn-0x5000cca369cb68aa' /lib/udev/rules.d/60-persistent-storage.rules:76
udev_rules_apply_to_event: IMPORT '/usr/bin/zpool_id -d /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde' /etc/udev/rules.d/60-zpool.rules:5
util_run_program: '/usr/bin/zpool_id -d /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde' started
util_run_program: '/usr/bin/zpool_id' (stdout) 'Error: Missing ID_PATH for /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde'
util_run_program: '/usr/bin/zpool_id -d /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde' returned with exitcode 1
udev_rules_apply_to_event: IMPORT 'edd_id --export /dev/sde' /lib/udev/rules.d/61-persistent-storage-edd.rules:8
util_run_program: 'edd_id --export /dev/sde' started
util_run_program: '/lib/udev/edd_id' (stderr) 'no kernel EDD support'
util_run_program: 'edd_id --export /dev/sde' returned with exitcode 2
udev_rules_apply_to_event: RUN '/lib/udev/hdparm' /lib/udev/rules.d/85-hdparm.rules:2
udev_event_execute_rules: no node name set, will use kernel supplied name 'sde'
udev_node_add: creating device node '/dev/sde', devnum=8:64, mode=0660, uid=0, gid=6
udev_node_mknod: preserve file '/dev/sde', because it has correct dev_t
udev_node_mknod: preserve permissions /dev/sde, 060660, uid=0, gid=6
node_symlink: preserve already existing symlink '/dev/block/8:64' to '../sde'
link_find_prioritized: found 'b8:64' claiming '/dev/.udev/links/disk\x2fby-id\x2fata-Hitachi_HDS5C3020ALA632_ML0220F30U311D'
link_update: creating link '/dev/disk/by-id/ata-Hitachi_HDS5C3020ALA632_ML0220F30U311D' to '/dev/sde'
node_symlink: preserve already existing symlink '/dev/disk/by-id/ata-Hitachi_HDS5C3020ALA632_ML0220F30U311D' to '../../sde'
link_find_prioritized: found 'b8:64' claiming '/dev/.udev/links/disk\x2fby-id\x2fscsi-SATA_Hitachi_HDS5C30_ML0220F30U311D'
link_update: creating link '/dev/disk/by-id/scsi-SATA_Hitachi_HDS5C30_ML0220F30U311D' to '/dev/sde'
node_symlink: preserve already existing symlink '/dev/disk/by-id/scsi-SATA_Hitachi_HDS5C30_ML0220F30U311D' to '../../sde'
link_find_prioritized: found 'b8:64' claiming '/dev/.udev/links/disk\x2fby-id\x2fwwn-0x5000cca369cb68aa'
link_update: creating link '/dev/disk/by-id/wwn-0x5000cca369cb68aa' to '/dev/sde'
node_symlink: preserve already existing symlink '/dev/disk/by-id/wwn-0x5000cca369cb68aa' to '../../sde'
udev_device_update_db: created db file '/dev/.udev/data/b8:64' for '/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde'
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde
udevadm_test: MAJOR=8
udevadm_test: MINOR=64
udevadm_test: DEVNAME=/dev/sde
udevadm_test: DEVTYPE=disk
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=block
udevadm_test: ID_ATA=1
udevadm_test: ID_TYPE=disk
udevadm_test: ID_BUS=ata
udevadm_test: ID_MODEL=Hitachi_HDS5C3020ALA632
udevadm_test: ID_MODEL_ENC=Hitachi\x20HDS5C3020ALA632\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
udevadm_test: ID_REVISION=ML6OA508
udevadm_test: ID_SERIAL=Hitachi_HDS5C3020ALA632_ML0220F30U311D
udevadm_test: ID_SERIAL_SHORT=ML0220F30U311D
udevadm_test: ID_ATA_WRITE_CACHE=1
udevadm_test: ID_ATA_WRITE_CACHE_ENABLED=1
udevadm_test: ID_ATA_FEATURE_SET_HPA=1
udevadm_test: ID_ATA_FEATURE_SET_HPA_ENABLED=1
udevadm_test: ID_ATA_FEATURE_SET_PM=1
udevadm_test: ID_ATA_FEATURE_SET_PM_ENABLED=1
udevadm_test: ID_ATA_FEATURE_SET_SECURITY=1
udevadm_test: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
udevadm_test: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=504
udevadm_test: ID_ATA_FEATURE_SET_SMART=1
udevadm_test: ID_ATA_FEATURE_SET_SMART_ENABLED=1
udevadm_test: ID_ATA_FEATURE_SET_PUIS=1
udevadm_test: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
udevadm_test: ID_ATA_FEATURE_SET_APM=1
udevadm_test: ID_ATA_FEATURE_SET_APM_ENABLED=0
udevadm_test: ID_ATA_DOWNLOAD_MICROCODE=1
udevadm_test: ID_ATA_SATA=1
udevadm_test: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
udevadm_test: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
udevadm_test: ID_ATA_ROTATION_RATE_RPM=5940
udevadm_test: ID_WWN=0x5000cca369cb68aa
udevadm_test: ID_WWN_WITH_EXTENSION=0x5000cca369cb68aa
udevadm_test: DEVLINKS=/dev/disk/by-id/ata-Hitachi_HDS5C3020ALA632_ML0220F30U311D /dev/disk/by-id/scsi-SATA_Hitachi_HDS5C30_ML0220F30U311D /dev/disk/by-id/wwn-0x5000cca369cb68aa
udevadm_test: ID_SCSI_COMPAT=SATA_Hitachi_HDS5C30_ML0220F30U311D
udevadm_test: ID_PART_TABLE_TYPE=gpt
udevadm_test: run: '/lib/udev/hdparm'
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

```

Without having a deeper understanding of udev this line seems suspicious: 
```
util_run_program: 'path_id /devices/pci0000:00/0000:00:04.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde' returned with exitcode 1
```


So - what can I do to make udev create the by-path links?

Thanks,
Ulrich

---

### Post by UloPe on 2011-07-25
Ok so after digging through the udev sources and reading the linux-hotplug mailing list it appears path_id simply can't handle sas / sata devices yet. 

Great...

---


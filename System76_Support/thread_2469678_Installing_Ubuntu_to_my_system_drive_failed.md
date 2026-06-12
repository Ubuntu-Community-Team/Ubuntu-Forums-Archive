---
title: "Installing Ubuntu to my system drive failed"
date: 2021-12-06
forum: System76 Support
---

### Post by supermonkey12345123 on 2021-12-06
Hi, first time Linux user here,

I'm trying to install Pop OS on my Surface book 3. I have everything setup, and I'm currently typing this post in Demo mode. I tried to install pop os onto my drive, but I kept on getting an installation failed message. I have 21.04 as my Pop OS version, and my original OS was the latest Windows 11. I'm not sure how to attach a file onto a post, since it shows up as a white square, so I'll just paste it into the post itself I guess.


installer.log:

```
[INFO distinst:crates/disks/src/config/disks.rs:579] probed "/dev/sda"
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/sda
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/sda
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/sda
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/sda2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/sda3
[INFO distinst:crates/disks/src/config/disks.rs:579] probed "/dev/nvme0n1"
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/nvme0n1
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p3
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p4
[INFO distinst:crates/external/src/lvm.rs:209] obtaining list of physical volumes
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/sda"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[INFO distinst:crates/disks/src/config/disk_trait.rs:60] child_dev "/dev/sda1" has mount_opt Some(MountInfo { source: "/dev/sda1", dest: "/cdrom", fstype: "iso9660", options: ["ro", "noatime", "nojoliet", "check=s", "map=n", "blocksize=2048"], dump: 0, pass: 0 })
[INFO distinst:crates/disks/src/config/disk_trait.rs:60] child_dev "/dev/sda2" has mount_opt None
[INFO distinst:crates/disks/src/config/disk_trait.rs:60] child_dev "/dev/sda3" has mount_opt Some(MountInfo { source: "/dev/sda3", dest: "/var/log", fstype: "ext4", options: ["rw", "relatime"], dump: 0, pass: 0 })
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/sda2"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/sda3"
[INFO distinst:crates/os-detect/src/lib.rs:52] detecting OS from device: "/dev/sda3"
[INFO distinst:crates/os-detect/src/lib.rs:68] detecting OS from "/tmp/distinst.xCNLIsFXiNYG"
[INFO distinst:crates/os-detect/src/lib.rs:71] Found "/tmp/distinst.xCNLIsFXiNYG/install-logs-2021-12-06.0"
[INFO distinst:crates/os-detect/src/lib.rs:71] Found "/tmp/distinst.xCNLIsFXiNYG/install-logs-2021-12-06.1"
[INFO distinst:crates/os-detect/src/lib.rs:71] Found "/tmp/distinst.xCNLIsFXiNYG/lost+found"
[INFO distinst:src/auto/options/mod.rs:107] found shrinkable partition on "/dev/sda3": 3837535574 free of 3901020334
[INFO distinst:crates/disks/src/config/disk_trait.rs:60] child_dev "/dev/sda1" has mount_opt Some(MountInfo { source: "/dev/sda1", dest: "/cdrom", fstype: "iso9660", options: ["ro", "noatime", "nojoliet", "check=s", "map=n", "blocksize=2048"], dump: 0, pass: 0 })
[INFO distinst:crates/disks/src/config/disk_trait.rs:60] child_dev "/dev/sda2" has mount_opt None
[INFO distinst:crates/disks/src/config/disk_trait.rs:60] child_dev "/dev/sda3" has mount_opt Some(MountInfo { source: "/dev/sda3", dest: "/var/log", fstype: "ext4", options: ["rw", "relatime"], dump: 0, pass: 0 })
[INFO distinst:crates/disks/src/config/disk_trait.rs:60] child_dev "/dev/sda1" has mount_opt Some(MountInfo { source: "/dev/sda1", dest: "/cdrom", fstype: "iso9660", options: ["ro", "noatime", "nojoliet", "check=s", "map=n", "blocksize=2048"], dump: 0, pass: 0 })
[INFO distinst:src/auto/options/mod.rs:171] install options: skipping options on "/dev/sda"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1p1"
[INFO distinst:crates/os-detect/src/lib.rs:52] detecting OS from device: "/dev/nvme0n1p1"
[INFO distinst:crates/os-detect/src/lib.rs:68] detecting OS from "/tmp/distinst.LuFlRkzoCxtV"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1p2"
[INFO distinst:crates/os-detect/src/lib.rs:52] detecting OS from device: "/dev/nvme0n1p2"
[INFO distinst:crates/os-detect/src/lib.rs:68] detecting OS from "/tmp/distinst.ACfaSfBqtb9x"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1p3"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1p4"
[INFO distinst:src/auto/options/mod.rs:176] found erase option on "/dev/nvme0n1": 500118192 sectors
[INFO distinst:crates/disks/src/config/disks.rs:579] probed "/dev/sda"
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/sda
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/sda
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/sda
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/sda2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/sda3
[INFO distinst:crates/disks/src/config/disks.rs:579] probed "/dev/nvme0n1"
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/nvme0n1
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p3
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p4
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/sda"
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/nvme0n1
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p3
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p4
[INFO distinst:crates/disks/src/config/disk.rs:348] specifying to write new table on /dev/nvme0n1
[INFO distinst:crates/disks/src/config/disk.rs:278] unmount all partitions on /dev/nvme0n1
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[INFO distinst:crates/disks/src/config/disk_trait.rs:118] checking if 4096:1023999 overlaps
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[INFO distinst:crates/disks/src/config/disk_trait.rs:118] checking if 1024000:9412607 overlaps
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[INFO distinst:crates/disks/src/config/disk_trait.rs:118] checking if 9412608:491725487 overlaps
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[INFO distinst:crates/disks/src/config/disk_trait.rs:118] checking if 491725488:500114095 overlaps
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/nvme0n1"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/data"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/data"
[DEBUG distinst:crates/disk-types/src/sector.rs:17] get block size for "/sys/class/block/data"
[ERROR distinst:ffi/src/lib.rs:49] libdistinst: pointer in FFI is null
[ERROR distinst:ffi/src/lib.rs:49] libdistinst: pointer in FFI is null
[ERROR distinst:ffi/src/lib.rs:49] libdistinst: pointer in FFI is null
[INFO distinst:src/installer/state.rs:33] starting initializing step
[INFO distinst:src/installer/steps/initialize.rs:15] Initializing
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:src/installer/steps/initialize.rs:20] config.squashfs: found at /cdrom/casper_pop-os_21.04_amd64_nvidia_debug_25/filesystem.squashfs
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/nvme0n1
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/nvme0n1
[INFO distinst:crates/disks/src/config/disks.rs:808] verifying if keyfiles have paths
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p3
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p4
[INFO distinst:crates/disks/src/config/disks.rs:397] devices to modify: ["/dev/nvme0n1p1", "/dev/nvme0n1p2", "/dev/nvme0n1p3", "/dev/nvme0n1p4"]
[INFO distinst:crates/external/src/lvm.rs:209] obtaining list of physical volumes
[INFO distinst:crates/disks/src/config/disks.rs:399] volume map: {}
[INFO distinst:crates/external/src/lvm.rs:51] searching for device maps to deactivate
[INFO distinst:crates/disks/src/config/disks.rs:401] pvs: []
[INFO distinst:crates/disks/src/config/disks.rs:550] unmounting devices
[INFO distinst:crates/disks/src/config/disk.rs:305] unmount all partitions with a target on /dev/nvme0n1
[INFO distinst:src/installer/state.rs:33] starting partitioning step
[INFO distinst:crates/external/src/lvm.rs:209] obtaining list of physical volumes
[INFO distinst:src/installer/steps/partition.rs:25] /dev/nvme0n1: Committing changes to disk
[INFO distinst:crates/disks/src/config/disk.rs:786] committing changes to /dev/nvme0n1: Disk {
    model_name: "KBG40ZNS256G TOSHIBA MEMORY",
    serial: "KBG40ZNS256G TOSHIBA MEMORY_Z0FPH648Q6LL",
    device_path: "/dev/nvme0n1",
    file_system: None,
    mount_point: None,
    size: 500118192,
    device_type: "PED_DEVICE_NVME",
    table_type: Some(
        Gpt,
    ),
    read_only: false,
    mklabel: true,
    partitions: [
        PartitionInfo {
            bitflags: 4,
            number: -1,
            ordering: -1,
            start_sector: 4096,
            end_sector: 1023999,
            part_type: Primary,
            filesystem: Some(
                Fat32,
            ),
            flags: [
                PED_PARTITION_ESP,
            ],
            name: None,
            device_path: "",
            mount_point: None,
            target: Some(
                "/boot/efi",
            ),
            original_vg: None,
            volume_group: None,
            key_id: None,
            identifiers: PartitionIdentifiers {
                id: None,
                label: None,
                part_label: None,
                part_uuid: None,
                path: None,
                uuid: None,
            },
        },
        PartitionInfo {
            bitflags: 4,
            number: -1,
            ordering: -1,
            start_sector: 1024000,
            end_sector: 9412607,
            part_type: Primary,
            filesystem: Some(
                Fat32,
            ),
            flags: [],
            name: Some(
                "recovery",
            ),
            device_path: "",
            mount_point: None,
            target: Some(
                "/recovery",
            ),
            original_vg: None,
            volume_group: None,
            key_id: None,
            identifiers: PartitionIdentifiers {
                id: None,
                label: None,
                part_label: None,
                part_uuid: None,
                path: None,
                uuid: None,
            },
        },
        PartitionInfo {
            bitflags: 4,
            number: -1,
            ordering: -1,
            start_sector: 9412608,
            end_sector: 491725487,
            part_type: Primary,
            filesystem: Some(
                Luks,
            ),
            flags: [],
            name: None,
            device_path: "",
            mount_point: None,
            target: None,
            original_vg: None,
            volume_group: Some(
                (
                    "data",
                    Some(
                        LvmEncryption { physical_volume: cryptdata, password: hidden, keydata: None },
                    ),
                ),
            ),
            key_id: None,
            identifiers: PartitionIdentifiers {
                id: None,
                label: None,
                part_label: None,
                part_uuid: None,
                path: None,
                uuid: None,
            },
        },
        PartitionInfo {
            bitflags: 4,
            number: -1,
            ordering: -1,
            start_sector: 491725488,
            end_sector: 500114095,
            part_type: Primary,
            filesystem: Some(
                Swap,
            ),
            flags: [],
            name: None,
            device_path: "",
            mount_point: None,
            target: None,
            original_vg: None,
            volume_group: None,
            key_id: None,
            identifiers: PartitionIdentifiers {
                id: None,
                label: None,
                part_label: None,
                part_uuid: None,
                path: None,
                uuid: None,
            },
        },
    ],
}
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/nvme0n1
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p3
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p4
[INFO distinst:crates/disks/src/config/disk.rs:613] generating diff of disk at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/disk.rs:669] proposed layout:
    -1: 4096 - 1023999
    -1: 1024000 - 9412607
    -1: 9412608 - 491725487
    -1: 491725488 - 500114095
[INFO distinst:crates/disk-ops/src/ops.rs:50] /dev/nvme0n1: executing remove operations
[INFO distinst:crates/external/src/block.rs:14] using wipefs to wipe signatures from "/dev/nvme0n1"
[INFO distinst:crates/external/src/lib.rs:34] executing wipefs with ["-a", "/dev/nvme0n1"]
[INFO distinst:crates/disk-ops/src/mklabel.rs:16] writing Gpt table on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:20] opening device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:62] committing changes to /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:78] syncing device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:20] opening device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:78] syncing device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/ops.rs:94] /dev/nvme0n1: executing change operations
[INFO distinst:crates/disk-ops/src/parted.rs:20] opening device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:78] syncing device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/ops.rs:218] /dev/nvme0n1: executing creation operations
[INFO distinst:crates/disk-ops/src/ops.rs:221] creating partition (PartitionCreate { path: "/dev/nvme0n1", start_sector: 4096, end_sector: 1023999, format: true, file_system: Some(Fat32), kind: Primary, flags: [PED_PARTITION_ESP], label: None }) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:20] opening device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:81] creating new partition with 1019903 sectors: 4096 - 1023999
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:124] committing new partition (4096:1023999) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:62] committing changes to /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:78] syncing device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/ops.rs:221] creating partition (PartitionCreate { path: "/dev/nvme0n1", start_sector: 1024000, end_sector: 9412607, format: true, file_system: Some(Fat32), kind: Primary, flags: [], label: Some("recovery") }) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:20] opening device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:81] creating new partition with 8388607 sectors: 1024000 - 9412607
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:124] committing new partition (1024000:9412607) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:62] committing changes to /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:78] syncing device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/ops.rs:221] creating partition (PartitionCreate { path: "/dev/nvme0n1", start_sector: 9412608, end_sector: 491725487, format: true, file_system: Some(Luks), kind: Primary, flags: [], label: None }) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:20] opening device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:81] creating new partition with 482312879 sectors: 9412608 - 491725487
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:124] committing new partition (9412608:491725487) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:62] committing changes to /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:78] syncing device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/ops.rs:221] creating partition (PartitionCreate { path: "/dev/nvme0n1", start_sector: 491725488, end_sector: 500114095, format: true, file_system: Some(Swap), kind: Primary, flags: [], label: None }) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:20] opening device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:81] creating new partition with 8388607 sectors: 491725488 - 500114095
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/mkpart.rs:124] committing new partition (491725488:500114095) on /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:62] committing changes to /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:78] syncing device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/external/src/lib.rs:34] executing blockdev with ["--flushbufs", "--rereadpt", "/dev/nvme0n1"]
[INFO distinst:crates/disk-ops/src/ops.rs:292] executing format operations
[INFO distinst:crates/disk-ops/src/ops.rs:296] formatting /dev/nvme0n1p3 with Luks
[INFO distinst:crates/disk-ops/src/ops.rs:296] formatting /dev/nvme0n1p4 with Swap
[INFO distinst:crates/disk-ops/src/ops.rs:296] formatting /dev/nvme0n1p1 with Fat32
[INFO distinst:crates/disk-ops/src/ops.rs:296] formatting /dev/nvme0n1p2 with Fat32
[INFO distinst:crates/external/src/lib.rs:34] executing mkfs.fat with ["-F", "32", "/dev/nvme0n1p2"]
[INFO distinst:crates/external/src/lib.rs:34] executing mkfs.fat with ["-F", "32", "/dev/nvme0n1p1"]
[INFO distinst:crates/disks/src/config/disk.rs:807] reloading disk information for /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:8] getting device at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/disk.rs:164] obtaining disk information from /dev/nvme0n1
[INFO distinst:crates/disks/src/serial.rs:14] obtaining serial model from /dev/nvme0n1
[INFO distinst:crates/disk-ops/src/parted.rs:31] opening disk at /dev/nvme0n1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p1
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p2
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p3
[INFO distinst:crates/disks/src/config/partitions/mod.rs:118] obtaining partition information from /dev/nvme0n1p4
[INFO distinst:crates/disks/src/config/disk.rs:831] checking for mount target at 4096
[INFO distinst:crates/disks/src/config/disk.rs:831] checking for mount target at 1024000
[INFO distinst:crates/disks/src/config/disk.rs:831] checking for mount target at 9412608
[INFO distinst:crates/external/src/lib.rs:34] executing blockdev with ["--flushbufs", "--rereadpt", "/dev/nvme0n1"]
[INFO distinst:crates/external/src/lvm.rs:209] obtaining list of physical volumes
[INFO distinst:crates/external/src/lvm.rs:51] searching for device maps to deactivate
[INFO distinst:crates/disks/src/external.rs:66] cryptsetup is encrypting /dev/nvme0n1p3 with LvmEncryption { physical_volume: cryptdata, password: hidden, keydata: None }
[INFO distinst:crates/external/src/lib.rs:34] executing cryptsetup with ["-s", "512", "luksFormat", "--type", "luks2", "/dev/nvme0n1p3"]
[INFO distinst:crates/external/src/lvm.rs:51] searching for device maps to deactivate
[INFO distinst:crates/disks/src/external.rs:117] cryptsetup is opening /dev/nvme0n1p3 with pv cryptdata and LvmEncryption { physical_volume: cryptdata, password: hidden, keydata: None }
[INFO distinst:crates/external/src/lib.rs:34] executing cryptsetup with ["open", "/dev/nvme0n1p3", "cryptdata"]
[INFO distinst:crates/external/src/lib.rs:34] executing pvcreate with ["-ffy", "/dev/mapper/cryptdata"]
[INFO distinst:crates/external/src/lib.rs:34] executing vgcreate with ["-ffy", "data", "/dev/mapper/cryptdata"]
[INFO distinst:crates/external/src/lib.rs:34] executing lvcreate with ["-y", "-l", "100%FREE", "data", "-n", "root"]
[INFO distinst:crates/external/src/lib.rs:34] executing mkfs.ext4 with ["-F", "-q", "-E", "lazy_itable_init", "/dev/mapper/data-root"]
[INFO distinst:crates/disks/src/config/disks.rs:1171] associating "/dev/mapper/data" with "/dev/nvme0n1p3"
[INFO distinst:src/installer/mod.rs:170] mounting temporary chroot directory at distinst
[INFO distinst:src/installer/mod.rs:175] mounting all targets to the temporary chroot
[INFO distinst:crates/disks/src/config/disks.rs:243] mounting "/dev/mapper/data-root" (ext4) to "/tmp/distinst.TZuVa48CLXE0/"
[INFO distinst:crates/disks/src/config/disks.rs:243] mounting "/dev/nvme0n1p1" (vfat) to "/tmp/distinst.TZuVa48CLXE0/boot/efi"
[INFO distinst:crates/disks/src/config/disks.rs:243] mounting "/dev/nvme0n1p2" (vfat) to "/tmp/distinst.TZuVa48CLXE0/recovery"
[INFO distinst:src/installer/state.rs:33] starting extracting step
[INFO distinst:src/installer/mod.rs:413] Extracting /cdrom/casper_pop-os_21.04_amd64_nvidia_debug_25/filesystem.squashfs
[DEBUG distinst:crates/squashfs/src/lib.rs:166] "unsquashfs" "-f" "-d" "/tmp/distinst.TZuVa48CLXE0" "/cdrom/casper_pop-os_21.04_amd64_nvidia_debug_25/filesystem.squashfs"
[ERROR distinst:src/installer/state.rs:37] extracting error: archive extraction failed with status: exit status: 1
[ERROR distinst:src/installer/mod.rs:300] errored while installing system: archive extraction failed with status: exit status: 1
[INFO distinst:ffi/src/installer.rs:188] Install error: archive extraction failed with status: exit status: 1
```

---

### Post by slickymaster on 2021-12-06
Thread moved to **System76 Support** for a better fit

---

### Post by supermonkey12345123 on 2021-12-06
Sorry, I didn't know that there were different places for support. Still a very new user of a forum :/

---

### Post by oldfred on 2021-12-06
Note familar with PopOS but your errors:

> [ERROR distinst:src/installer/state.rs:37] extracting error: archive extraction failed with status: exit status: 1
[ERROR distinst:src/installer/mod.rs:300] errored while installing system: archive extraction failed with status: exit status: 1

I would first check that ISO or install flash drive is correct, not sure if error is from extracting the install or writing the extracted data into RAM.

---

### Post by supermonkey12345123 on 2021-12-06
Hi, yes, I am installing it on my Samsung ssd.

---

### Post by oldfred on 2021-12-06
Have you updated UEFI and SSD firmware?

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

Samsung has an ISO for my model with newer firmware.

To see firmware version FW Rev.

sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

Or:
udisksctl status

---

### Post by supermonkey12345123 on 2021-12-06
Hi, I'm so sorry. It appears that I have a toshiba ssd. The Samsung one was the one on my PC and I remembered it wrong...

---


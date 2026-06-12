---
title: "Strange error with HA+LVM2+DRBD: VG creation refers to wrong device"
date: 2012-07-11
forum: Server Platforms
---

### Post by chakritw on 2012-07-11
Hello,

Currently I am working on a system with 2 servers and have to set up iSCSI target service over LVM volume over DRBD. These are basic configuration details:


Architecture: i386 32-bit
Disk: VM Disk over SATA RAID-1
OS: Ubuntu 12.04
DRBD version: 8.3.11
DRBD base file system: ext4
LVM2 version: 2.02.66
cLVM version: 2.02.66
Cluster infrastructure: pacemaker+heartbeat
Pacemaker version: 1.1.6
Heartbeat version: 1:3.0.5

I created DRBD disk, created crm resources to control master-slave DRBD activation between 2 servers, synced the data, and tried setting up PV, VG and LV over it from the Primary node. This is the result:

```

piing@piing-node-2:~$ sudo lvcreate -L 186G -n lun0 iscsivg01
[COLOR="Red"] device-mapper: reload ioctl failed: Invalid argument
  Aborting. Failed to activate new LV to wipe the start of it.
  Node /dev/mapper/iscsivg01-lun0 was not removed by udev. Falling back to direct node removal.[/COLOR]
  
piing@piing-node-2:~$ sudo lvcreate -vvvv -L 186G -n lun0 iscsivg01
#lvmcmdline.c:1035         Processing: lvcreate -vvvv -L 186G -n lun0 iscsivg01
#lvmcmdline.c:1038         O_DIRECT will be used
#config/config.c:987       Setting global/locking_type to 1
#config/config.c:987       Setting global/wait_for_locks to 1
#locking/locking.c:240       File-based locking selected.
#config/config.c:964       Setting global/locking_dir to /var/lock/lvm
#activate/activate.c:361       Getting target version for linear
#ioctl/libdm-iface.c:1821         dm version   OF   [16384]
#ioctl/libdm-iface.c:1821         dm versions   OF   [16384]
#activate/activate.c:361       Getting target version for striped
#ioctl/libdm-iface.c:1821         dm versions   OF   [16384]
#lvcreate.c:291     Setting logging type to disk
#config/config.c:987       Setting activation/mirror_region_size to 512
#lvcreate.c:526     Finding volume group "iscsivg01"
#locking/file_locking.c:235       Locking /var/lock/lvm/V_iscsivg01 WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/V_iscsivg01:aux WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/V_iscsivg01 WB
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/V_iscsivg01:aux
#device/dev-io.c:487         Opened /dev/ram0 RO O_DIRECT
#device/dev-io.c:134         /dev/ram0: block size is 4096 bytes
#label/label.c:184       /dev/ram0: No label detected
#device/dev-io.c:533         Closed /dev/ram0
#device/dev-io.c:487         Opened /dev/ram1 RO O_DIRECT
#device/dev-io.c:134         /dev/ram1: block size is 4096 bytes
#label/label.c:184       /dev/ram1: No label detected
#device/dev-io.c:533         Closed /dev/ram1
#device/dev-io.c:487         Opened /dev/sda1 RO O_DIRECT
#device/dev-io.c:134         /dev/sda1: block size is 4096 bytes
#label/label.c:184       /dev/sda1: No label detected
#device/dev-io.c:533         Closed /dev/sda1
#device/dev-io.c:487         Opened /dev/ram2 RO O_DIRECT
#device/dev-io.c:134         /dev/ram2: block size is 4096 bytes
#label/label.c:184       /dev/ram2: No label detected
#device/dev-io.c:533         Closed /dev/ram2
#device/dev-io.c:487         Opened /dev/ram3 RO O_DIRECT
#device/dev-io.c:134         /dev/ram3: block size is 4096 bytes
#label/label.c:184       /dev/ram3: No label detected
#device/dev-io.c:533         Closed /dev/ram3
#device/dev-io.c:487         Opened /dev/ram4 RO O_DIRECT
#device/dev-io.c:134         /dev/ram4: block size is 4096 bytes
#label/label.c:184       /dev/ram4: No label detected
#device/dev-io.c:533         Closed /dev/ram4
#device/dev-io.c:487         Opened /dev/ram5 RO O_DIRECT
#device/dev-io.c:134         /dev/ram5: block size is 4096 bytes
#label/label.c:184       /dev/ram5: No label detected
#device/dev-io.c:533         Closed /dev/ram5
#device/dev-io.c:487         Opened /dev/sda5 RO O_DIRECT
#device/dev-io.c:134         /dev/sda5: block size is 4096 bytes
#label/label.c:184       /dev/sda5: No label detected
#device/dev-io.c:533         Closed /dev/sda5
#device/dev-io.c:487         Opened /dev/ram6 RO O_DIRECT
#device/dev-io.c:134         /dev/ram6: block size is 4096 bytes
#label/label.c:184       /dev/ram6: No label detected
#device/dev-io.c:533         Closed /dev/ram6
#device/dev-io.c:487         Opened /dev/sda6 RO O_DIRECT
#device/dev-io.c:134         /dev/sda6: block size is 4096 bytes
#label/label.c:184       /dev/sda6: No label detected
#device/dev-io.c:533         Closed /dev/sda6
#device/dev-io.c:487         Opened /dev/ram7 RO O_DIRECT
#device/dev-io.c:134         /dev/ram7: block size is 4096 bytes
#label/label.c:184       /dev/ram7: No label detected
#device/dev-io.c:533         Closed /dev/ram7
#device/dev-io.c:487         Opened /dev/sda7 RO O_DIRECT
#device/dev-io.c:134         /dev/sda7: block size is 4096 bytes
#label/label.c:184       /dev/sda7: No label detected
#device/dev-io.c:533         Closed /dev/sda7
#device/dev-io.c:487         Opened /dev/ram8 RO O_DIRECT
#device/dev-io.c:134         /dev/ram8: block size is 4096 bytes
#label/label.c:184       /dev/ram8: No label detected
#device/dev-io.c:533         Closed /dev/ram8
#device/dev-io.c:487         Opened /dev/sda8 RO O_DIRECT
#device/dev-io.c:134         /dev/sda8: block size is 4096 bytes
[COLOR="Red"]#label/label.c:160       /dev/sda8: lvm2 label detected
#cache/lvmcache.c:1136         lvmcache: /dev/sda8: now in VG #orphans_lvm2 (#orphans_lvm2)
#format_text/format-text.c:1137         /dev/sda8: Found metadata at 6656 size 678 (in area at 4096 size 192512) for iscsivg01 (JuQJwx-pH4y-vuGj-uo82-viH0-B0DH-0Do7dx)
#cache/lvmcache.c:1136         lvmcache: /dev/sda8: now in VG iscsivg01 with 1 mdas[/COLOR]
#cache/lvmcache.c:923         lvmcache: /dev/sda8: setting iscsivg01 VGID to JuQJwxpH4yvuGjuo82viH0B0DH0Do7dx
#cache/lvmcache.c:1173         lvmcache: /dev/sda8: VG iscsivg01: Set creation host to piing-node-2.
#device/dev-io.c:487         Opened /dev/ram9 RO O_DIRECT
#device/dev-io.c:134         /dev/ram9: block size is 4096 bytes
#label/label.c:184       /dev/ram9: No label detected
#device/dev-io.c:533         Closed /dev/ram9
#device/dev-io.c:487         Opened /dev/ram10 RO O_DIRECT
#device/dev-io.c:134         /dev/ram10: block size is 4096 bytes
#label/label.c:184       /dev/ram10: No label detected
#device/dev-io.c:533         Closed /dev/ram10
#device/dev-io.c:487         Opened /dev/ram11 RO O_DIRECT
#device/dev-io.c:134         /dev/ram11: block size is 4096 bytes
#label/label.c:184       /dev/ram11: No label detected
#device/dev-io.c:533         Closed /dev/ram11
#device/dev-io.c:487         Opened /dev/ram12 RO O_DIRECT
#device/dev-io.c:134         /dev/ram12: block size is 4096 bytes
#label/label.c:184       /dev/ram12: No label detected
#device/dev-io.c:533         Closed /dev/ram12
#device/dev-io.c:487         Opened /dev/ram13 RO O_DIRECT
#device/dev-io.c:134         /dev/ram13: block size is 4096 bytes
#label/label.c:184       /dev/ram13: No label detected
#device/dev-io.c:533         Closed /dev/ram13
#device/dev-io.c:487         Opened /dev/ram14 RO O_DIRECT
#device/dev-io.c:134         /dev/ram14: block size is 4096 bytes
#label/label.c:184       /dev/ram14: No label detected
#device/dev-io.c:533         Closed /dev/ram14
#device/dev-io.c:487         Opened /dev/ram15 RO O_DIRECT
#device/dev-io.c:134         /dev/ram15: block size is 4096 bytes
#label/label.c:184       /dev/ram15: No label detected
#device/dev-io.c:533         Closed /dev/ram15
#label/label.c:270         Using cached label for /dev/sda8
#label/label.c:270         Using cached label for /dev/sda8
#format_text/format-text.c:498         Read iscsivg01 metadata (3) from /dev/sda8 at 6656 size 678
#metadata/pv_manip.c:296         /dev/sda8 0:      0  47683: NULL(0:0)
#format_text/archiver.c:127     Archiving volume group "iscsivg01" metadata (seqno 3).
#metadata/lv_manip.c:2042     Creating logical volume lun0
#metadata/pv_map.c:55         Allowing allocation on /dev/sda8 start PE 0 length 47683
#metadata/lv_manip.c:1366         Trying allocation using contiguous policy.  Need 47616 extents for 1 parallel areas and 0 log areas of 0 extents. (Total 47616 extents.)
#metadata/lv_manip.c:1230         Trying allocation area 0 on /dev/sda8 start PE 0 length 47616 leaving 67.
#metadata/lv_manip.c:795         Allocating parallel area 0 on /dev/sda8 start PE 0 length 47616.
#metadata/pv_manip.c:296         /dev/sda8 0:      0  47616: lun0(0:0)
#metadata/pv_manip.c:296         /dev/sda8 1:  47616     67: NULL(0:0)
#device/dev-io.c:533         Closed /dev/sda8
#device/dev-io.c:487         Opened /dev/sda8 RW O_DIRECT
#device/dev-io.c:134         /dev/sda8: block size is 4096 bytes
#format_text/format-text.c:590         Writing iscsivg01 metadata to /dev/sda8 at 7680 len 941
#format_text/format-text.c:695         Pre-Committing iscsivg01 metadata (4) to /dev/sda8 header at 4096
#format_text/format-text.c:695         Committing iscsivg01 metadata (4) to /dev/sda8 header at 4096
#format_text/archiver.c:390     Creating volume group backup "/etc/lvm/backup/iscsivg01" (seqno 4).
#format_text/format-text.c:888         Writing iscsivg01 metadata to /etc/lvm/backup/.lvm_piing-node-2_14473_2072241393
#format_text/format-text.c:932         Committing iscsivg01 metadata (4)
#format_text/format-text.c:933         Renaming /etc/lvm/backup/iscsivg01.tmp to /etc/lvm/backup/iscsivg01
#locking/file_locking.c:291       Locking LV JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy (R)
#metadata/metadata.c:3091       Finding volume group for uuid JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy
#label/label.c:160       /dev/sda8: lvm2 label detected
#cache/lvmcache.c:1136         lvmcache: /dev/sda8: now in VG #orphans_lvm2 (#orphans_lvm2) with 1 mdas
#format_text/format-text.c:1137         /dev/sda8: Found metadata at 7680 size 941 (in area at 4096 size 192512) for iscsivg01 (JuQJwx-pH4y-vuGj-uo82-viH0-B0DH-0Do7dx)
#cache/lvmcache.c:1136         lvmcache: /dev/sda8: now in VG iscsivg01 with 1 mdas
#cache/lvmcache.c:923         lvmcache: /dev/sda8: setting iscsivg01 VGID to JuQJwxpH4yvuGjuo82viH0B0DH0Do7dx
#cache/lvmcache.c:1173         lvmcache: /dev/sda8: VG iscsivg01: Set creation host to piing-node-2.
#label/label.c:270         Using cached label for /dev/sda8
#format_text/format-text.c:498         Read iscsivg01 metadata (4) from /dev/sda8 at 7680 size 941
#metadata/metadata.c:3097     Found volume group "iscsivg01"
#activate/dev_manager.c:236         Getting device info for iscsivg01-lun0 [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy NF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy NF   [16384]
#device/dev-io.c:291       /dev/sda8: read_ahead is 256 sectors
#mm/memlock.c:265       Locking memory
#mm/memlock.c:176         mlock        764KiB      8048000 -      8107000 r-xp  00000000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         mlock          8KiB      8107000 -      8109000 r--p  000bf000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         mlock         12KiB      8109000 -      810c000 rw-p  000c1000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         mlock         32KiB      810c000 -      8114000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock      10500KiB      8ece000 -      990f000 rw-p  00000000 00:00 0          [heap]
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7282000-b7482000 r--p 00000000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         mlock          8KiB     b7482000 -     b7484000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         92KiB     b7484000 -     b749b000 r-xp  00000000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         mlock          4KiB     b749b000 -     b749c000 r--p  00016000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         mlock          4KiB     b749c000 -     b749d000 rw-p  00017000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         mlock          8KiB     b749d000 -     b749f000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         28KiB     b749f000 -     b74a6000 r-xp  00000000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         mlock          4KiB     b74a6000 -     b74a7000 r--p  00006000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         mlock          4KiB     b74a7000 -     b74a8000 rw-p  00007000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         mlock        116KiB     b74a8000 -     b74c5000 r-xp  00000000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         mlock          4KiB     b74c5000 -     b74c6000 r--p  0001c000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         mlock          4KiB     b74c6000 -     b74c7000 rw-p  0001d000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         mlock          4KiB     b74c7000 -     b74c8000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock        112KiB     b74c8000 -     b74e4000 r-xp  00000000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         mlock          8KiB     b74e4000 -     b74e6000 r--p  0001b000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         mlock          4KiB     b74e6000 -     b74e7000 rw-p  0001d000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         mlock       1660KiB     b74e7000 -     b7686000 r-xp  00000000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         mlock          8KiB     b7686000 -     b7688000 r--p  0019f000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         mlock          4KiB     b7688000 -     b7689000 rw-p  001a1000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         mlock         12KiB     b7689000 -     b768c000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         56KiB     b768c000 -     b769a000 r-xp  00000000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         mlock          4KiB     b769a000 -     b769b000 r--p  0000e000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         mlock          4KiB     b769b000 -     b769c000 rw-p  0000f000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         mlock        136KiB     b769c000 -     b76be000 r-xp  00000000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         mlock          4KiB     b76be000 -     b76bf000 r--p  00021000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         mlock          8KiB     b76bf000 -     b76c1000 rw-p  00022000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76c1000-b76f6000 r-xp 00000000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f6000-b76f7000 r--p 00035000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f7000-b76fa000 rw-p 00036000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:176         mlock          8KiB     b76fa000 -     b76fc000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         16KiB     b76fc000 -     b7700000 r-xp  00000000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         mlock          4KiB     b7700000 -     b7701000 r--p  00003000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         mlock          4KiB     b7701000 -     b7702000 rw-p  00004000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7702000-b7705000 r-xp 00000000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7705000-b7706000 r--p 00002000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7706000-b7707000 rw-p 00003000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:176         mlock          4KiB     b770e000 -     b770f000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'gconv/gconv-modules.cache' matches 'b770f000-b7716000 r--s 00000000 08:05 397138     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache': Skipping.
#mm/memlock.c:176         mlock          4KiB     b7716000 -     b7717000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7717000-b7718000 r--p 005e0000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         mlock          8KiB     b7718000 -     b771a000 rw-p  00000000 00:00 0
#mm/memlock.c:148         mlock ignore filter '[vdso]' matches 'b771a000-b771b000 r-xp 00000000 00:00 0          [vdso]': Skipping.
#mm/memlock.c:176         mlock        128KiB     b771b000 -     b773b000 r-xp  00000000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         mlock          4KiB     b773b000 -     b773c000 r--p  0001f000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         mlock          4KiB     b773c000 -     b773d000 rw-p  00020000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         mlock        268KiB     bfb20000 -     bfb63000 rw-p  00000000 00:00 0          [stack]
#mm/memlock.c:176         mlock        268KiB     bfb20000 -     bfb63000 rw-p  00000000 00:00 0          [stack]
#mm/memlock.c:232         Locked 14680064 bytes
#mm/memlock.c:318         memlock_count inc to 1
#activate/dev_manager.c:827         Getting device info for iscsivg01-lun0 [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy OF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy OF   [16384]
#activate/dev_manager.c:827         Getting device info for iscsivg01-lun0-real [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-real]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-real OF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-real OF   [16384]
#activate/dev_manager.c:827         Getting device info for iscsivg01-lun0-cow [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-cow]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-cow OF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-cow OF   [16384]
#activate/dev_manager.c:1135         Checking kernel supports striped segment type for lun0
#metadata/metadata.c:2160         Calculated readahead of LV lun0 is 256
#libdm-deptree.c:1268     Creating iscsivg01-lun0
#ioctl/libdm-iface.c:1821         dm create iscsivg01-lun0 LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy NF   [16384]
#libdm-common.c:799         iscsivg01-lun0: Stacking NODE_ADD (252,1) 0:6 0660
#libdm-deptree.c:1601     Loading iscsivg01-lun0 table (252:1)
[COLOR="Red"]#libdm-deptree.c:1547         Adding target to (252:1): 0 390070272 linear 8:8 384
#ioctl/libdm-iface.c:1821         dm table   (252:1) OF   [16384]
#ioctl/libdm-iface.c:1821         dm reload   (252:1) NF   [16384]
#ioctl/libdm-iface.c:1838   device-mapper: reload ioctl failed: Invalid argument[/COLOR]
#libdm-deptree.c:1686         <backtrace>
#activate/dev_manager.c:1471         <backtrace>
#activate/dev_manager.c:1506         <backtrace>
#activate/activate.c:571         <backtrace>
#activate/activate.c:1128         <backtrace>
#mm/memlock.c:282       Unlocking memory
#mm/memlock.c:176         munlock        764KiB      8048000 -      8107000 r-xp  00000000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         munlock          8KiB      8107000 -      8109000 r--p  000bf000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         munlock         12KiB      8109000 -      810c000 rw-p  000c1000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         munlock         32KiB      810c000 -      8114000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock      10500KiB      8ece000 -      990f000 rw-p  00000000 00:00 0          [heap]
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7282000-b7482000 r--p 00000000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         munlock          8KiB     b7482000 -     b7484000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         92KiB     b7484000 -     b749b000 r-xp  00000000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         munlock          4KiB     b749b000 -     b749c000 r--p  00016000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         munlock          4KiB     b749c000 -     b749d000 rw-p  00017000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         munlock          8KiB     b749d000 -     b749f000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         28KiB     b749f000 -     b74a6000 r-xp  00000000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         munlock          4KiB     b74a6000 -     b74a7000 r--p  00006000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         munlock          4KiB     b74a7000 -     b74a8000 rw-p  00007000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         munlock        116KiB     b74a8000 -     b74c5000 r-xp  00000000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         munlock          4KiB     b74c5000 -     b74c6000 r--p  0001c000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         munlock          4KiB     b74c6000 -     b74c7000 rw-p  0001d000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         munlock          4KiB     b74c7000 -     b74c8000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock        112KiB     b74c8000 -     b74e4000 r-xp  00000000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         munlock          8KiB     b74e4000 -     b74e6000 r--p  0001b000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         munlock          4KiB     b74e6000 -     b74e7000 rw-p  0001d000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         munlock       1660KiB     b74e7000 -     b7686000 r-xp  00000000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         munlock          8KiB     b7686000 -     b7688000 r--p  0019f000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         munlock          4KiB     b7688000 -     b7689000 rw-p  001a1000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         munlock         12KiB     b7689000 -     b768c000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         56KiB     b768c000 -     b769a000 r-xp  00000000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         munlock          4KiB     b769a000 -     b769b000 r--p  0000e000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         munlock          4KiB     b769b000 -     b769c000 rw-p  0000f000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         munlock        136KiB     b769c000 -     b76be000 r-xp  00000000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         munlock          4KiB     b76be000 -     b76bf000 r--p  00021000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         munlock          8KiB     b76bf000 -     b76c1000 rw-p  00022000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76c1000-b76f6000 r-xp 00000000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f6000-b76f7000 r--p 00035000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f7000-b76fa000 rw-p 00036000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:176         munlock          8KiB     b76fa000 -     b76fc000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         16KiB     b76fc000 -     b7700000 r-xp  00000000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         munlock          4KiB     b7700000 -     b7701000 r--p  00003000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         munlock          4KiB     b7701000 -     b7702000 rw-p  00004000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7702000-b7705000 r-xp 00000000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7705000-b7706000 r--p 00002000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7706000-b7707000 rw-p 00003000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:176         munlock          4KiB     b770e000 -     b770f000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'gconv/gconv-modules.cache' matches 'b770f000-b7716000 r--s 00000000 08:05 397138     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache': Skipping.
#mm/memlock.c:176         munlock          4KiB     b7716000 -     b7717000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7717000-b7718000 r--p 005e0000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         munlock          8KiB     b7718000 -     b771a000 rw-p  00000000 00:00 0
#mm/memlock.c:148         mlock ignore filter '[vdso]' matches 'b771a000-b771b000 r-xp 00000000 00:00 0          [vdso]': Skipping.
#mm/memlock.c:176         munlock        128KiB     b771b000 -     b773b000 r-xp  00000000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         munlock          4KiB     b773b000 -     b773c000 r--p  0001f000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         munlock          4KiB     b773c000 -     b773d000 rw-p  00020000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         munlock          0KiB     bfb20000 -     bfb20000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock        268KiB     bfb20000 -     bfb63000 rw-p  00000000 00:00 0          [stack]
#mm/memlock.c:232         Unlocked 14405632 bytes
#mm/memlock.c:327         memlock_count dec to 0
#libdm-common.c:475         Created /dev/mapper/iscsivg01-lun0
#activate/activate.c:1155         <backtrace>
#locking/locking.c:389         <backtrace>
#metadata/lv_manip.c:3230   Aborting. Failed to activate new LV to wipe the start of it.
#locking/file_locking.c:286       Locking LV JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy (NL)
#metadata/metadata.c:3091       Finding volume group for uuid JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy
#label/label.c:270         Using cached label for /dev/sda8
#label/label.c:270         Using cached label for /dev/sda8
#format_text/format-text.c:498         Read iscsivg01 metadata (4) from /dev/sda8 at 7680 size 941
#metadata/metadata.c:3097     Found volume group "iscsivg01"
#activate/dev_manager.c:236         Getting device info for iscsivg01-lun0 [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy OF   [16384]
#mm/memlock.c:265       Locking memory
#mm/memlock.c:176         mlock        764KiB      8048000 -      8107000 r-xp  00000000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         mlock          8KiB      8107000 -      8109000 r--p  000bf000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         mlock         12KiB      8109000 -      810c000 rw-p  000c1000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         mlock         32KiB      810c000 -      8114000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock      10500KiB      8ece000 -      990f000 rw-p  00000000 00:00 0          [heap]
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7282000-b7482000 r--p 00000000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         mlock          8KiB     b7482000 -     b7484000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         92KiB     b7484000 -     b749b000 r-xp  00000000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         mlock          4KiB     b749b000 -     b749c000 r--p  00016000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         mlock          4KiB     b749c000 -     b749d000 rw-p  00017000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         mlock          8KiB     b749d000 -     b749f000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         28KiB     b749f000 -     b74a6000 r-xp  00000000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         mlock          4KiB     b74a6000 -     b74a7000 r--p  00006000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         mlock          4KiB     b74a7000 -     b74a8000 rw-p  00007000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         mlock        116KiB     b74a8000 -     b74c5000 r-xp  00000000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         mlock          4KiB     b74c5000 -     b74c6000 r--p  0001c000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         mlock          4KiB     b74c6000 -     b74c7000 rw-p  0001d000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         mlock          4KiB     b74c7000 -     b74c8000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock        112KiB     b74c8000 -     b74e4000 r-xp  00000000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         mlock          8KiB     b74e4000 -     b74e6000 r--p  0001b000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         mlock          4KiB     b74e6000 -     b74e7000 rw-p  0001d000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         mlock       1660KiB     b74e7000 -     b7686000 r-xp  00000000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         mlock          8KiB     b7686000 -     b7688000 r--p  0019f000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         mlock          4KiB     b7688000 -     b7689000 rw-p  001a1000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         mlock         12KiB     b7689000 -     b768c000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         56KiB     b768c000 -     b769a000 r-xp  00000000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         mlock          4KiB     b769a000 -     b769b000 r--p  0000e000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         mlock          4KiB     b769b000 -     b769c000 rw-p  0000f000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         mlock        136KiB     b769c000 -     b76be000 r-xp  00000000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         mlock          4KiB     b76be000 -     b76bf000 r--p  00021000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         mlock          8KiB     b76bf000 -     b76c1000 rw-p  00022000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76c1000-b76f6000 r-xp 00000000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f6000-b76f7000 r--p 00035000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f7000-b76fa000 rw-p 00036000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:176         mlock          8KiB     b76fa000 -     b76fc000 rw-p  00000000 00:00 0
#mm/memlock.c:176         mlock         16KiB     b76fc000 -     b7700000 r-xp  00000000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         mlock          4KiB     b7700000 -     b7701000 r--p  00003000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         mlock          4KiB     b7701000 -     b7702000 rw-p  00004000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7702000-b7705000 r-xp 00000000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7705000-b7706000 r--p 00002000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7706000-b7707000 rw-p 00003000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:176         mlock          4KiB     b770e000 -     b770f000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'gconv/gconv-modules.cache' matches 'b770f000-b7716000 r--s 00000000 08:05 397138     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache': Skipping.
#mm/memlock.c:176         mlock          4KiB     b7716000 -     b7717000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7717000-b7718000 r--p 005e0000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         mlock          8KiB     b7718000 -     b771a000 rw-p  00000000 00:00 0
#mm/memlock.c:148         mlock ignore filter '[vdso]' matches 'b771a000-b771b000 r-xp 00000000 00:00 0          [vdso]': Skipping.
#mm/memlock.c:176         mlock        128KiB     b771b000 -     b773b000 r-xp  00000000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         mlock          4KiB     b773b000 -     b773c000 r--p  0001f000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         mlock          4KiB     b773c000 -     b773d000 rw-p  00020000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         mlock        268KiB     bfb20000 -     bfb63000 rw-p  00000000 00:00 0          [stack]
#mm/memlock.c:176         mlock        268KiB     bfb20000 -     bfb63000 rw-p  00000000 00:00 0          [stack]
#mm/memlock.c:232         Locked 14680064 bytes
#mm/memlock.c:318         memlock_count inc to 1
#activate/dev_manager.c:827         Getting device info for iscsivg01-lun0 [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy OF   [16384]
#ioctl/libdm-iface.c:1821         dm deps   (252:1) OF   [16384]
#activate/dev_manager.c:827         Getting device info for iscsivg01-lun0-real [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-real]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-real OF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-real OF   [16384]
#activate/dev_manager.c:827         Getting device info for iscsivg01-lun0-cow [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-cow]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-cow OF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy-cow OF   [16384]
#ioctl/libdm-iface.c:1821         dm info   (252:1) OF   [16384]
#libdm-deptree.c:865     Removing iscsivg01-lun0 (252:1)
#libdm-common.c:1153         Udev cookie 0xd4d123d (semid 294912) created
#libdm-common.c:1166         Udev cookie 0xd4d123d (semid 294912) incremented
#libdm-common.c:1054         Udev cookie 0xd4d123d (semid 294912) incremented
#libdm-common.c:1226         Udev cookie 0xd4d123d (semid 294912) assigned to dm_task type 2 with flags 0x0
#ioctl/libdm-iface.c:1821         dm remove   (252:1) NF   [16384]
#libdm-common.c:815         iscsivg01-lun0: Stacking NODE_DEL (replaces other stacked ops)
#libdm-common.c:1081         Udev cookie 0xd4d123d (semid 294912) decremented
#libdm-common.c:1276         Udev cookie 0xd4d123d (semid 294912): Waiting for zero
#libdm-common.c:1096         Udev cookie 0xd4d123d (semid 294912) destroyed
#mm/memlock.c:282       Unlocking memory
#mm/memlock.c:176         munlock        764KiB      8048000 -      8107000 r-xp  00000000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         munlock          8KiB      8107000 -      8109000 r--p  000bf000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         munlock         12KiB      8109000 -      810c000 rw-p  000c1000 08:05 265000     /sbin/lvm
#mm/memlock.c:176         munlock         32KiB      810c000 -      8114000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock      10500KiB      8ece000 -      990f000 rw-p  00000000 00:00 0          [heap]
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7282000-b7482000 r--p 00000000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         munlock          8KiB     b7482000 -     b7484000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         92KiB     b7484000 -     b749b000 r-xp  00000000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         munlock          4KiB     b749b000 -     b749c000 r--p  00016000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         munlock          4KiB     b749c000 -     b749d000 rw-p  00017000 08:05 653987     /lib/i386-linux-gnu/libpthread-2.15.so
#mm/memlock.c:176         munlock          8KiB     b749d000 -     b749f000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         28KiB     b749f000 -     b74a6000 r-xp  00000000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         munlock          4KiB     b74a6000 -     b74a7000 r--p  00006000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         munlock          4KiB     b74a7000 -     b74a8000 rw-p  00007000 08:05 653993     /lib/i386-linux-gnu/librt-2.15.so
#mm/memlock.c:176         munlock        116KiB     b74a8000 -     b74c5000 r-xp  00000000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         munlock          4KiB     b74c5000 -     b74c6000 r--p  0001c000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         munlock          4KiB     b74c6000 -     b74c7000 rw-p  0001d000 08:05 653995     /lib/i386-linux-gnu/libselinux.so.1
#mm/memlock.c:176         munlock          4KiB     b74c7000 -     b74c8000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock        112KiB     b74c8000 -     b74e4000 r-xp  00000000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         munlock          8KiB     b74e4000 -     b74e6000 r--p  0001b000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         munlock          4KiB     b74e6000 -     b74e7000 rw-p  0001d000 08:05 654004     /lib/i386-linux-gnu/libtinfo.so.5.9
#mm/memlock.c:176         munlock       1660KiB     b74e7000 -     b7686000 r-xp  00000000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         munlock          8KiB     b7686000 -     b7688000 r--p  0019f000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         munlock          4KiB     b7688000 -     b7689000 rw-p  001a1000 08:05 653907     /lib/i386-linux-gnu/libc-2.15.so
#mm/memlock.c:176         munlock         12KiB     b7689000 -     b768c000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         56KiB     b768c000 -     b769a000 r-xp  00000000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         munlock          4KiB     b769a000 -     b769b000 r--p  0000e000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         munlock          4KiB     b769b000 -     b769c000 rw-p  0000f000 08:05 654006     /lib/i386-linux-gnu/libudev.so.0.13.0
#mm/memlock.c:176         munlock        136KiB     b769c000 -     b76be000 r-xp  00000000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         munlock          4KiB     b76be000 -     b76bf000 r--p  00021000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:176         munlock          8KiB     b76bf000 -     b76c1000 rw-p  00022000 08:05 659531     /lib/libdevmapper.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76c1000-b76f6000 r-xp 00000000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f6000-b76f7000 r--p 00035000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:158         mlock default filter '/libreadline.so.' matches 'b76f7000-b76fa000 rw-p 00036000 08:05 653990     /lib/i386-linux-gnu/libreadline.so.6.2': Skipping.
#mm/memlock.c:176         munlock          8KiB     b76fa000 -     b76fc000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock         16KiB     b76fc000 -     b7700000 r-xp  00000000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         munlock          4KiB     b7700000 -     b7701000 r--p  00003000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:176         munlock          4KiB     b7701000 -     b7702000 rw-p  00004000 08:05 658092     /lib/libdevmapper-event.so.1.02.1
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7702000-b7705000 r-xp 00000000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7705000-b7706000 r--p 00002000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:158         mlock default filter '/libdl-' matches 'b7706000-b7707000 rw-p 00003000 08:05 653920     /lib/i386-linux-gnu/libdl-2.15.so': Skipping.
#mm/memlock.c:176         munlock          4KiB     b770e000 -     b770f000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'gconv/gconv-modules.cache' matches 'b770f000-b7716000 r--s 00000000 08:05 397138     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache': Skipping.
#mm/memlock.c:176         munlock          4KiB     b7716000 -     b7717000 rw-p  00000000 00:00 0
#mm/memlock.c:158         mlock default filter 'locale/locale-archive' matches 'b7717000-b7718000 r--p 005e0000 08:05 400424     /usr/lib/locale/locale-archive': Skipping.
#mm/memlock.c:176         munlock          8KiB     b7718000 -     b771a000 rw-p  00000000 00:00 0
#mm/memlock.c:148         mlock ignore filter '[vdso]' matches 'b771a000-b771b000 r-xp 00000000 00:00 0          [vdso]': Skipping.
#mm/memlock.c:176         munlock        128KiB     b771b000 -     b773b000 r-xp  00000000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         munlock          4KiB     b773b000 -     b773c000 r--p  0001f000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         munlock          4KiB     b773c000 -     b773d000 rw-p  00020000 08:05 653887     /lib/i386-linux-gnu/ld-2.15.so
#mm/memlock.c:176         munlock          0KiB     bfb20000 -     bfb20000 rw-p  00000000 00:00 0
#mm/memlock.c:176         munlock        268KiB     bfb20000 -     bfb63000 rw-p  00000000 00:00 0          [stack]
#mm/memlock.c:232         Unlocked 14405632 bytes
#mm/memlock.c:327         memlock_count dec to 0
[COLOR="Red"]  Node /dev/mapper/iscsivg01-lun0 was not removed by udev. Falling back to direct node removal.[/COLOR]
#libdm-common.c:503         Removed /dev/mapper/iscsivg01-lun0
#activate/dev_manager.c:236         Getting device info for iscsivg01-lun0 [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy OF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy OF   [16384]
#locking/file_locking.c:281       Unlocking LV JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy
#metadata/metadata.c:3091       Finding volume group for uuid JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy
#label/label.c:270         Using cached label for /dev/sda8
#label/label.c:270         Using cached label for /dev/sda8
#format_text/format-text.c:498         Read iscsivg01 metadata (4) from /dev/sda8 at 7680 size 941
#metadata/metadata.c:3097     Found volume group "iscsivg01"
#activate/dev_manager.c:236         Getting device info for iscsivg01-lun0 [LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy]
#ioctl/libdm-iface.c:1821         dm info  LVM-JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy NF   [16384]
#ioctl/libdm-iface.c:1821         dm info  JuQJwxpH4yvuGjuo82viH0B0DH0Do7dxpiezeL2gMmflbxUbpOYw8sD2KPSIraMy NF   [16384]
#activate/activate.c:938         <backtrace>
#metadata/pv_manip.c:296         /dev/sda8 0:      0  47616: NULL(0:0)
#metadata/pv_manip.c:296         /dev/sda8 1:  47616     67: NULL(0:0)
#format_text/format-text.c:590         Writing iscsivg01 metadata to /dev/sda8 at 8704 len 678
#format_text/format-text.c:695         Pre-Committing iscsivg01 metadata (5) to /dev/sda8 header at 4096
#format_text/format-text.c:695         Committing iscsivg01 metadata (5) to /dev/sda8 header at 4096
#format_text/archiver.c:390     Creating volume group backup "/etc/lvm/backup/iscsivg01" (seqno 5).
#format_text/format-text.c:888         Writing iscsivg01 metadata to /etc/lvm/backup/.lvm_piing-node-2_14473_712565374
#format_text/format-text.c:932         Committing iscsivg01 metadata (5)
#format_text/format-text.c:933         Renaming /etc/lvm/backup/iscsivg01.tmp to /etc/lvm/backup/iscsivg01
#lvcreate.c:540         <backtrace>
#locking/file_locking.c:74       Unlocking /var/lock/lvm/V_iscsivg01
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/V_iscsivg01
#device/dev-io.c:533         Closed /dev/sda8

```


I've searched for the solution and tried many things: tweaking filter in lvm.conf, partitioning the drbd device, etc.. but none worked. Moreover, I've actually set up such system successfully just a week before. But now when the servers had to be re-configured with RAID-1 and re-installed, the old settings stopped working. 

This is the filter line I'm using:
```

	filter = [ "a|/dev/lvm/drbd|", "a|/dev/drbd|", "r/.*/" ]

```

While investigating further, I found that when vgcreate command was used to create Volume Group over Physical Volume already sitting on DRBD device ( /dev/drbd0, /dev/lvm/drbd0 ), the device reference from pvs fell to ( /dev/sda8 ), the device underlying DRBD. Even weirder is that result from pvscan still showed as DRBD device.

```


piing@piing-node-2:~$ sudo vgs
  No volume groups found
  
piing@piing-node-2:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  No volume groups found
  
piing@piing-node-2:~$ sudo pvs
  PV         VG   Fmt  Attr PSize   PFree
  /dev/drbd0      lvm2 a-   186.26g 186.26g
  
piing@piing-node-2:~$ sudo pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  PV /dev/drbd0   VG iscsivg01   lvm2 [186.26 GiB / 186.26 GiB free]
  Total: 1 [186.26 GiB] / in use: 1 [186.26 GiB] / in no VG: 0 [0   ]
  ]
  
piing@piing-node-2:~$ sudo vgcreate iscsivg01 /dev/drbd0
  Volume group "iscsivg01" successfully created
  
piing@piing-node-2:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "iscsivg01" using metadata type lvm2
  
piing@piing-node-2:~$ sudo vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  iscsivg01   1   0   0 wz--n- 186.26g 186.26g
  
piing@piing-node-2:~$ sudo pvs
  PV         VG        Fmt  Attr PSize   PFree
[COLOR="Red"]  /dev/sda8  iscsivg01 lvm2 a-   186.26g 186.26g[/COLOR]
  
piing@piing-node-2:~$ sudo pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
[COLOR="Orange"]  PV /dev/drbd0   VG iscsivg01   lvm2 [186.26 GiB / 186.26 GiB free][/COLOR]
  Total: 1 [186.26 GiB] / in use: 1 [186.26 GiB] / in no VG: 0 [0   ]
  ]
  

```


If I then removed the VG, result from pvs went back to showing DRBD device. Then I created VG again, and it becomes /dev/sda8 again.

```


piing@piing-node-2:~$ sudo vgremove iscsivg01
  Volume group "iscsivg01" successfully removed
  
piing@piing-node-2:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  No volume groups found
  
piing@piing-node-2:~$ sudo pvs
  PV         VG   Fmt  Attr PSize   PFree
  /dev/drbd0      lvm2 a-   186.26g 186.26g
  
piing@piing-node-2:~$ sudo vgcreate iscsivg01 /dev/drbd0
  Volume group "iscsivg01" successfully created
  
piing@piing-node-2:~$ sudo pvs
  PV         VG        Fmt  Attr PSize   PFree
[COLOR="Red"]  /dev/sda8  iscsivg01 lvm2 a-   186.26g 186.26g[/COLOR]
  
piing@piing-node-2:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "iscsivg01" using metadata type lvm2
  
piing@piing-node-2:~$ sudo pvs
  PV         VG        Fmt  Attr PSize   PFree
[COLOR="Red"]  /dev/sda8  iscsivg01 lvm2 a-   186.26g 186.26g[/COLOR]
  
piing@piing-node-2:~$ sudo vgremove iscsivg01
  Volume group "iscsivg01" successfully removed
  
piing@piing-node-2:~$ sudo pvs
  PV         VG   Fmt  Attr PSize   PFree
  /dev/drbd0      lvm2 a-   186.26g 186.26g
  

```

And the system doesn't even recognize ( /dev/drbd0 ) or ( /dev/lvm/drbd0 ) to be in volume group ( iscsivg01 ) when directly addressed.

```


piing@piing-node-2:~$ sudo pvs -v /dev/drbd0
    Using physical volume(s) on command line
    Wiping cache of LVM-capable devices
  PV             VG   Fmt  Attr PSize   PFree   DevSize PV UUID
  /dev/drbd0      lvm2 a-   186.26g 186.26g 186.26g IeZ1rK-UMhp-bLqH-waSM-PZ3t-afJU-Wbvy2G
  
piing@piing-node-2:~$ sudo vgremove iscsivg01
  Volume group "iscsivg01" successfully removed
  
piing@piing-node-2:~$ sudo vgcreate -v iscsivg01 /dev/drbd0
    Wiping cache of LVM-capable devices
    Wiping cache of LVM-capable devices
    Adding physical volume '/dev/drbd0' to volume group 'iscsivg01'
    Archiving volume group "iscsivg01" metadata (seqno 0).
    Creating volume group backup "/etc/lvm/backup/iscsivg01" (seqno 1).
  Volume group "iscsivg01" successfully created
  
piing@piing-node-2:~$ sudo pvs -v
    Scanning for physical volume names
    Wiping cache of LVM-capable devices
  PV         VG   Fmt  Attr PSize   PFree   DevSize PV UUID
[COLOR="Red"]  /dev/sda8       lvm2 a-   186.26g 186.26g 186.26g IeZ1rK-UMhp-bLqH-waSM-PZ3t-afJU-Wbvy2G[/COLOR]
  
piing@piing-node-2:~$ sudo lvcreate -v -L 186G -n lun0 iscsivg01 /dev/drbd0
    Setting logging type to disk
    Finding volume group "iscsivg01"
[COLOR="Red"]  Physical Volume "/dev/drbd0" not found in Volume Group "iscsivg01"[/COLOR]
  

```

Finally, I tried re-creating it as cluster-aware volume. Which left me unable to even do anything with it anymore :(

```

piing@piing-node-2:~$ sudo vgcreate -vvvv -c y iscsivg01 /dev/lvm/drbd0
#lvmcmdline.c:1035         Processing: vgcreate -vvvv -c y iscsivg01 /dev/lvm/drbd0
#lvmcmdline.c:1038         O_DIRECT will be used
#config/config.c:987       Setting global/locking_type to 1
#config/config.c:987       Setting global/wait_for_locks to 1
#locking/locking.c:240       File-based locking selected.
#config/config.c:964       Setting global/locking_dir to /var/lock/lvm
#config/config.c:992       metadata/pvmetadatasize not found in config: defaulting to 255
#config/config.c:992       metadata/pvmetadatacopies not found in config: defaulting to 1
#locking/file_locking.c:235       Locking /var/lock/lvm/V_iscsivg01 WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/V_iscsivg01:aux WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/V_iscsivg01 WB
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/V_iscsivg01:aux
#device/dev-io.c:487         Opened /dev/ram0 RO O_DIRECT
#device/dev-io.c:134         /dev/ram0: block size is 4096 bytes
#label/label.c:184       /dev/ram0: No label detected
#device/dev-io.c:533         Closed /dev/ram0
#device/dev-io.c:487         Opened /dev/ram1 RO O_DIRECT
#device/dev-io.c:134         /dev/ram1: block size is 4096 bytes
#label/label.c:184       /dev/ram1: No label detected
#device/dev-io.c:533         Closed /dev/ram1
#device/dev-io.c:487         Opened /dev/sda1 RO O_DIRECT
#device/dev-io.c:134         /dev/sda1: block size is 4096 bytes
#label/label.c:184       /dev/sda1: No label detected
#device/dev-io.c:533         Closed /dev/sda1
#device/dev-io.c:487         Opened /dev/ram2 RO O_DIRECT
#device/dev-io.c:134         /dev/ram2: block size is 4096 bytes
#label/label.c:184       /dev/ram2: No label detected
#device/dev-io.c:533         Closed /dev/ram2
#device/dev-io.c:487         Opened /dev/ram3 RO O_DIRECT
#device/dev-io.c:134         /dev/ram3: block size is 4096 bytes
#label/label.c:184       /dev/ram3: No label detected
#device/dev-io.c:533         Closed /dev/ram3
#device/dev-io.c:487         Opened /dev/ram4 RO O_DIRECT
#device/dev-io.c:134         /dev/ram4: block size is 4096 bytes
#label/label.c:184       /dev/ram4: No label detected
#device/dev-io.c:533         Closed /dev/ram4
#device/dev-io.c:487         Opened /dev/ram5 RO O_DIRECT
#device/dev-io.c:134         /dev/ram5: block size is 4096 bytes
#label/label.c:184       /dev/ram5: No label detected
#device/dev-io.c:533         Closed /dev/ram5
#device/dev-io.c:487         Opened /dev/sda5 RO O_DIRECT
#device/dev-io.c:134         /dev/sda5: block size is 4096 bytes
#label/label.c:184       /dev/sda5: No label detected
#device/dev-io.c:533         Closed /dev/sda5
#device/dev-io.c:487         Opened /dev/ram6 RO O_DIRECT
#device/dev-io.c:134         /dev/ram6: block size is 4096 bytes
#label/label.c:184       /dev/ram6: No label detected
#device/dev-io.c:533         Closed /dev/ram6
#device/dev-io.c:487         Opened /dev/sda6 RO O_DIRECT
#device/dev-io.c:134         /dev/sda6: block size is 4096 bytes
#label/label.c:184       /dev/sda6: No label detected
#device/dev-io.c:533         Closed /dev/sda6
#device/dev-io.c:487         Opened /dev/ram7 RO O_DIRECT
#device/dev-io.c:134         /dev/ram7: block size is 4096 bytes
#label/label.c:184       /dev/ram7: No label detected
#device/dev-io.c:533         Closed /dev/ram7
#device/dev-io.c:487         Opened /dev/sda7 RO O_DIRECT
#device/dev-io.c:134         /dev/sda7: block size is 4096 bytes
#label/label.c:184       /dev/sda7: No label detected
#device/dev-io.c:533         Closed /dev/sda7
#device/dev-io.c:487         Opened /dev/ram8 RO O_DIRECT
#device/dev-io.c:134         /dev/ram8: block size is 4096 bytes
#label/label.c:184       /dev/ram8: No label detected
#device/dev-io.c:533         Closed /dev/ram8
#device/dev-io.c:487         Opened /dev/sda8 RO O_DIRECT
#device/dev-io.c:134         /dev/sda8: block size is 4096 bytes
#label/label.c:160       /dev/sda8: lvm2 label detected
#cache/lvmcache.c:1136         lvmcache: /dev/sda8: now in VG #orphans_lvm2 (#orphans_lvm2)
#format_text/format-text.c:1137         /dev/sda8: Found metadata at 4608 size 683 (in area at 4096 size 192512) for iscsivg01 (ebjnVL-uTLR-ixTo-9ySB-fY5d-0uhF-CTYvyu)
#cache/lvmcache.c:1136         lvmcache: /dev/sda8: now in VG iscsivg01 with 1 mdas
#cache/lvmcache.c:923         lvmcache: /dev/sda8: setting iscsivg01 VGID to ebjnVLuTLRixTo9ySBfY5d0uhFCTYvyu
#cache/lvmcache.c:1173         lvmcache: /dev/sda8: VG iscsivg01: Set creation host to piing-node-2.
#device/dev-io.c:487         Opened /dev/ram9 RO O_DIRECT
#device/dev-io.c:134         /dev/ram9: block size is 4096 bytes
#label/label.c:184       /dev/ram9: No label detected
#device/dev-io.c:533         Closed /dev/ram9
#device/dev-io.c:487         Opened /dev/ram10 RO O_DIRECT
#device/dev-io.c:134         /dev/ram10: block size is 4096 bytes
#label/label.c:184       /dev/ram10: No label detected
#device/dev-io.c:533         Closed /dev/ram10
#device/dev-io.c:487         Opened /dev/ram11 RO O_DIRECT
#device/dev-io.c:134         /dev/ram11: block size is 4096 bytes
#label/label.c:184       /dev/ram11: No label detected
#device/dev-io.c:533         Closed /dev/ram11
#device/dev-io.c:487         Opened /dev/ram12 RO O_DIRECT
#device/dev-io.c:134         /dev/ram12: block size is 4096 bytes
#label/label.c:184       /dev/ram12: No label detected
#device/dev-io.c:533         Closed /dev/ram12
#device/dev-io.c:487         Opened /dev/ram13 RO O_DIRECT
#device/dev-io.c:134         /dev/ram13: block size is 4096 bytes
#label/label.c:184       /dev/ram13: No label detected
#device/dev-io.c:533         Closed /dev/ram13
#device/dev-io.c:487         Opened /dev/ram14 RO O_DIRECT
#device/dev-io.c:134         /dev/ram14: block size is 4096 bytes
#label/label.c:184       /dev/ram14: No label detected
#device/dev-io.c:533         Closed /dev/ram14
#device/dev-io.c:487         Opened /dev/ram15 RO O_DIRECT
#device/dev-io.c:134         /dev/ram15: block size is 4096 bytes
#label/label.c:184       /dev/ram15: No label detected
#device/dev-io.c:533         Closed /dev/ram15
#label/label.c:270         Using cached label for /dev/sda8
#locking/file_locking.c:74       Unlocking /var/lock/lvm/V_iscsivg01
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/V_iscsivg01
#device/dev-io.c:533         Closed /dev/sda8
#vgcreate.c:60   A volume group called iscsivg01 already exists.
piing@piing-node-2:~$ sudo vgremove iscsivg01
  Volume group "iscsivg01" successfully removed
piing@piing-node-2:~$ sudo vgcreate -vvvv -c y iscsivg01 /dev/lvm/drbd0
#lvmcmdline.c:1035         Processing: vgcreate -vvvv -c y iscsivg01 /dev/lvm/drbd0
#lvmcmdline.c:1038         O_DIRECT will be used
#config/config.c:987       Setting global/locking_type to 1
#config/config.c:987       Setting global/wait_for_locks to 1
#locking/locking.c:240       File-based locking selected.
#config/config.c:964       Setting global/locking_dir to /var/lock/lvm
#config/config.c:992       metadata/pvmetadatasize not found in config: defaulting to 255
#config/config.c:992       metadata/pvmetadatacopies not found in config: defaulting to 1
#locking/file_locking.c:235       Locking /var/lock/lvm/V_iscsivg01 WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/V_iscsivg01:aux WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/V_iscsivg01 WB
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/V_iscsivg01:aux
#device/dev-io.c:487         Opened /dev/ram0 RO O_DIRECT
#device/dev-io.c:134         /dev/ram0: block size is 4096 bytes
#label/label.c:184       /dev/ram0: No label detected
#device/dev-io.c:533         Closed /dev/ram0
#device/dev-io.c:487         Opened /dev/ram1 RO O_DIRECT
#device/dev-io.c:134         /dev/ram1: block size is 4096 bytes
#label/label.c:184       /dev/ram1: No label detected
#device/dev-io.c:533         Closed /dev/ram1
#device/dev-io.c:487         Opened /dev/sda1 RO O_DIRECT
#device/dev-io.c:134         /dev/sda1: block size is 4096 bytes
#label/label.c:184       /dev/sda1: No label detected
#device/dev-io.c:533         Closed /dev/sda1
#device/dev-io.c:487         Opened /dev/ram2 RO O_DIRECT
#device/dev-io.c:134         /dev/ram2: block size is 4096 bytes
#label/label.c:184       /dev/ram2: No label detected
#device/dev-io.c:533         Closed /dev/ram2
#device/dev-io.c:487         Opened /dev/ram3 RO O_DIRECT
#device/dev-io.c:134         /dev/ram3: block size is 4096 bytes
#label/label.c:184       /dev/ram3: No label detected
#device/dev-io.c:533         Closed /dev/ram3
#device/dev-io.c:487         Opened /dev/ram4 RO O_DIRECT
#device/dev-io.c:134         /dev/ram4: block size is 4096 bytes
#label/label.c:184       /dev/ram4: No label detected
#device/dev-io.c:533         Closed /dev/ram4
#device/dev-io.c:487         Opened /dev/ram5 RO O_DIRECT
#device/dev-io.c:134         /dev/ram5: block size is 4096 bytes
#label/label.c:184       /dev/ram5: No label detected
#device/dev-io.c:533         Closed /dev/ram5
#device/dev-io.c:487         Opened /dev/sda5 RO O_DIRECT
#device/dev-io.c:134         /dev/sda5: block size is 4096 bytes
#label/label.c:184       /dev/sda5: No label detected
#device/dev-io.c:533         Closed /dev/sda5
#device/dev-io.c:487         Opened /dev/ram6 RO O_DIRECT
#device/dev-io.c:134         /dev/ram6: block size is 4096 bytes
#label/label.c:184       /dev/ram6: No label detected
#device/dev-io.c:533         Closed /dev/ram6
#device/dev-io.c:487         Opened /dev/sda6 RO O_DIRECT
#device/dev-io.c:134         /dev/sda6: block size is 4096 bytes
#label/label.c:184       /dev/sda6: No label detected
#device/dev-io.c:533         Closed /dev/sda6
#device/dev-io.c:487         Opened /dev/ram7 RO O_DIRECT
#device/dev-io.c:134         /dev/ram7: block size is 4096 bytes
#label/label.c:184       /dev/ram7: No label detected
#device/dev-io.c:533         Closed /dev/ram7
#device/dev-io.c:487         Opened /dev/sda7 RO O_DIRECT
#device/dev-io.c:134         /dev/sda7: block size is 4096 bytes
#label/label.c:184       /dev/sda7: No label detected
#device/dev-io.c:533         Closed /dev/sda7
#device/dev-io.c:487         Opened /dev/ram8 RO O_DIRECT
#device/dev-io.c:134         /dev/ram8: block size is 4096 bytes
#label/label.c:184       /dev/ram8: No label detected
#device/dev-io.c:533         Closed /dev/ram8
#device/dev-io.c:487         Opened /dev/sda8 RO O_DIRECT
#device/dev-io.c:134         /dev/sda8: block size is 4096 bytes
#label/label.c:160       /dev/sda8: lvm2 label detected
#cache/lvmcache.c:1136         lvmcache: /dev/sda8: now in VG #orphans_lvm2 (#orphans_lvm2)
#device/dev-io.c:533         Closed /dev/sda8
#device/dev-io.c:487         Opened /dev/ram9 RO O_DIRECT
#device/dev-io.c:134         /dev/ram9: block size is 4096 bytes
#label/label.c:184       /dev/ram9: No label detected
#device/dev-io.c:533         Closed /dev/ram9
#device/dev-io.c:487         Opened /dev/ram10 RO O_DIRECT
#device/dev-io.c:134         /dev/ram10: block size is 4096 bytes
#label/label.c:184       /dev/ram10: No label detected
#device/dev-io.c:533         Closed /dev/ram10
#device/dev-io.c:487         Opened /dev/ram11 RO O_DIRECT
#device/dev-io.c:134         /dev/ram11: block size is 4096 bytes
#label/label.c:184       /dev/ram11: No label detected
#device/dev-io.c:533         Closed /dev/ram11
#device/dev-io.c:487         Opened /dev/ram12 RO O_DIRECT
#device/dev-io.c:134         /dev/ram12: block size is 4096 bytes
#label/label.c:184       /dev/ram12: No label detected
#device/dev-io.c:533         Closed /dev/ram12
#device/dev-io.c:487         Opened /dev/ram13 RO O_DIRECT
#device/dev-io.c:134         /dev/ram13: block size is 4096 bytes
#label/label.c:184       /dev/ram13: No label detected
#device/dev-io.c:533         Closed /dev/ram13
#device/dev-io.c:487         Opened /dev/ram14 RO O_DIRECT
#device/dev-io.c:134         /dev/ram14: block size is 4096 bytes
#label/label.c:184       /dev/ram14: No label detected
#device/dev-io.c:533         Closed /dev/ram14
#device/dev-io.c:487         Opened /dev/ram15 RO O_DIRECT
#device/dev-io.c:134         /dev/ram15: block size is 4096 bytes
#label/label.c:184       /dev/ram15: No label detected
#device/dev-io.c:533         Closed /dev/ram15
#regex/matcher.c:269         Matcher built with 29 dfa states
#config/config.c:987       Setting devices/ignore_suspended_devices to 0
#config/config.c:964       Setting devices/cache_dir to /etc/lvm/cache
#config/config.c:987       Setting devices/write_cache_state to 0
#filters/filter-persistent.c:56     Wiping cache of LVM-capable devices
#device/dev-cache.c:277         /dev/lvm/drbd0: Added to device cache
#filters/filter-regex.c:172         /dev/ram0: Skipping (regex)
#device/dev-io.c:487         Opened /dev/lvm/drbd0 RO
#device/dev-io.c:260       /dev/lvm/drbd0: size is 390613280 sectors
#device/dev-io.c:134         /dev/lvm/drbd0: block size is 4096 bytes
#device/dev-io.c:533         Closed /dev/lvm/drbd0
#device/dev-io.c:260       /dev/lvm/drbd0: size is 390613280 sectors
#device/dev-io.c:487         Opened /dev/lvm/drbd0 RO O_DIRECT
#device/dev-io.c:134         /dev/lvm/drbd0: block size is 4096 bytes
#device/dev-io.c:533         Closed /dev/lvm/drbd0
#filters/filter-composite.c:31         Using /dev/lvm/drbd0
#device/dev-io.c:487         Opened /dev/lvm/drbd0 RO O_DIRECT
#device/dev-io.c:134         /dev/lvm/drbd0: block size is 4096 bytes
#label/label.c:160       /dev/lvm/drbd0: lvm2 label detected
[COLOR="Orange"]#cache/lvmcache.c:1298       Duplicate PV IeZ1rKUMhpbLqHwaSMPZ3tafJUWbvy2G on /dev/sda8 - using  /dev/lvm/drbd0[/COLOR]
#device/dev-io.c:533         Closed /dev/lvm/drbd0
#filters/filter-regex.c:172         /dev/ram1: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda1: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram2: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram3: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram4: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram5: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda5: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram6: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda6: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram7: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda7: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram8: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda8: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram9: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram10: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram11: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram12: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram13: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram14: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram15: Skipping (regex)
#regex/matcher.c:269         Matcher built with 29 dfa states
#config/config.c:987       Setting devices/ignore_suspended_devices to 0
#config/config.c:964       Setting devices/cache_dir to /etc/lvm/cache
#config/config.c:987       Setting devices/write_cache_state to 0
#filters/filter-regex.c:172         /dev/ram0: Skipping (regex)
#device/dev-io.c:487         Opened /dev/lvm/drbd0 RO O_DIRECT
#device/dev-io.c:260       /dev/lvm/drbd0: size is 390613280 sectors
#device/dev-io.c:134         /dev/lvm/drbd0: block size is 4096 bytes
#device/dev-io.c:533         Closed /dev/lvm/drbd0
#device/dev-io.c:260       /dev/lvm/drbd0: size is 390613280 sectors
#device/dev-io.c:487         Opened /dev/lvm/drbd0 RO O_DIRECT
#device/dev-io.c:134         /dev/lvm/drbd0: block size is 4096 bytes
#device/dev-io.c:533         Closed /dev/lvm/drbd0
#filters/filter-composite.c:31         Using /dev/lvm/drbd0
#label/label.c:270         Using cached label for /dev/lvm/drbd0
#filters/filter-regex.c:172         /dev/ram1: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda1: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram2: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram3: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram4: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram5: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda5: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram6: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda6: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram7: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda7: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram8: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda8: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram9: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram10: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram11: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram12: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram13: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram14: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram15: Skipping (regex)
#metadata/metadata.c:2668         <backtrace>
#format_text/format-text.c:1920         <backtrace>
#locking/file_locking.c:235       Locking /var/lock/lvm/P_orphans WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/P_orphans:aux WB
#locking/file_locking.c:141         _do_flock /var/lock/lvm/P_orphans WB
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/P_orphans:aux
#device/dev-io.c:487         Opened /dev/lvm/drbd0 RO O_DIRECT
#device/dev-io.c:134         /dev/lvm/drbd0: block size is 4096 bytes
#label/label.c:160       /dev/lvm/drbd0: lvm2 label detected
#label/label.c:160       /dev/lvm/drbd0: lvm2 label detected
#regex/matcher.c:269         Matcher built with 29 dfa states
#config/config.c:987       Setting devices/ignore_suspended_devices to 0
#config/config.c:964       Setting devices/cache_dir to /etc/lvm/cache
#config/config.c:987       Setting devices/write_cache_state to 0
#filters/filter-persistent.c:56     Wiping cache of LVM-capable devices
#device/dev-cache.c:262         /dev/lvm/drbd0: Already in device cache
#filters/filter-regex.c:172         /dev/ram0: Skipping (regex)
#device/dev-io.c:260       /dev/lvm/drbd0: size is 390613280 sectors
#device/dev-io.c:260       /dev/lvm/drbd0: size is 390613280 sectors
#filters/filter-composite.c:31         Using /dev/lvm/drbd0
#label/label.c:160       /dev/lvm/drbd0: lvm2 label detected
#filters/filter-regex.c:172         /dev/ram1: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda1: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram2: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram3: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram4: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram5: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda5: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram6: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda6: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram7: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda7: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram8: Skipping (regex)
#filters/filter-regex.c:172         /dev/sda8: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram9: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram10: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram11: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram12: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram13: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram14: Skipping (regex)
#filters/filter-regex.c:172         /dev/ram15: Skipping (regex)
#metadata/metadata.c:177     Adding physical volume '/dev/lvm/drbd0' to volume group 'iscsivg01'
#format_text/archiver.c:127     Archiving volume group "iscsivg01" metadata (seqno 0).
#metadata/pv_manip.c:296         /dev/lvm/drbd0 0:      0  47683: NULL(0:0)
#device/dev-io.c:533         Closed /dev/lvm/drbd0
#device/dev-io.c:487         Opened /dev/lvm/drbd0 RW O_DIRECT
#device/dev-io.c:134         /dev/lvm/drbd0: block size is 4096 bytes
#format_text/format-text.c:590         Writing iscsivg01 metadata to /dev/lvm/drbd0 at 4608 len 696
#format_text/format-text.c:695         Pre-Committing iscsivg01 metadata (1) to /dev/lvm/drbd0 header at 4096
#format_text/format-text.c:695         Committing iscsivg01 metadata (1) to /dev/lvm/drbd0 header at 4096
#cache/lvmcache.c:1136         lvmcache: /dev/lvm/drbd0: now in VG iscsivg01 with 1 mdas
#cache/lvmcache.c:923         lvmcache: /dev/lvm/drbd0: setting iscsivg01 VGID to B9aqVzzZD3t57nCZt9JEB9jXN5D2eB22
#locking/file_locking.c:74       Unlocking /var/lock/lvm/P_orphans
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/P_orphans
#locking/file_locking.c:74       Unlocking /var/lock/lvm/V_iscsivg01
#locking/file_locking.c:51         _undo_flock /var/lock/lvm/V_iscsivg01
#device/dev-io.c:533         Closed /dev/lvm/drbd0
#format_text/archiver.c:390     Creating volume group backup "/etc/lvm/backup/iscsivg01" (seqno 1).
#format_text/format-text.c:888         Writing iscsivg01 metadata to /etc/lvm/backup/.lvm_piing-node-2_15014_2079890684
#format_text/format-text.c:932         Committing iscsivg01 metadata (1)
#format_text/format-text.c:933         Renaming /etc/lvm/backup/iscsivg01.tmp to /etc/lvm/backup/iscsivg01
  Clustered volume group "iscsivg01" successfully created
  
piing@piing-node-2:~$ sudo pvs
  Skipping clustered volume group iscsivg01
  Skipping volume group iscsivg01
  
piing@piing-node-2:~$ sudo pvscan
  PV /dev/lvm/drbd0   VG iscsivg01   lvm2 [186.26 GiB / 186.26 GiB free]
  Total: 1 [186.26 GiB] / in use: 1 [186.26 GiB] / in no VG: 0 [0   ]
  
piing@piing-node-2:~$ sudo pvdisplay
  Skipping clustered volume group iscsivg01
  Skipping volume group iscsivg01
  
piing@piing-node-2:~$ sudo lvcreate -L 186G -n lun0 iscsivg01 /dev/lvm/drbd0
[COLOR="Red"]  Skipping clustered volume group iscsivg01[/COLOR]
  
piing@piing-node-2:~$ sudo lvcreate -L 186G -n lun0 iscsivg01
[COLOR="Red"]  Skipping clustered volume group iscsivg01[/COLOR]
  
piing@piing-node-2:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
[COLOR="Red"]  Skipping clustered volume group iscsivg01[/COLOR]
  
piing@piing-node-2:~$ sudo vgs
[COLOR="Red"]  Skipping clustered volume group iscsivg01[/COLOR]

piing@piing-node-2:~$ sudo vgremove iscsivg01
[COLOR="Red"]  Skipping clustered volume group iscsivg01[/COLOR]
  


```


Have you ever seen any issue like this? Any clue? Did I miss something here?

Thanks!
Chakrit W.

---


---
title: "cryptsetup fails with &quot;Unable to make device node for 'temporary-cryptsetup-XXXX'&quot;"
date: 2007-04-12
forum: Server Platforms
---

### Post by greencat on 2007-04-12
Hi there,

I've been trying to setup up an encrypted partition using cryptsetup on top of an EVMS managed LVM2 volume on top of a MD RAID array all on a update to date as of posting Feisty, which was an upgrade from Edgy.

Creating a file system on the device with out cryptsetup doing it's bit works just fine.

```

# cryptsetup --verbose  luksFormat  /dev/evms/root
....
Unable to make device node for 'temporary-cryptsetup-5546'
Failed to write to key storage.
Command failed.
```

I have the dm-crypt, aes and sha256 modules loaded.

Syslog shows the following with udev debugging on:
```

Apr 12 11:12:22 mal udevd[2904]: udev_event_run: seq 2508 forked, pid [5745], 'add' 'block', 0 seconds old
Apr 12 11:12:22 mal udevd-event[5745]: run_program: '/sbin/devmap_name 254 27'
Apr 12 11:12:22 mal udevd-event[5745]: run_program: '/sbin/devmap_name' (stdout) 'temporary-cryptsetup-5744'
Apr 12 11:12:22 mal udevd-event[5745]: run_program: '/sbin/devmap_name' returned with status 0
Apr 12 11:12:22 mal udevd-event[5745]: udev_rules_get_name: rule applied, 'dm-27' becomes 'mapper/temporary-cryptsetup-5744'
Apr 12 11:12:22 mal udevd-event[5745]: run_program: 'vol_id --export /dev/.tmp-254-27'
Apr 12 11:12:22 mal vol_id[5747]: volume_id.c:45 probing at offset 0x0, size 0x0
Apr 12 11:12:22 mal vol_id[5747]: lvm.c:49 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x400(1024), len 0x800
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0xc00
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x800
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x800
Apr 12 11:12:22 mal vol_id[5747]: highpoint.c:52 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x1200(4608), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x1400
Apr 12 11:12:22 mal vol_id[5747]: volume_id.c:103 probing at offset 0x0, size 0x0
Apr 12 11:12:22 mal vol_id[5747]: fat.c:161 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x400
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x400
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x11000
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x11000
Apr 12 11:12:22 mal vol_id[5747]: linux_swap.c:46 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0xff6(4086), len 0xa
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x1000
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x2
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x2
Apr 12 11:12:22 mal vol_id[5747]: xfs.c:48 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x200
Apr 12 11:12:22 mal vol_id[5747]: ext.c:78 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x400(1024), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x600
Apr 12 11:12:22 mal vol_id[5747]: reiserfs.c:63 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x10000(65536), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x10200
Apr 12 11:12:22 mal vol_id[5747]: jfs.c:48 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x8000(32768), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x8200
Apr 12 11:12:22 mal vol_id[5747]: udf.c:75 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x8000(32768), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x8200
Apr 12 11:12:22 mal vol_id[5747]: iso9660.c:62 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x8000(32768), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x8200
Apr 12 11:12:22 mal vol_id[5747]: hfs.c:189 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x400(1024), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x600
Apr 12 11:12:22 mal vol_id[5747]: ufs.c:178 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x800
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x800
Apr 12 11:12:22 mal vol_id[5747]: ntfs.c:108 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x200
Apr 12 11:12:22 mal vol_id[5747]: cramfs.c:48 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x200
Apr 12 11:12:22 mal vol_id[5747]: romfs.c:40 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x200
Apr 12 11:12:22 mal vol_id[5747]: hpfs.c:41 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x2000(8192), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x2200
Apr 12 11:12:22 mal vol_id[5747]: sysv.c:98 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x200(512), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x400
Apr 12 11:12:22 mal vol_id[5747]: minix.c:49 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x400(1024), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x600
Apr 12 11:12:22 mal vol_id[5747]: ocfs.c:135 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x0(0), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x200
Apr 12 11:12:22 mal vol_id[5747]: ocfs.c:173 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x400(1024), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x600
Apr 12 11:12:22 mal vol_id[5747]: vxfs.c:40 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x200(512), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x400
Apr 12 11:12:22 mal vol_id[5747]: squashfs.c:39 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x200(512), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x400
Apr 12 11:12:22 mal vol_id[5747]: netware.c:85 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x1000(4096), len 0x200
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x1200
Apr 12 11:12:22 mal vol_id[5747]: gfs.c:81 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x10000(65536), len 0xe0
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x100e0
Apr 12 11:12:22 mal vol_id[5747]: gfs.c:81 probing at offset 0x0
Apr 12 11:12:22 mal vol_id[5747]: util.c:183 get buffer off 0x10000(65536), len 0xe0
Apr 12 11:12:22 mal vol_id[5747]: util.c:196 read sbbuf len:0x100e0
Apr 12 11:12:22 mal udevd-event[5745]: run_program: '/lib/udev/vol_id' (stderr) '/dev/.tmp-254-27: unknown volume type'
Apr 12 11:12:22 mal udevd-event[5745]: run_program: '/lib/udev/vol_id' returned with status 4
Apr 12 11:12:22 mal udevd-event[5745]: udev_db_get_device: no db file to read /dev/.udev/db/%2fblock%2fdm-27: No such file or directory
Apr 12 11:12:22 mal udevd-event[5745]: udev_node_add: creating device node '/dev/mapper/temporary-cryptsetup-5744', major = '254', minor = '27', mode = '0660', uid = '0', gid = '6'
Apr 12 11:12:22 mal udevd-event[5745]: name_index: creating index: '/dev/.udev/names/mapper%2ftemporary-cryptsetup-5744/%2fblock%2fdm-27'
Apr 12 11:12:22 mal udevd-event[5745]: run_program: 'watershed /sbin/evms_activate'
Apr 12 11:12:23 mal udevd-event[5745]: run_program: '/lib/udev/watershed' (stdout) 'Engine: The plug-in SWAPFS in module /lib/evms/2.5.5/swap-1.1.13.so failed to load.  The plug-in's setup_evms_plugin() function failed with error code 38: Function not implemented.'
Apr 12 11:12:23 mal udevd-event[5745]: run_program: '/lib/udev/watershed' returned with status 0
Apr 12 11:12:23 mal udevd-event[5745]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Apr 12 11:12:23 mal udevd-event[5745]: udev_event_run: seq 2508 finished
Apr 12 11:12:23 mal udevd[2904]: udev_done: seq 2508, pid [5745] exit with 0, 1 seconds old
Apr 12 11:12:23 mal udevd[2904]: udev_event_run: seq 2509 forked, pid [5769], 'change' 'block', 1 seconds old
Apr 12 11:12:23 mal udevd-event[5769]: run_program: '/sbin/devmap_name 254 27'
Apr 12 11:12:23 mal udevd-event[5769]: run_program: '/sbin/devmap_name' (stderr) 'Command failed'
Apr 12 11:12:23 mal udevd-event[5769]: run_program: '/sbin/devmap_name' returned with status 1
Apr 12 11:12:23 mal udevd-event[5769]: udev_rules_get_name: rule applied, 'dm-27' becomes ''
Apr 12 11:12:23 mal udevd-event[5769]: run_program: 'vol_id --export /dev/.tmp-254-27'
Apr 12 11:12:23 mal udevd-event[5769]: run_program: '/lib/udev/vol_id' (stderr) '/dev/.tmp-254-27: error open volume'
Apr 12 11:12:23 mal udevd-event[5769]: run_program: '/lib/udev/vol_id' returned with status 2
Apr 12 11:12:23 mal udevd-event[5769]: udev_device_event: device node creation supressed
Apr 12 11:12:23 mal udevd-event[5769]: run_program: 'watershed /sbin/evms_activate'
Apr 12 11:12:25 mal udevd-event[5769]: run_program: '/lib/udev/watershed' (stdout) 'Engine: The plug-in SWAPFS in module /lib/evms/2.5.5/swap-1.1.13.so failed to load.  The plug-in's setup_evms_plugin() function failed with error code 38: Function not implemented.'
Apr 12 11:12:25 mal udevd-event[5769]: run_program: '/lib/udev/watershed' returned with status 0
Apr 12 11:12:25 mal udevd-event[5769]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Apr 12 11:12:25 mal udevd-event[5769]: udev_event_run: seq 2509 finished
Apr 12 11:12:25 mal udevd[2904]: udev_done: seq 2509, pid [5769] exit with 0, 3 seconds old
Apr 12 11:12:25 mal udevd[2904]: udev_event_run: seq 2510 forked, pid [5796], 'remove' 'block', 3 seconds old
Apr 12 11:12:25 mal udevd-event[5796]: udev_db_get_device: found a symlink as db file
Apr 12 11:12:25 mal udevd-event[5796]: name_index: removing index: '/dev/.udev/names/mapper%2ftemporary-cryptsetup-5744/%2fblock%2fdm-27'
Apr 12 11:12:25 mal udevd-event[5796]: udev_node_remove: removing device node '/dev/mapper/temporary-cryptsetup-5744'
Apr 12 11:12:25 mal udevd-event[5796]: pass_env_to_socket: passed -1 bytes to socket '/org/kernel/udev/monitor', 
Apr 12 11:12:25 mal udevd-event[5796]: udev_event_run: seq 2510 finished
Apr 12 11:12:25 mal udevd[2904]: udev_done: seq 2510, pid [5796] exit with 0, 3 seconds old

```

I'm at a complete loss as to what to try next, and searching around doesn't show this particular error message up. Any help would be greatly appreciated.

---


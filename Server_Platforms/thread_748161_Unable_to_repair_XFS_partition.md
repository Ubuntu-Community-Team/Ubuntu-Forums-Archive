---
title: "Unable to repair XFS partition"
date: 2008-04-07
forum: Server Platforms
---

### Post by jimbolaya on 2008-04-07
I'm running  Feisty on my server and I can no longer repair an XFS partition.  My XFS partition was on a RAID 1 with 2 500MB disks hooked to a SiI3114 SATA card.  If there was heavy disk I/O on the RAID volume, I would get I/O errors.  I'd have to reboot to restore the RAID volume.  The SiI card didn't seem to like the disks very well and sometimes wouldn't recognize them.

Unfortunately, I haven't been able to read from the partition for a few days now.  I "dd_rescue"d the data to another drive with no errors that I've attached with a USB-SATA cable.  Unfortunately, I get the same errors.

Here's what I've tried so far:

```

xfs_repair /dev/sdc1
        - creating 2 worker thread(s)
Phase 1 - find and verify superblock...
        - reporting progress in intervals of 15 minutes
Phase 2 - using internal log
        - zero log...
ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_repair.  If you are unable to mount the filesystem, then use
the -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.
```

But if I run "xfs_repair -n /dev/sdc1" it gives me a whole list of things it needs to do.  If I mount it, I get this in dmesg:

```
577324.020000] Starting XFS recovery on filesystem: sdc1 (logdev: internal)
[577324.270000] Filesystem "sdc1": XFS internal error xfs_btree_check_sblock at 
line 334 of file fs/xfs/xfs_btree.c.  Caller 0xf909a32b
[577324.270000]  [<f908710b>] xfs_btree_check_sblock+0x5b/0xf0 [xfs]
[577324.270000]  [<f909a32b>] xfs_inobt_lookup+0x1cb/0x470 [xfs]
[577324.270000]  [<f909a32b>] xfs_inobt_lookup+0x1cb/0x470 [xfs]
[577324.270000]  [<f90c28a8>] kmem_zone_zalloc+0x28/0x60 [xfs]
[577324.270000]  [<f90993ff>] xfs_difree+0x25f/0x610 [xfs]
[577324.270000]  [<f90b6d4f>] xfs_trans_read_buf+0x19f/0x360 [xfs]
[577324.270000]  [<f909fe87>] xfs_ifree+0x597/0xc70 [xfs]
[577324.270000]  [<f90c281e>] kmem_zone_alloc+0x4e/0xb0 [xfs]
[577324.270000]  [<f90c28a8>] kmem_zone_zalloc+0x28/0x60 [xfs]
[577324.270000]  [<f90b7191>] xfs_trans_ijoin+0x31/0x70 [xfs]
[577324.270000]  [<f90c15f1>] xfs_inactive+0x4c1/0xb10 [xfs]
[577324.270000]  [<c01583bc>] find_or_create_page+0x1c/0xb0
[577324.270000]  [<f90c6417>] xfs_buf_get_flags+0x2a7/0x4c0 [xfs]
[577324.270000]  [<f90c664c>] xfs_buf_read_flags+0x1c/0x90 [xfs]
[577324.270000]  [<f90c5241>] xfs_buf_offset+0x31/0x40 [xfs]
[577324.270000]  [<f909f8cd>] xfs_itobp+0x20d/0x230 [xfs]
[577324.270000]  [<f90cca17>] xfs_fs_clear_inode+0x77/0xc0 [xfs]
[577324.270000]  [<c018b693>] clear_inode+0x93/0x140
[577324.270000]  [<c015f707>] truncate_inode_pages+0x17/0x20
[577324.270000]  [<c018b84c>] generic_delete_inode+0x10c/0x120
[577324.270000]  [<c018addc>] iput+0x5c/0x70
[577324.270000]  [<f90ad88b>] xlog_recover_process_iunlinks+0x58b/0x5b0 [xfs]
[577324.270000]  [<f90a2793>] xfs_iread+0x173/0x710 [xfs]
[577324.270000]  [<f90adc46>] xlog_recover_finish+0x396/0x460 [xfs]
[577324.270000]  [<f90633e7>] xfs_rtmount_inodes+0xb7/0xd0 [xfs]
[577324.270000]  [<f90b2c2a>] xfs_mountfs+0xdfa/0xfc0 [xfs]
[577324.270000]  [<c01eed2d>] _atomic_dec_and_lock+0x3d/0x70
[577324.270000]  [<f90ba2eb>] xfs_mount+0xa3b/0xb50 [xfs]
[577324.270000]  [<f905f8d0>] xfs_qm_parseargs+0x0/0x2b0 [xfs]
[577324.270000]  [<f90b98b0>] xfs_mount+0x0/0xb50 [xfs]
[577324.270000]  [<f90cd022>] vfs_mount+0x22/0x30 [xfs]
[577324.270000]  [<f90cce58>] xfs_fs_fill_super+0x78/0x1e0 [xfs]
[577324.270000]  [<c01f36af>] snprintf+0x1f/0x30
[577324.270000]  [<c01b29b2>] disk_name+0x92/0xc0
[577324.270000]  [<c017a139>] get_sb_bdev+0xf9/0x130
[577324.270000]  [<f90cc070>] xfs_fs_get_sb+0x20/0x30 [xfs]
[577324.270000]  [<f90ccde0>] xfs_fs_fill_super+0x0/0x1e0 [xfs]
[577324.270000]  [<c0179ab6>] vfs_kern_mount+0xb6/0x130
[577324.270000]  [<c0179b89>] do_kern_mount+0x39/0x60
[577324.270000]  [<c018ea1a>] do_mount+0x2ea/0x700
[577324.270000]  [<f89336b4>] sd_release+0x44/0x90 [sd_mod]
[577324.270000]  [<c0181ab3>] do_path_lookup+0x83/0x1c0
[577324.270000]  [<f88ab10e>] scsi_device_put+0x3e/0x40 [scsi_mod]
[577324.270000]  [<c015c647>] __alloc_pages+0x57/0x310
[577324.270000]  [<c02f5944>] error_code+0x7c/0x84
[577324.270000]  [<c018d9d0>] copy_mount_options+0x40/0x150
[577324.280000]  [<c018eea7>] sys_mount+0x77/0xc0
[577324.280000]  [<c01031b4>] sysenter_past_esp+0x69/0x9d
[577324.280000]  =======================
[577324.280000] xfs_difree: xfs_inobt_lookup_le returned()  an error 117 on sdc1
.  Returning error.
[577324.280000] xfs_inactive:   xfs_ifree() returned an error = 117 on sdc1
[577324.280000] xfs_force_shutdown(sdc1,0x1) called from line 1780 of file fs/xf
s/xfs_vnodeops.c.  Return address = 0xf90cd29c
[577324.280000] Filesystem "sdc1": I/O Error Detected.  Shutting down filesystem
: sdc1
[577324.280000] Please umount the filesystem, and rectify the problem(s)
[577324.360000] Ending XFS recovery on filesystem: sdc1 (logdev: internal)
```

I can't even run xfs_check on it, since I get I/O errors if the partition is mounted.  I don't get I/O errors if I try to access the partition directly (using xfs_repair or even xfs_logprint).  I have no idea where the I/O error  is coming from.  Is this a  bug in the XFS code?  Or is my data really hosed?

James

---

### Post by ikonia on 2008-04-07
We are missing a few bits of info here.

Questions:


1.) you say the disk is a raid1 volume, is this a hardware or software mirrored solution

2.) if it's raid1, then the 2 disks are mirrored, so is the corruption on both disks or just one

3.) is the error complaining about the raid volume being corrupted, (eg: software mirror /dev/md0) or the physical devices under the mirror ?

More info please and we can move this forward.

---

### Post by jimbolaya on 2008-04-07
1) This is a software RAID.  A typical scenario would be that the SATA card would stop recognizing one of the disks.  Then, when the server rebooted, it would only recognize one of the two mirrors.  I would then re-add the mirror that it couldn't recognize and it would rebuild the RAID.

2)  I don't know if the corruption was on one or the other.  I'm not sure how to figure that out (it wasn't obvious to me from the logs).

3)  It's complaining about corruption on /dev/md0.  The message is essentially the same as above, but instead of /dev/sdc1 it's /dev/md0.

---


---
title: "errors during bootup from block./genhd.c:1573"
date: 2013-01-02
forum: Server Platforms
---

### Post by MakOwner on 2013-01-02
I found this error in dmesg after the last boot.
Immediately before this message I see the mount of an external software RAID array of eSATA disks.  The filesystem mounts and fscks run with no issue - this is the only indication of problem.  This occurred after the last kernel update and reboot.

This is Dell PE850 hardware with a non-dell Silicon Image Port Multiplier compatible PCIe eSATA card installed.


Can anyone hit me with a clue on this?

```

[   28.322876] ------------[ cut here ]------------
[   28.322894] WARNING: at /build/buildd/linux-3.2.0/block/genhd.c:1573 disk_clear_events+0x119/0x130()
[   28.322899] Hardware name: PowerEdge 850
[   28.322903] Modules linked in: dcdbas(+) psmouse xgifb(C) serio_raw bonding floppy(+) shpchp i3000_edac edac_core mac_hid lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov aacraid sata_sil24 tg3 raid6_pq async_tx raid1 raid0 multipath linear
[   28.322955] Pid: 800, comm: blkid Tainted: G         C   3.2.0-35-generic #55-Ubuntu
[   28.322960] Call Trace:
[   28.322972]  [<ffffffff81067f0f>] warn_slowpath_common+0x7f/0xc0
[   28.322981]  [<ffffffff81067f6a>] warn_slowpath_null+0x1a/0x20
[   28.322991]  [<ffffffff812fda59>] disk_clear_events+0x119/0x130
[   28.323001]  [<ffffffff811b04f7>] check_disk_change+0x37/0x80
[   28.323010]  [<ffffffff814451ed>] sd_open+0xad/0x1e0
[   28.323018]  [<ffffffff811b1cb7>] __blkdev_get+0x2f7/0x460
[   28.323028]  [<ffffffff8129e72c>] ? security_inode_permission+0x1c/0x30
[   28.323037]  [<ffffffff811b1e7e>] blkdev_get+0x5e/0x1e0
[   28.323045]  [<ffffffff811b205d>] blkdev_open+0x5d/0x80
[   28.323053]  [<ffffffff811770a0>] __dentry_open+0x290/0x360
[   28.323060]  [<ffffffff811b2000>] ? blkdev_get+0x1e0/0x1e0
[   28.323070]  [<ffffffff8129e72c>] ? security_inode_permission+0x1c/0x30
[   28.323078]  [<ffffffff81184daa>] ? inode_permission+0x4a/0x110
[   28.323085]  [<ffffffff8117771d>] vfs_open+0x3d/0x40
[   28.323092]  [<ffffffff81178620>] nameidata_to_filp+0x40/0x50
[   28.323100]  [<ffffffff811875e8>] do_last+0x3f8/0x730
[   28.323109]  [<ffffffff81188cc1>] path_openat+0xd1/0x3f0
[   28.323115]  [<ffffffff81184605>] ? putname+0x35/0x50
[   28.323123]  [<ffffffff81189063>] ? user_path_at_empty+0x63/0xa0
[   28.323130]  [<ffffffff81189102>] do_filp_open+0x42/0xa0
[   28.323140]  [<ffffffff8131acc1>] ? strncpy_from_user+0x31/0x40
[   28.323148]  [<ffffffff8118444a>] ? do_getname+0x10a/0x180
[   28.323159]  [<ffffffff8165cfde>] ? _raw_spin_lock+0xe/0x20
[   28.323170]  [<ffffffff81196417>] ? alloc_fd+0xf7/0x150
[   28.323177]  [<ffffffff81178728>] do_sys_open+0xf8/0x240
[   28.323185]  [<ffffffff81178890>] sys_open+0x20/0x30
[   28.323193]  [<ffffffff816655c2>] system_call_fastpath+0x16/0x1b
[   28.323199] ---[ end trace 985a0aac0015fcc1 ]---

```


[http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2012-04/18307/%28Bug-754691%29-Re-WARNING-at-build-buildd-linux-2.6.38-block-genhd.c-1556-disk_clear_events-0x10a-0x120%28%29.html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2012-04/18307/%28Bug-754691%29-Re-WARNING-at-build-buildd-linux-2.6.38-block-genhd.c-1556-disk_clear_events-0x10a-0x120%28%29.html)

My google-fu is not that strong, but it looks like this has been a known issue for a long time.

---

### Post by MakOwner on 2013-01-03
Hopefully this link works, it points to a thread in the Server forum.

[http://ubuntuforums.org/showthread.php?t=2100775](http://ubuntuforums.org/showthread.php?t=2100775)

---

### Post by howefield on 2013-01-03
Threads merged,

Feel free to bump your thread once every 24 hours or so in the event of a lack of response.

---

### Post by MakOwner on 2013-03-01
> **howefield said:**
> Threads merged,

Feel free to bump your thread once every 24 hours or so in the event of a lack of response.

This thread is the first result in Google -- with no response to it.

---


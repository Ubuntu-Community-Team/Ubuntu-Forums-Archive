---
title: "[SOLVED] Server lockups, please help?"
date: 2008-10-22
forum: Server Platforms
---

### Post by linuxpenguin on 2008-10-22
My server has recently decided to start taking naps suddenly and unexpectedly.  On the webpage side I see a nice ugly message about an incorrect key for a SQL table.

Yesterday I checked all the tables and there were a few errors, but all got fixed.  Then today this happened again.  I was positive this whole time that the SQL was not the problem, because it's always working fine for quite a while once I reboot it.

I was thinking that the thing was actually completely locking up until just now when it happened to lock up while I was connected through SSH to look at logs for any hints.  I found NOTHING conclusive - but wouldn't you know, it locked up while I was looking.  Rather than reboot I figured I'd see if it came back.  After a couple minutes, my session came back responsive as ever.  Then I tried to run apt-get update (as root) and got an I/O error.

Fortunately though I am at least able to get the output of dmesg, and here she be.  I'm sorry for posting all of this here, but I'm at somewhat of a loss as to what I should do.

```
[   42.910404] ReiserFS: sdb1: checking transaction log (sdb1)
[   46.299828] ReiserFS: sdb1: replayed 418 transactions in 3 seconds
[   46.300166] ReiserFS: sdb1: Using r5 hash to sort names
[   46.876352] ip_tables: (C) 2000-2006 Netfilter Core Team
[   49.744080] No dock devices found.
[   51.729807] audit(1224713329.055:2): type=1502 operation="capable" name="sys_resource" pid=4757 profile="/usr/sbin/mysqld" namespace="default"
[   52.006241] eth0: no IPv6 routers present
[ 7053.962378] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 7053.962470] ata1.01: cmd ca/00:08:af:69:44/00:00:00:00:00/f0 tag 0 dma 4096 out
[ 7053.962474]          res 40/00:78:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[ 7053.962531] ata1.01: status: { DRDY }
[ 7058.987392] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 7063.952745] ata1: device not ready (errno=-16), forcing hardreset
[ 7063.952766] ata1: soft resetting link
[ 7069.137356] ata1: port is slow to respond, please be patient (Status 0x90)
[ 7073.983773] ata1: SRST failed (errno=-16)
[ 7073.983833] ata1: soft resetting link
[ 7104.149643] ata1.01: qc timeout (cmd 0xec)
[ 7104.149669] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7104.149678] ata1.01: revalidation failed (errno=-5)
[ 7104.149730] ata1: failed to recover some devices, retrying in 5 secs
[ 7109.147375] ata1: soft resetting link
[ 7114.334556] ata1: port is slow to respond, please be patient (Status 0x90)
[ 7119.182633] ata1: SRST failed (errno=-16)
[ 7119.182694] ata1: soft resetting link
[ 7149.348494] ata1.01: qc timeout (cmd 0xec)
[ 7149.348520] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7149.348529] ata1.01: revalidation failed (errno=-5)
[ 7149.348581] ata1: failed to recover some devices, retrying in 5 secs
[ 7154.346225] ata1: soft resetting link
[ 7159.533404] ata1: port is slow to respond, please be patient (Status 0x90)
[ 7164.381485] ata1: SRST failed (errno=-16)
[ 7164.381544] ata1: soft resetting link
[ 7194.547425] ata1.01: qc timeout (cmd 0xec)
[ 7194.547450] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7194.547459] ata1.01: revalidation failed (errno=-5)
[ 7194.547512] ata1.01: disabled
[ 7195.080810] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x40)
[ 7195.080827] ata1.00: revalidation failed (errno=-5)
[ 7195.080875] ata1: failed to recover some devices, retrying in 5 secs
[ 7200.073784] ata1: soft resetting link
[ 7205.270933] ata1: port is slow to respond, please be patient (Status 0x90)
[ 7210.059162] ata1: SRST failed (errno=-16)
[ 7210.059222] ata1: soft resetting link
[ 7240.225023] ata1.00: qc timeout (cmd 0xec)
[ 7240.225048] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7240.225057] ata1.00: revalidation failed (errno=-5)
[ 7240.225111] ata1: failed to recover some devices, retrying in 5 secs
[ 7245.222755] ata1: soft resetting link
[ 7250.410013] ata1: port is slow to respond, please be patient (Status 0x90)
[ 7255.258011] ata1: SRST failed (errno=-16)
[ 7255.258069] ata1: soft resetting link
[ 7285.434249] ata1.00: qc timeout (cmd 0xec)
[ 7285.434275] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7285.434284] ata1.00: revalidation failed (errno=-5)
[ 7285.434336] ata1.00: disabled
[ 7286.122117] ata1: soft resetting link
[ 7291.309436] ata1: port is slow to respond, please be patient (Status 0x90)
[ 7296.157439] ata1: SRST failed (errno=-16)
[ 7296.157496] ata1: soft resetting link
[ 7296.329512] ata1: EH complete
[ 7296.329592] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329605] end_request: I/O error, dev sda, sector 17586855
[ 7296.329617] Buffer I/O error on device sda1, logical block 2198349
[ 7296.329660] lost page write due to I/O error on sda1
[ 7296.329702] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329711] end_request: I/O error, dev sdb, sector 4483503
[ 7296.329741] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329752] end_request: I/O error, dev sda, sector 55836767
[ 7296.329781] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329790] end_request: I/O error, dev sdb, sector 37228439
[ 7296.329815] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329823] end_request: I/O error, dev sda, sector 19152959
[ 7296.329848] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329856] end_request: I/O error, dev sdb, sector 37229127
[ 7296.329878] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329889] end_request: I/O error, dev sda, sector 17603799
[ 7296.329894] Buffer I/O error on device sda1, logical block 2200467
[ 7296.329934] lost page write due to I/O error on sda1
[ 7296.329954] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.329963] end_request: I/O error, dev sda, sector 18476735
[ 7296.329971] Buffer I/O error on device sda1, logical block 2309584
[ 7296.330010] lost page write due to I/O error on sda1
[ 7296.330031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.330039] end_request: I/O error, dev sda, sector 18474503
[ 7296.330047] Buffer I/O error on device sda1, logical block 2309305
[ 7296.330086] lost page write due to I/O error on sda1
[ 7296.330271] EXT3-fs error (device sda1): ext3_get_inode_loc: unable to read inode block - inode=3489860, block=6979588
[ 7296.330356] Aborting journal on device sda1.
[ 7296.330434] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [5 2845 0x0 SD]
[ 7296.330676] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1196144 offset 0
[ 7296.330751] Remounting filesystem read-only
[ 7296.330861] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [5 4517 0x0 SD]
[ 7296.331129] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331141] end_request: I/O error, dev sdb, sector 35599
[ 7296.331150] Buffer I/O error on device sdb1, logical block 4442
[ 7296.331189] lost page write due to I/O error on sdb1
[ 7296.331201] Buffer I/O error on device sdb1, logical block 4443
[ 7296.331237] lost page write due to I/O error on sdb1
[ 7296.331265] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331273] end_request: I/O error, dev sda, sector 12423
[ 7296.331278] Buffer I/O error on device sda1, logical block 1545
[ 7296.331317] lost page write due to I/O error on sda1
[ 7296.331342] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331350] end_request: I/O error, dev sdb, sector 6727919
[ 7296.331375] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331383] end_request: I/O error, dev sda, sector 63
[ 7296.331391] Buffer I/O error on device sda1, logical block 0
[ 7296.331429] lost page write due to I/O error on sda1
[ 7296.331450] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331458] end_request: I/O error, dev sdb, sector 37229127
[ 7296.331479] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331488] end_request: I/O error, dev sda, sector 17347015
[ 7296.331495] Buffer I/O error on device sda1, logical block 2168369
[ 7296.331534] lost page write due to I/O error on sda1
[ 7296.331551] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331560] end_request: I/O error, dev sda, sector 17347591
[ 7296.331568] Buffer I/O error on device sda1, logical block 2168441
[ 7296.331607] lost page write due to I/O error on sda1
[ 7296.331628] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331636] end_request: I/O error, dev sda, sector 17347639
[ 7296.331657] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331665] end_request: I/O error, dev sda, sector 17365623
[ 7296.331689] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331698] end_request: I/O error, dev sda, sector 17586855
[ 7296.331718] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331727] end_request: I/O error, dev sda, sector 17603799
[ 7296.331744] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.331752] end_request: I/O error, dev sda, sector 18476735
[ 7296.331785] __journal_remove_journal_head: freeing b_committed_data
[ 7296.331810] __journal_remove_journal_head: freeing b_committed_data
[ 7296.331824] __journal_remove_journal_head: freeing b_committed_data
[ 7296.331832] WARNING: at /build/buildd/linux-2.6.24/fs/buffer.c:1169 mark_buffer_dirty()
[ 7296.331843] Pid: 2479, comm: kjournald Not tainted 2.6.24-21-server #1
[ 7296.331922]  [<c01bc2e4>] mark_buffer_dirty+0x74/0x90
[ 7296.331980]  [<f0211258>] __journal_unfile_buffer+0x8/0x20 [jbd]
[ 7296.332021]  [<f0211331>] journal_refile_buffer+0x31/0x80 [jbd]
[ 7296.332063]  [<f0213470>] journal_commit_transaction+0x8a0/0xd90 [jbd]
[ 7296.332191]  [<c013b517>] lock_timer_base+0x27/0x60
[ 7296.332232]  [<c013b595>] try_to_del_timer_sync+0x45/0x50
[ 7296.332277]  [<f0216740>] kjournald+0xa0/0x200 [jbd]
[ 7296.332335]  [<c0145ea0>] autoremove_wake_function+0x0/0x40
[ 7296.332381]  [<f02166a0>] kjournald+0x0/0x200 [jbd]
[ 7296.332409]  [<c0145be2>] kthread+0x42/0x70
[ 7296.332418]  [<c0145ba0>] kthread+0x0/0x70
[ 7296.332439]  [<c0108ffb>] kernel_thread_helper+0x7/0x10
[ 7296.332488]  =======================
[ 7296.332497] __journal_remove_journal_head: freeing b_committed_data
[ 7296.332513] __journal_remove_journal_head: freeing b_frozen_data
[ 7296.332520] __journal_remove_journal_head: freeing b_frozen_data
[ 7296.332525] __journal_remove_journal_head: freeing b_frozen_data
[ 7296.332542] journal commit I/O error
[ 7296.333421] Remounting filesystem read-only
[ 7296.333575] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [5 4533 0x0 SD]
[ 7296.333740] REISERFS: abort (device sdb1): Journal write error in flush_commit_list
[ 7296.333802] REISERFS: Aborting journal for filesystem on sdb1
[ 7296.334244] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [14312 397 0x0 SD]
[ 7296.334436] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334448] end_request: I/O error, dev sda, sector 63
[ 7296.334490] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334502] end_request: I/O error, dev sdb, sector 6727919
[ 7296.334526] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334535] end_request: I/O error, dev sda, sector 17039615
[ 7296.334556] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334565] end_request: I/O error, dev sdb, sector 4483503
[ 7296.334585] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334597] end_request: I/O error, dev sda, sector 17039743
[ 7296.334617] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334626] end_request: I/O error, dev sda, sector 17123607
[ 7296.334646] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334655] end_request: I/O error, dev sda, sector 17147679
[ 7296.334672] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334681] end_request: I/O error, dev sda, sector 17236815
[ 7296.334701] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334709] end_request: I/O error, dev sda, sector 17301567
[ 7296.334730] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334738] end_request: I/O error, dev sda, sector 17373135
[ 7296.334759] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334767] end_request: I/O error, dev sda, sector 17563711
[ 7296.334787] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334796] end_request: I/O error, dev sda, sector 18350143
[ 7296.334817] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334825] end_request: I/O error, dev sda, sector 18472975
[ 7296.334849] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334857] end_request: I/O error, dev sda, sector 63963199
[ 7296.334879] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.334887] end_request: I/O error, dev sda, sector 64045119
[ 7296.337037] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.337054] end_request: I/O error, dev sdb, sector 37293575
[ 7296.337125] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [14312 397 0x0 SD]
[ 7296.337404] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.337413] end_request: I/O error, dev sdb, sector 6727919
[ 7296.337619] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [14312 397 0x0 SD]
[ 7296.337757] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.337767] end_request: I/O error, dev sdb, sector 6727919
[ 7296.337901] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7296.337913] end_request: I/O error, dev sdb, sector 37293575
[ 7296.347072] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [14312 397 0x0 SD]
[ 7301.315085] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7301.315110] end_request: I/O error, dev sda, sector 71
[ 7301.315118] printk: 35 messages suppressed.
[ 7301.315127] Buffer I/O error on device sda1, logical block 1
[ 7301.315178] lost page write due to I/O error on sda1
[ 7301.315216] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7301.315225] end_request: I/O error, dev sda, sector 17039431
[ 7301.315248] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7301.315257] end_request: I/O error, dev sda, sector 17039447
[ 7301.315277] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7301.315286] end_request: I/O error, dev sda, sector 17039463
[ 7301.315306] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7301.315315] end_request: I/O error, dev sda, sector 17039487
[ 7301.315336] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7301.315344] end_request: I/O error, dev sda, sector 17039511
[ 7301.315365] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7301.315377] end_request: I/O error, dev sda, sector 17039567
[ 7326.263470] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7326.263495] end_request: I/O error, dev sdb, sector 4472895
[ 7326.263503] printk: 9 messages suppressed.
[ 7326.263511] Buffer I/O error on device sdb1, logical block 559104
[ 7326.263563] lost page write due to I/O error on sdb1
[ 7331.251193] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7331.251221] end_request: I/O error, dev sdb, sector 4483503
[ 7331.251233] Buffer I/O error on device sdb1, logical block 560430
[ 7331.251283] lost page write due to I/O error on sdb1
[ 7338.126507] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.126534] end_request: I/O error, dev sda, sector 16793679
[ 7338.128109] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.128130] end_request: I/O error, dev sda, sector 16781415
[ 7338.131745] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.131984] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.131997] end_request: I/O error, dev sda, sector 16781415
[ 7338.132458] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.133175] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.133188] end_request: I/O error, dev sda, sector 56099039
[ 7338.134699] EXT3-fs error (device sda1): ext3_get_inode_loc: unable to read inode block - inode=3506782, block=7012372
[ 7338.135815] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.135830] end_request: I/O error, dev sda, sector 16781415
[ 7338.137977] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.138184] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.138193] end_request: I/O error, dev sda, sector 16781415
[ 7338.138598] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.139368] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.139380] end_request: I/O error, dev sda, sector 16781415
[ 7338.140805] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.140965] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.140974] end_request: I/O error, dev sda, sector 16781415
[ 7338.141277] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.141834] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.141846] end_request: I/O error, dev sda, sector 16781415
[ 7338.143019] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.143210] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.143223] end_request: I/O error, dev sda, sector 16781415
[ 7338.143581] EXT3-fs error (device sda1): ext3_find_entry: reading directory #1048583 offset 0
[ 7338.144403] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.144416] end_request: I/O error, dev sda, sector 56099039
[ 7338.146067] EXT3-fs error (device sda1): ext3_get_inode_loc: unable to read inode block - inode=3506782, block=7012372
[ 7338.146287] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 7338.146300] end_request: I/O error, dev sda, sector 56099039
[ 7338.146738] EXT3-fs error (device sda1): ext3_get_inode_loc: unable to read inode block - inode=3506782, block=7012372
root@webnet:/var/log#

```

Knowing what I do about Linux and computers, I can deduce that this means that basically, my hard drives are now read-only (until/unless I reboot).

But what I don't know is, what should/can I do?  It's not a bad install - the server's been up for a while now - and the whole system hasn't been in use all that long, so I don't see how the problem could be the hardware.  What can I do to figure out just what caused this?  Any help would be appreciated.

One thing I was going to try was to disable SMP but I can't for the life of me remember - how do you do that?  I tried to search it on the forums but couldn't really find the answer.

Just for reference - here's the setup:
Ubuntu 8.04 Hardy running MySQL, PHP, LightTPD (all from standard Ubuntu repo's)
768(IIRC) MB RAM
2.66GHz Pentium 4 (NO Hyperthreading)

I think I should also add that these are NOT SATA drives - they just are named as though they were.  I think the motherboard can handle both, and so that may be why it's calling them that way.

---

### Post by lykwydchykyn on 2008-10-22
I think you need to run a badblocks scan on the drive.  Buffer I/O errors are not a happy thing.  Also check your SMART readings on the drive.

```

badblocks -v /dev/sda
smartctl --all /dev/sda

```

You may need to install smartmontools from the repos to do that second one.

And get a good backup!

---

### Post by linuxpenguin on 2008-10-22
Nope, everything looks good.  No bad blocks, and only one SMART error.
```
root@webnet:/home/scott# badblocks -v /dev/sda
Checking blocks 0 to 39082679
Checking for bad blocks (read-only test): done
Pass completed, 0 bad blocks found.
root@webnet:/home/scott# smartctl --all /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST340014A
Serial Number:    5JX621HP
Firmware Version: 3.06
User Capacity:    40,020,664,320 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Wed Oct 22 23:38:22 2008 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 ( 430) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   072   055   006    Pre-fail  Always       -       9365009
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       6
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   087   060   030    Pre-fail  Always       -       522272690
  9 Power_On_Hours          0x0032   077   077   000    Old_age   Always       -       20521
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       452
194 Temperature_Celsius     0x0022   031   061   000    Old_age   Always       -       31
195 Hardware_ECC_Recovered  0x001a   072   054   000    Old_age   Always       -       9365009
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 1
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1 occurred at disk power-on lifetime: 16471 hours (686 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 00 00 00 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 da 01 00 00 00 e0 00      00:01:14.967  READ DMA
  b0 da 00 01 4f c2 a0 00      00:01:14.931  SMART RETURN STATUS
  e3 03 00 01 10 00 a0 00      00:01:14.860  IDLE
  91 03 3f 01 10 00 ef 00      00:02:00.181  INITIALIZE DEVICE PARAMETERS [OBS-6]
  c6 03 10 01 a5 5a a0 00      00:02:00.009  SET MULTIPLE MODE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     16965         -
# 2  Short offline       Completed without error       00%     16965         -
# 3  Extended offline    Completed without error       00%         0         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```
I've done some more Googling. . . it sounds like others have similar issues, and like maybe adding 'irqpoll' or other options in GRUB may stop this.

I'll give it a shot.

---

### Post by linuxpenguin on 2008-10-23
Well I added the "irqpoll" option in GRUB's config last night. . .

It doesn't necessarily mean anything conclusive, but I just got home from work and the server is still running fine.  I got on my homepage fine and could visit all the links and what-not - and get into phpMyAdmin. :)

Seems this whole week, every day when I came home from work it would either be not responding or would give me that SQL error when I try to get on my site.  And typing the URL I use for phpMyAdmin would bring me to a "404" page - presumably because it couldn't even read the file it was trying to get at.  Yesterday when I was able to stay logged in in spite of the error, I tried to reboot but got an I/O error - then I tried to explore more, and found that for most directories, even though I could access them, no files would show up in them, and in the ones where I could see the files listed I would get an I/O error when trying to execute or edit them.

Just letting you guys know in case anyone else ever runs into this.  I'll be sure to give an update later if I see that it errored out again, or if it stays up long enough for me to be sure it's fixed.

---

### Post by linuxpenguin on 2008-10-26
Well good news - the server's been running stable for a while now (save a power outage that happened the other night) - so this seems to have taken care of the issue!  Not sure exactly why this helps, but it's working and that's what's important.

---


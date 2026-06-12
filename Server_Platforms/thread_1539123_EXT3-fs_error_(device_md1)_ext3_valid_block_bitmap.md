---
title: "EXT3-fs error (device md1): ext3_valid_block_bitmap: Invalid block bitmap - block_gro"
date: 2010-07-26
forum: Server Platforms
---

### Post by altoas on 2010-07-26
software raid1 with 2x1TB drives. It was working fine for over 2y. but after update to 2.6.32-22 it started to corrupt the fs


[7403770.048761] EXT3-fs error (device md1): ext3_valid_block_bitmap: Invalid block bitmap - block_group = 0, block = 1025
[7403776.103609] EXT3-fs error (device md1): ext3_new_block: Allocating block in system zone - blocks from 1025, length 1
[7403776.152691] EXT3-fs error (device md1): ext3_new_block: Allocating block in system zone - blocks from 1026, length 1
[7403776.177774] EXT3-fs error (device md1): ext3_new_block: Allocating block in system zone - blocks from 1027, length 1


[7404082.494766] init_special_inode: bogus i_mode (36515) for inode md1:11616264
[7404083.216034] init_special_inode: bogus i_mode (151623) for inode md1:11616262
[7404083.227176] init_special_inode: bogus i_mode (134124) for inode md1:12509193
[7404083.266631] init_special_inode: bogus i_mode (171475) for inode md1:11624453
[7404083.266747] attempt to access beyond end of device
[7404083.266752] md1: rw=0, want=31269653200, limit=1927751552
[7404083.266755] attempt to access beyond end of device
[7404083.266757] md1: rw=0, want=31269653200, limit=1927751552
[7404083.589838] init_special_inode: bogus i_mode (167767) for inode md1:12058653
[7404083.589923] init_special_inode: bogus i_mode (177166) for inode md1:12058652
[7404083.623337] init_special_inode: bogus i_mode (167362) for inode md1:12075014
[7404083.639081] init_special_inode: bogus i_mode (170126) for inode md1:12083203
[7404083.898811] init_special_inode: bogus i_mode (76553) for inode md1:11894786
[7404084.433064] init_special_inode: bogus i_mode (56670) for inode md1:11976707
[7404084.498326] init_special_inode: bogus i_mode (35011) for inode md1:12034054
[7404084.695039] init_special_inode: bogus i_mode (111167) for inode md1:11984900
[7404084.695125] init_special_inode: bogus i_mode (70313) for inode md1:11984898
[7404525.040599] attempt to access beyond end of device
[7404525.040607] md1: rw=1, want=31665241568, limit=1927751552
[7404525.040610] attempt to access beyond end of device
[7404525.040614] md1: rw=1, want=28667985200, limit=1927751552
[7404525.040617] attempt to access beyond end of device
[7404525.040620] md1: rw=1, want=7180209680, limit=1927751552
[7404525.040622] attempt to access beyond end of device
[7404525.040626] md1: rw=1, want=30035793400, limit=1927751552
[7404525.040628] attempt to access beyond end of device
[7404525.040632] md1: rw=1, want=30337447144, limit=1927751552
[7404525.043101] Aborting journal on device md1.
[7404525.062775] ext3_abort called.
[7404525.073770] EXT3-fs error (device md1): ext3_journal_start_sb: Detected aborted journal
[7404525.096286] Remounting filesystem read-only


fsck deleted all data. lost+found is full with #ddddd files 

can I recover the files somehow?

---


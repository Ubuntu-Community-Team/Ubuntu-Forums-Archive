---
title: "Secure delete ext4 kernel patch"
date: 2011-08-26
forum: Security
---

### Post by oldos2er on 2011-08-26
Does anyone know if this kernel patch has been applied to any 11.04 kernels? [http://lwn.net/Articles/450262/](http://lwn.net/Articles/450262/)

I've googled the subject but can't find any good info.

---

### Post by FuturePilot on 2011-08-26
I would be interested to know this as well.

---

### Post by bodhi.zazen on 2011-08-26
As that is a patch to the kernel you would assume it is included as the patch is not maintained by Ubuntu and I can not see why they would remove it.

If you want to know, file a bug report or post on the kernel mailing list.

---

### Post by NightwishFan on 2011-08-26
All the lines related to ext4 in the diff of the ubuntu image generic source package:
Nothing jumps out at me. If it is in mainline it likely is in Ubuntu, if not in mainline it probably isnt.

```
+  * ext4: fix possible use-after-free in ext4_remove_li_request()
+  * ext4: release page cache in ext4_mb_load_buddy error path
+  * ext4: Use schedule_timeout_interruptible() for waiting in lazyinit
+  * ext4: init timer earlier to avoid a kernel panic in __save_error_info,
+  * ext4: fix a double free in ext4_register_li_request
+  * ext4: fix credits computing for indirect mapped files
+  * Revert "SAUCE: sync before umount to reduce time taken by ext4 umount"
+  * ext4: Convert to generic reserved quota's space management.
+  * ext4: fix sleep inside spinlock issue with quota and dealloc (#14739)
+  * ext4: Update documentation to correct the inode_readahead_blks option
+  * quota: Fix dquot_transfer for filesystems different from ext4
+  * Revert "ext4: Fix insufficient checks in EXT4_IOC_MOVE_EXT"
+  * ext4: fix potential buffer head leak when add_dirent_to_buf() returns
+  * ext4: avoid divide by zero when trying to mount a corrupted file system
+  * ext4: fix the returned block count if EXT4_IOC_MOVE_EXT fails
+  * ext4: fix lock order problem in ext4_move_extents()
+  * ext4: fix possible recursive locking warning in EXT4_IOC_MOVE_EXT
+  * ext4: plug a buffer_head leak in an error path of ext4_iget()
+  * ext4: make sure directory and symlink blocks are revoked
+  * ext4: fix i_flags access in ext4_da_writepages_trans_blocks()
+  * ext4: journal all modifications in ext4_xattr_set_handle
+  * ext4: don't update the superblock in ext4_statfs()
+  * ext4: fix uninit block bitmap initialization when s_meta_first_bg is
+  * ext4: fix block validity checks so they work correctly with meta_bg
+  * ext4: avoid issuing unnecessary barriers
+  * ext4: fix error handling in ext4_ind_get_blocks()
+  * ext4: make trim/discard optional (and off by default)
+  * ext4: make "norecovery" an alias for "noload"
+  * ext4: Fix double-free of blocks with EXT4_IOC_MOVE_EXT
+  * ext4: initialize moved_len before calling ext4_move_extents()
+  * ext4: move_extent_per_page() cleanup
+  * ext4: Return the PTR_ERR of the correct pointer in
+  * ext4: Avoid data / filesystem corruption when write fails to copy data
+  * ext4: wait for log to commit when umounting
+  * ext4: remove blocks from inode prealloc list on failure
+  * ext4: ext4_get_reserved_space() must return bytes instead of blocks
+  * ext4: quota macros cleanup
+  * ext4: fix incorrect block reservation on quota transfer.
+  * ext4: Wait for proper transaction commit on fsync
+  * ext4: Fix insufficient checks in EXT4_IOC_MOVE_EXT
+  * ext4: Fix potential fiemap deadlock (mmap_sem vs. i_data_sem)
+  * ext4: Fix insufficient checks in EXT4_IOC_MOVE_EXT
+  * ext4: Don't update superblock write time when filesystem is read-only
+  * ext4: fix possible use-after-free in ext4_remove_li_request()
+  * ext4: release page cache in ext4_mb_load_buddy error path
+  * ext4: Use schedule_timeout_interruptible() for waiting in lazyinit
+  * ext4: init timer earlier to avoid a kernel panic in __save_error_info,
+  * ext4: fix a double free in ext4_register_li_request
+  * ext4: fix credits computing for indirect mapped files
+  * Revert "SAUCE: sync before umount to reduce time taken by ext4 umount"
+  * ext4: Convert to generic reserved quota's space management.
+  * ext4: fix sleep inside spinlock issue with quota and dealloc (#14739)
+  * ext4: Update documentation to correct the inode_readahead_blks option
+  * quota: Fix dquot_transfer for filesystems different from ext4
+  * Revert "ext4: Fix insufficient checks in EXT4_IOC_MOVE_EXT"
+  * ext4: fix potential buffer head leak when add_dirent_to_buf() returns
+  * ext4: avoid divide by zero when trying to mount a corrupted file system
+  * ext4: fix the returned block count if EXT4_IOC_MOVE_EXT fails
+  * ext4: fix lock order problem in ext4_move_extents()
+  * ext4: fix possible recursive locking warning in EXT4_IOC_MOVE_EXT
+  * ext4: plug a buffer_head leak in an error path of ext4_iget()
+  * ext4: make sure directory and symlink blocks are revoked
+  * ext4: fix i_flags access in ext4_da_writepages_trans_blocks()
+  * ext4: journal all modifications in ext4_xattr_set_handle
+  * ext4: don't update the superblock in ext4_statfs()
+  * ext4: fix uninit block bitmap initialization when s_meta_first_bg is
+  * ext4: fix block validity checks so they work correctly with meta_bg
+  * ext4: avoid issuing unnecessary barriers
+  * ext4: fix error handling in ext4_ind_get_blocks()
+  * ext4: make trim/discard optional (and off by default)
+  * ext4: make "norecovery" an alias for "noload"
+  * ext4: Fix double-free of blocks with EXT4_IOC_MOVE_EXT
+  * ext4: initialize moved_len before calling ext4_move_extents()
+  * ext4: move_extent_per_page() cleanup
+  * ext4: Return the PTR_ERR of the correct pointer in
+  * ext4: Avoid data / filesystem corruption when write fails to copy data
+  * ext4: wait for log to commit when umounting
+  * ext4: remove blocks from inode prealloc list on failure
+  * ext4: ext4_get_reserved_space() must return bytes instead of blocks
+  * ext4: quota macros cleanup
+  * ext4: fix incorrect block reservation on quota transfer.
+  * ext4: Wait for proper transaction commit on fsync
+  * ext4: Fix insufficient checks in EXT4_IOC_MOVE_EXT
+  * ext4: Fix potential fiemap deadlock (mmap_sem vs. i_data_sem)
+  * ext4: Fix insufficient checks in EXT4_IOC_MOVE_EXT
+  * ext4: Don't update superblock write time when filesystem is read-only
+  * Revert "ext4: wait on all pending commits in ext4_sync_fs()"
+  * ext4: Fix to read empty directory blocks correctly in 64k
+  * ext4: Fix lockdep warning
+  * ext4: Initialize preallocation list_head's properly
+  * ext4: Implement range_cyclic in ext4_da_writepages instead of
+  * ext4: Fix NULL dereference in ext4_ext_migrate()'s error handling
+  * ext4: Add fallback for find_group_flex
+  * ext4: Fix deadlock in ext4_write_begin() and ext4_da_write_begin()
+  * Enable build of ext4 as a module on LPIA
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Initialize the new
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Add sanity check
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: only use
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Add sanity checks
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Fix
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Init the complete
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Don't allow new
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: mark the
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Use new
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Fix the race
+    between read_inode_bitmap() and ext4_new_inode()"
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Fix race between
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: don't use blocks
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: cleanup mballoc
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Use
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Add blocks added
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Don't overwrite
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Widen type of
+    ext4_sb_info.s_mb_maxs[]"
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: avoid ext4_error
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Fix the delalloc
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: tone down
+    ext4_da_writepages warnings"
+  * Revert "SAUCE: (revert before 2.6.28.y update) ext4: Add support for
+  * ext4: Add support for non-native signed/unsigned htree hash algorithms
+  * ext4: tone down ext4_da_writepages warnings
+  * ext4: Fix the delalloc writepages to allocate blocks at the right
+  * ext4: avoid ext4_error when mounting a fs with a single bg
+  * ext4: Widen type of ext4_sb_info.s_mb_maxs[]
+  * ext4: Don't overwrite allocation_context ac_status
+  * ext4: Add blocks added during resize to bitmap
+  * ext4: Use EXT4_GROUP_INFO_NEED_INIT_BIT during resize
+  * ext4: cleanup mballoc header files
+  * ext4: don't use blocks freed but not yet committed in buddy cache init
+  * ext4: Fix race between read_block_bitmap() and mark_diskspace_used()
+  * ext4: Fix the race between read_inode_bitmap() and ext4_new_inode()
+  * ext4: Use new buffer_head flag to check uninit group bitmaps
+  * ext4: mark the blocks/inode bitmap beyond end of group as used
+  * ext4: Don't allow new groups to be added during block allocation
+  * ext4: Init the complete page while building buddy cache
+  * ext4: Fix s_dirty_blocks_counter if block allocation failed with
+  * ext4: Add sanity checks for the superblock before mounting the
+  * ext4: only use i_size_high for regular files
+  * ext4: Add sanity check to make_indexed_dir
+  * ext4: Initialize the new group descriptor when resizing the filesystem
+  * SAUCE: (revert before 2.6.28.y update) ext4: Fix the delalloc
+  * SAUCE: (revert before 2.6.28.y update) ext4: avoid ext4_error when
+  * SAUCE: (revert before 2.6.28.y update) ext4: Don't overwrite
+  * SAUCE: (revert before 2.6.28.y update) ext4: Add blocks added during
+  * SAUCE: (revert before 2.6.28.y update) ext4: Use
+  * SAUCE: (revert before 2.6.28.y update) ext4: cleanup mballoc header
+  * SAUCE: (revert before 2.6.28.y update) ext4: don't use blocks freed but
+  * SAUCE: (revert before 2.6.28.y update) ext4: Fix race between
+  * SAUCE: (revert before 2.6.28.y update) ext4: Fix the race between
+    read_inode_bitmap() and ext4_new_inode()
+  * SAUCE: (revert before 2.6.28.y update) ext4: Use new buffer_head flag
+  * SAUCE: (revert before 2.6.28.y update) ext4: mark the blocks/inode
+  * SAUCE: (revert before 2.6.28.y update) ext4: Don't allow new groups to
+  * SAUCE: (revert before 2.6.28.y update) ext4: Init the complete page
+  * SAUCE: (revert before 2.6.28.y update) ext4: Fix s_dirty_blocks_counter
+  * SAUCE: (revert before 2.6.28.y update) ext4: Add support for non-native
+  * SAUCE: (revert before 2.6.28.y update) ext4: tone down
+    ext4_da_writepages warnings
+  * SAUCE: (revert before 2.6.28.y update) ext4: Add sanity checks for the
+  * SAUCE: (revert before 2.6.28.y update) ext4: only use i_size_high for
+  * SAUCE: (revert before 2.6.28.y update) ext4: Add sanity check to
+  * SAUCE: (revert before 2.6.28.y update) ext4: Initialize the new group
+  * SAUCE: (revert before 2.6.28.y update) ext4: Widen type of
+    ext4_sb_info.s_mb_maxs[]
+  * ext4: add missing unlock to an error path in ext4_quota_write()
```

---

### Post by oldos2er on 2011-08-26
I've emailed the kernel-team list, and I will post back here if and when they answer.

Thanks everyone.

---

### Post by oldos2er on 2011-08-30
Received this reply from kernel-team mailing list:

"As far as I can tell these patches are note as yet applied to Linus'
kernel so we would not have them via there and I do not recall seeing
them.

I suspect there is going to be some resistance as they are only clearing
the blocks for the file, which would not be deemed 'secure delete' in
normal parlance."

---


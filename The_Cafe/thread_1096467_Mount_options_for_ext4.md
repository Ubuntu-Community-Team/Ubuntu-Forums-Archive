---
title: "Mount options for ext4 ?"
date: 2009-03-14
forum: The Cafe
---

### Post by dusan.saiko on 2009-03-14
Hello, 

do you know, where can I find manual for mount options for ext4 ?
man mount( 8 ) does not contain them yet (contains ext2 and ext3, not ext4).

I have found some posts using "extents,delalloc" options, but was not able to get any documentation for this.

Thanks.

---

### Post by Bölvaður on 2009-03-15
have you tried doing the same as for ext3 but just writing ext4 instead?

---

### Post by TheUnderTaker on 2009-03-15
Here are the mount options for ext4 from the kernel documentation

3. Options
==========

When mounting an ext4 filesystem, the following option are accepted:
(*) == default

extents		(*)	ext4 will use extents to address file data.  The
			file system will no longer be mountable by ext3.

noextents		ext4 will not use extents for newly created files

journal_checksum	Enable checksumming of the journal transactions.
			This will allow the recovery code in e2fsck and the
			kernel to detect corruption in the kernel.  It is a
			compatible change and will be ignored by older kernels.

journal_async_commit	Commit block can be written to disk without waiting
			for descriptor blocks. If enabled older kernels cannot
			mount the device. This will enable 'journal_checksum'
			internally.

journal=update		Update the ext4 file system's journal to the current
			format.

journal=inum		When a journal already exists, this option is ignored.
			Otherwise, it specifies the number of the inode which
			will represent the ext4 file system's journal file.

journal_dev=devnum	When the external journal device's major/minor numbers
			have changed, this option allows the user to specify
			the new journal location.  The journal device is
			identified through its new major/minor numbers encoded
			in devnum.

noload			Don't load the journal on mounting.

data=journal		All data are committed into the journal prior to being
			written into the main file system.

data=ordered	(*)	All data are forced directly out to the main file
			system prior to its metadata being committed to the
			journal.

data=writeback		Data ordering is not preserved, data may be written
			into the main file system after its metadata has been
			committed to the journal.

commit=nrsec	(*)	Ext4 can be told to sync all its data and metadata
			every 'nrsec' seconds. The default value is 5 seconds.
			This means that if you lose your power, you will lose
			as much as the latest 5 seconds of work (your
			filesystem will not be damaged though, thanks to the
			journaling).  This default value (or any low value)
			will hurt performance, but it's good for data-safety.
			Setting it to 0 will have the same effect as leaving
			it at the default (5 seconds).
			Setting it to very large values will improve
			performance.

barrier=<0|1(*)>	This enables/disables the use of write barriers in
			the jbd code.  barrier=0 disables, barrier=1 enables.
			This also requires an IO stack which can support
			barriers, and if jbd gets an error on a barrier
			write, it will disable again with a warning.
			Write barriers enforce proper on-disk ordering
			of journal commits, making volatile disk write caches
			safe to use, at some performance penalty.  If
			your disks are battery-backed in one way or another,
			disabling barriers may safely improve performance.

inode_readahead=n	This tuning parameter controls the maximum
			number of inode table blocks that ext4's inode
			table readahead algorithm will pre-read into
			the buffer cache.  The default value is 32 blocks.

orlov		(*)	This enables the new Orlov block allocator. It is
			enabled by default.

oldalloc		This disables the Orlov block allocator and enables
			the old block allocator.  Orlov should have better
			performance - we'd like to get some feedback if it's
			the contrary for you.

user_xattr		Enables Extended User Attributes.  Additionally, you
			need to have extended attribute support enabled in the
			kernel configuration (CONFIG_EXT4_FS_XATTR).  See the
			attr(5) manual page and [http://acl.bestbits.at/](http://acl.bestbits.at/) to
			learn more about extended attributes.

nouser_xattr		Disables Extended User Attributes.

acl			Enables POSIX Access Control Lists support.
			Additionally, you need to have ACL support enabled in
			the kernel configuration (CONFIG_EXT4_FS_POSIX_ACL).
			See the acl(5) manual page and [http://acl.bestbits.at/](http://acl.bestbits.at/)
			for more information.

noacl			This option disables POSIX Access Control List
			support.

reservation

noreservation

bsddf		(*)	Make 'df' act like BSD.
minixdf			Make 'df' act like Minix.

debug			Extra debugging information is sent to syslog.

errors=remount-ro(*)	Remount the filesystem read-only on an error.
errors=continue		Keep going on a filesystem error.
errors=panic		Panic and halt the machine if an error occurs.

data_err=ignore(*)	Just print an error message if an error occurs
			in a file data buffer in ordered mode.
data_err=abort		Abort the journal if an error occurs in a file
			data buffer in ordered mode.

grpid			Give objects the same group ID as their creator.
bsdgroups

nogrpid		(*)	New objects have the group ID of their creator.
sysvgroups

resgid=n		The group ID which may use the reserved blocks.

resuid=n		The user ID which may use the reserved blocks.

sb=n			Use alternate superblock at this location.

quota
noquota
grpquota
usrquota

bh		(*)	ext4 associates buffer heads to data pages to
nobh			(a) cache disk block mapping information
			(b) link pages into transaction to provide
			    ordering guarantees.
			"bh" option forces use of buffer heads.
			"nobh" option tries to avoid associating buffer
			heads (supported only for "writeback" mode).

stripe=n		Number of filesystem blocks that mballoc will try
			to use for allocation size and alignment. For RAID5/6
			systems this should be the number of data
			disks *  RAID chunk size in file system blocks.
delalloc	(*)	Deferring block allocation until write-out time.
nodelalloc		Disable delayed allocation. Blocks are allocation
			when data is copied from user to page cache.

---

### Post by dusan.saiko on 2009-03-15
thank you, perfect :-)

---

### Post by rockorequin on 2009-04-01
A couple of these options don't sound quite right to me, specifically:

*commit=nrsec (*) Ext4 can be told to sync all its data and metadata every 'nrsec' seconds. The default value is 5 seconds.*

Five seconds is an ext3 setting. For performance reasons, ext4 might not write data for over a minute (delayed allocation), and in its original form, it can commit the file metadata without writing the data, resulting in zero-length files. Since the write time is so long, some have people experienced data loss when their system crashed.

[I]data=ordered (*) All data are forced directly out to the main file system prior to its metadata being committed to the journal.
[/I]
To reduce the chance of this data loss, Ubuntu now has patches that insert a barrier to renames that occur over existing files so that you don't lose the old contents as well as the new if the file system is not unmounted cleanly. According to the patch comments, this is applied if data=ordered mode is set, but it *only* applies if you truncate a file or rename it over another file. So data is *only* sync'd with metadata in these cases.

This means of course that it's still possible to end up with zero-length files if you create a file, rename it to a file that doesn't already exist, and then before the system has a chance to write the data, it crashes or loses power or you do something like remove an external USB ext4 drive without unmounting or sync'ing it first.

There's a long bug discussion about this at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

---


---
title: "Wipe with ex4 journaling file system"
date: 2010-02-17
forum: Security
---

### Post by ubunchu on 2010-02-17
I was reading a website about securely wiping data from  your hard drive with wipe on the right click menu, when I stumbled across part of the article where it talked about journaling filesystems.

[Article]("http://www.freesoftwaremagazine.com/columns/shred_and_secure_delete_tools_wiping_files_partitions_and_disks_gnu_linux")

> There are three types of journaling: journal, ordered and writeback. Using shred, with an ext3 file system presents the user with the problem of secure deletion because it can only really be effectively used with ordered and writeback journals.

It also lists ext4 as a journaling file system in the article, so I looked up the wikipedia page on it and I also found this:

> **Delayed allocation**Ext4 uses a filesystem performance technique called [allocate-on-flush]("http://en.wikipedia.org/wiki/Allocate-on-flush"), also known as *delayed allocation*. It consists of delaying block allocation until the data is going to be written to the disk, unlike some other file systems, which may allocate the necessary blocks before that step. This improves performance and reduces [fragmentation]("http://en.wikipedia.org/wiki/File_system_fragmentation") by improving block allocation decisions based on the actual file size.

So I am confused about this delayed allocation thing. My thoughts are that ext3 and other journaling filesystems are bad to use with secure wipe when they are set on journal mode because that writes the file to the journaling sector as well as to the hard drive. Apparently, in ext3, the default was ordered mode. I would like to know if anyone has any idea if the ext4 file system on karmic 64bit is hazardous to the security of using the wipe command.

Thank you very much.

---

### Post by mkvnmtr on 2010-02-17
From my reading it looks like you are correct. You might try reading the man pages of secure delete or googling. It looks like the only thing that is very safe is to wipe the whole disk 38 times and reinstall. After a disk wipe and using encryption you would be as safe as your password.

---

### Post by rookcifer on 2010-02-18
You should be fine using shred to delete individual files on ext4, but if you are paranoid then you can simply overwrite the free space on the disk by using the secure-delete package or something like bcwipe.

In any case, you can securely do this with only one pass.  This "35 pass" business (started by Peter Gutmann) has been disproven when it comes to modern EPRML hard drives, as even Gutmann himself admits.

---


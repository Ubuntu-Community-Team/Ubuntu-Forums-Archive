---
title: "Moving Windows profile folder to a shared Ext2 partition"
date: 2007-01-30
forum: Windows
---

### Post by CSMatt on 2007-01-30
I know that most people here aren't exactly Windows experts, and for good reason in my opinion, but I still would feel better if I had some clarification before I act.

I know that the user's folder in the Documents and Settings folder is pointed to in the %UserProfile% environment variable.  Now I want to shift all personal information onto an Ext2 partition for read/write and patent-free interoperability with Ubuntu and Windows, and it would be most convenient if I could just move the entire profile folder over to the partition.  I know that I can just move My Documents, and I already did that, but  that leaves Application Data, Desktop, and other personal stuff on the NTFS partition.  I think I can change the environment variable in Windows, boot into Ubuntu to copy everything, and restart Windows in the new location with no problems.  However, there might be some reason that the profile folder can't exist on a FAT or NTFS file system.  Is it possible that the IFS driver I have installed is loaded *after* the profile folder is accessed and not before?  I already found out that it does not load in Safe Mode, which will make that pretty much impossible for this profile.  I can just make a new profile specifically for Safe Mode, or just use Administrator, so that isn't a loss.  Is there any other way that this would not be able to work?

---


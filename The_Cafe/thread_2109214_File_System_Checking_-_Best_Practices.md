---
title: "File System Checking - Best Practices"
date: 2013-01-26
forum: The Cafe
---

### Post by Herman on 2013-01-26
Is there any sense  in running fsck -N first or should we just use  -y right away and get it all over and done with fast?

When we run fsck or e2fsck with the -y option and there are some serious file system problems, it silently unlinks any orphaned files to the lost+found.
That's all fine and dandy when there's no big problems, normally no files need to be unlinked and fsck just runs and fixes the file system. 
When there are some problems, getting files back from the lost+found directory is probably not something most of us really want to spend time doing. They will be identified by inode numbers instead of their file names and there may be incomplete files and file fragments. It's like trying to put Humpty Dumpty back together again.

In spite of this, the majority of websites on the internet recommend running fsck with the -y option so the user doesn't have to spend time at the keyboard typing 'y' thousands of times possibly, granting permission for fsck to unlink each file one at a time.

The other way would be to try a test run with a non-destructive file system check like fsck -N, or e2fsck -C0 -p -f -v  first. But that doesn't fix anything. Often the file system check is needed because the file system is already dirty and cannot be mounted, so how does one go about getting the files back in this situation without resorting to fsck with the -y option? 

One idea might be if there are serious file system problems possibly caused by hardware issues, the user has a chance to image the file system possibly with gparted or ddrescue to a different drive or partition and fsck or e2fsck with the -y option later if needed, possibly saving a lot of files while they're still intact.

Am I wrong? What do you other people think about that and do any of you have an interesting story about file system checking, hard disk problems or data recovery?
What can be done to save files from a damaged file system before resorting to the -y option?

---


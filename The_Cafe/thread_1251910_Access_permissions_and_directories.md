---
title: "Access permissions and directories"
date: 2009-08-28
forum: The Cafe
---

### Post by samjh on 2009-08-28
I feel the need to vent.

Why, oh why, did the makers of the Unix/Linux access control scheme bind directory access with the execute bit?

For those who are wondering what I'm blabbing about, Linux access permissions have three bits: read, write, and execute.  If you do a "ls -l" command in bash, you'll see a bunch of thing like -rwxr-xr-x in the listing.  Those are access permissions for that particular file/directory.

The problem is that while the execute bit controls whether a owner/group/others can execute a file for file objects, its behaviour is different for directories.  For directories, the execute bit controls whether or not an owner/group/others can enter that directory.

Picture this scenario: you have a bunch of files and directories that you have just been copied from a NTFS drive (eg. from a Windows partition).  Because NTFS doesn't support permissions the same way as Linux, all files will have their execute bit enabled.  For the sake of good housekeeping and security, you want to disable execution for those files that shouldn't be executable.  You decide that ALL files and any files within all the subdirectories should not be executable.  So, the logical thing to do might be:
```
chmod 644 *
```The 644 means you've disabled execution for owner/group/others, and also disabled write access for group/others.

The result?  Well, you've just disabled the execution of all the files in that particular directory, but you've also disabled entry into all of the subdirectories!  So even when you are the legitimate owner of those subdirectories, you can't even get into them!

I've just been bitten by this (yes, foolish, I know), and wonder why the designers of this system didn't bind directory entry permissions with some other bit, instead of reusing the execute bit.

Sigh...

---

### Post by Bachstelze on 2009-08-28
```
chmod 644 * && chmod +X *
```

Fixed that for you.

---

### Post by samjh on 2009-08-28
I could kiss you.

---


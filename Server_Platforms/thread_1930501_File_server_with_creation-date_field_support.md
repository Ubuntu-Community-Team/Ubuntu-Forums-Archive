---
title: "File server with creation-date field support"
date: 2012-02-23
forum: Server Platforms
---

### Post by HugoRune on 2012-02-23
Hi all,

Is there a way to have a network share on an ubuntu file server that supports preserving the creation date of files, and presenting that information to any accessing windows clients.

I know that linux filesystems only store modified-date and last-accessed-date, so there is no easy way to preserve this information. Is there a workaround for that?

Bonus if that workaround works with encFS on the underlying file system.

---

### Post by matt_symes on 2012-02-23
Hi

> **HugoRune said:**
> Hi all,

Is there a way to have a network share on an ubuntu file server that supports preserving the creation date of files, and presenting that information to any accessing windows clients.

You may have to write something yourself to do this. There is no easy way as far as i am aware. Others will correct me if i am ill informed.

> 
I know that linux filesystems only store modified-date and last-accessed-date, so there is no easy way to preserve this information. Is there a workaround for that?

Actually this is not true. Certainly ext4 stores the file creation time (crtime) but there is no easy way to get to it.

Take a look at this.

```

matthew@matthew-Aspire-7540:~$ sudo debugfs -R "stat /home/matthew/examples.desktop" /dev/sda2
debugfs 1.42 (29-Nov-2011)
Inode: 159041   Type: regular    Mode:  0644   Flags: 0x80000
Generation: 1786925867    Version: 0x00000000:00000001
User:  1000   Group:  1000   Size: 179
File ACL: 0    Directory ACL: 0
Links: 1   Blockcount: 8
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x4f05d402:e179809c -- Thu Jan  5 16:46:58 2012
 atime: 0x4f466a18:9564497c -- Thu Feb 23 16:32:24 2012
 mtime: 0x4f05d402:e179809c -- Thu Jan  5 16:46:58 2012
**crtime: 0x4f05d402:e179809c -- Thu Jan  5 16:46:58 2012**
Size of extra inode fields: 28
EXTENTS:
(0):5
matthew@matthew-Aspire-7540:~$ 
```

You can get a files creation time using debugfs, however this is not exactly straight forward.

None of the standard commands currently return the crtime as far as i am aware. Certainly they never used to.

In summation, you can get the creation time but you may have to do some work to get it and that you will have to write your self.

> 
Bonus if that workaround works with encFS on the underlying file system.

Can i have the wooden spoon ? :(

Kind regards

---

### Post by Jonathan L on 2012-02-24
Hi

This won't help you directly, but it wanted to just clarify the three times.

In fact, unix systems have traditionally stored three times, 'ctime' for change, 'mtime' for modify, and 'atime' for access.  I've always thought the names were a little confusing, as 'change' and 'modify' are pretty nearly synonms, and 'access' could mean almost anything.

In practice, the mtime is the time you last wrote to the file
The ctime is the time it was actually changed (perhaps a chmod, or a restore from backup)
The atime is the last time it was read (though this is often disabled)

The purpose of the ctime is really to decided whether things need backing up in incremental backups.  If you create a file on Monday, delete it, and restore it from backup on Tuesday, then the mtime will be Monday and the ctime will be Tuesday.

You can see them all easily with stat or ls -lc and ls -lu:
```
$ stat x
  File: `x'
  Size: 87            Blocks: 8          IO Block: 4096   regular file
Device: 805h/2053d    Inode: 3551111     Links: 1
Access: (0666/-rw-rw-rw-)  Uid: ( 1000/     jcl)   Gid: ( 1000/     jcl)
Access: 2012-02-24 16:09:51.334371145 +0000
Modify: 2012-02-24 16:11:05.595350557 +0000
Change: 2012-02-24 16:11:54.531351775 +0000
```
These definitions of when the times are updated is given in [man stat]("http://manpages.ubuntu.com/manpages/lucid/en/man2/stat.2.html"), and the wikipedia article on [stat]("http://en.wikipedia.org/wiki/Stat_%28system_call%29") is also good.

Hope that's a little help.

Jonathan.


> **matt_symes said:**
> Hi



You may have to write something yourself to do this. There is no easy way as far as i am aware. Others will correct me if i am ill informed.



Actually this is not true. Certainly ext4 stores the file creation time (crtime) but there is no easy way to get to it.

Take a look at this.

```

matthew@matthew-Aspire-7540:~$ sudo debugfs -R "stat /home/matthew/examples.desktop" /dev/sda2
debugfs 1.42 (29-Nov-2011)
Inode: 159041   Type: regular    Mode:  0644   Flags: 0x80000
Generation: 1786925867    Version: 0x00000000:00000001
User:  1000   Group:  1000   Size: 179
File ACL: 0    Directory ACL: 0
Links: 1   Blockcount: 8
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x4f05d402:e179809c -- Thu Jan  5 16:46:58 2012
 atime: 0x4f466a18:9564497c -- Thu Feb 23 16:32:24 2012
 mtime: 0x4f05d402:e179809c -- Thu Jan  5 16:46:58 2012
**crtime: 0x4f05d402:e179809c -- Thu Jan  5 16:46:58 2012**
Size of extra inode fields: 28
EXTENTS:
(0):5
matthew@matthew-Aspire-7540:~$ 
```You can get a files creation time using debugfs, however this is not exactly straight forward.

None of the standard commands currently return the crtime as far as i am aware. Certainly they never used to.

In summation, you can get the creation time but you may have to do some work to get it and that you will have to write your self.



Can i have the wooden spoon ? :(

Kind regards

---


---
title: "Execution of ELF binaries off NTFS-formatted drive now denied?"
date: 2014-04-09
forum: Security
---

### Post by syntaxerror74 on 2014-04-09
There must have been a change just recently. This has never happened before until I've completed the latest apt-get update/upgrade sequence.

Don't ask me why, but for testing purposes, I had a couple of less-important binaries I didn't want to cram into my Ubuntu drives stored on an NTFS drive for some reason, and once in a blue moon I wanted to launch one of these and just used a symbolic link to it.

Now I ALWAYS get 'Permission denied' whenever I try to launch an ELF binary off said drive.
Not until I manually copy the binary to an ext3/4 partition the binary will execute again.

Is it just me who is constantly getting that "Permission denied" thing now?

---

### Post by ant2ne on 2014-04-09
what is 
```
ls -lh /path/to/binary
```

---

### Post by syntaxerror74 on 2014-04-09
Dunno what you're on about TBH...

backup2 is partition label of NTFS drive.
the_binary_to_be_executed is meant as a placeholder for a random ELF binary you want to execute.

path is /media/backup2/stuff/linux/the_binary_to_be_executed

---

### Post by ant2ne on 2014-04-09
So in a terminal type

```
ls -lh /media/backup2/stuff/linux/the_binary_to_be_executed 
```

---

### Post by syntaxerror74 on 2014-04-09
All entries are -rwxrwxrwx so octal 777, access for everyone (invariable; as usual with NTFS drives), owner and group = root.

---

### Post by ant2ne on 2014-04-09
does it execute if moved locally?

---

### Post by syntaxerror74 on 2014-04-09
Define "locally"...I said once I copy it to a partition with a file system of the ext3, ext4 ... kind, it executes fine.

Copying the binary to another directory *within* the NTFS partition has no effect. Permission denied.

---

### Post by steeldriver on 2014-04-09
How is the NTFS partition mounted (what are the mount options)? How are you trying to execute it (from a terminal? double-clicking from a file manager?)

---

### Post by ant2ne on 2014-04-09
Move it to your home directory provided that home is mounted normally and execute it there.

---

### Post by syntaxerror74 on 2014-04-09
> **steeldriver said:**
> How is the NTFS partition mounted (what are the mount options)? How are you trying to execute it (from a terminal? double-clicking from a file manager?)

ok, called mount with no parameters and grep'd on my partition, this is the result:
```
type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

Nothing in there that could make me worry so far...? [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

Yes, I am trying to execute it via terminal.

---

### Post by steeldriver on 2014-04-09
From **man mount**

```

       noexec Do  not  allow  direct  execution of any binaries on the mounted
              filesystem.  (Until recently it was  possible  to  run  binaries
              anyway  using a command like /lib/ld*.so /mnt/binary. This trick
              fails since Linux 2.4.25 / 2.6.0.)

```

It may be the case that the gvfs-fuse automount defaults have changed (adding the noexec option) - you would need to look at the relevant changelogs I guess

---

### Post by syntaxerror74 on 2014-04-10
Thank you very much! That's finally some distinct direction to search for.

Yes I am sure, they have changed - probably for security reasons, which is why I chose this sub-forum.

HOWEVER...I've just figured out that even my older fstab from end of last year *does* have the noexec option set.
And yet I WAS able to run binaries from these partitions (which according to the noexec description should have been impossible)

For that reason I am about to assume that noexec has never worked properly (i. e. ignoring the more secure setting) *until recently* when it got eventually fixed.

---

### Post by ant2ne on 2014-04-11
> ok, called mount with no parameters and grep'd on my partition, this is the result:
Code:

type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)

Nothing in there that could make me worry so far...? might google on that noexec.

---

### Post by syntaxerror74 on 2014-04-11
Yeah...or read 2 posts above yours instead. ;)

---

### Post by ant2ne on 2014-04-14
:confused::confused:Wonder how I missed it.

---


---
title: "Write permission to mounted file system"
date: 2010-02-01
forum: Security
---

### Post by hlxshady on 2010-02-01
Hello all,

I just found that I could perform write operation using a normal user account to a file system I mounted with the commands as followed:

sudo mount -t ntfs /dev/sda1 /mnt/disk/

This is the corresponding entry in the output of "mount" command:
/dev/sda1 on /mnt/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

As far as I remember, when using a normal user account, I had to use "sudo" to perform any write operations (mkdir, rm, etc) to a device mounted using "sudo".
But now it seems to be changed.

Have any of you got an idea of this?
Do I remember wrong, or did Karmic have any updates change this setting?
(I never manually changed user settings, except that I added a root user, but I never used it.)

OS: Karmic(up2dated)
Kernel: Linux stephen-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux


Thanks :)

---

### Post by quixote on 2010-02-03
Does that drive have an entry in /etc/fstab?  If one of the options there for that drive is "user" then maybe that's what's allowing it? (Or maybe it was "users".  They mean two different things, and I always forget which was which.)  

Another possibility would be something to do with new gnome virtual filesystem (gvfs, and fuse relate to that) and some kind of peculiar permission stuff it's doing.  I don't know anything about that, but it wouldn't be the first odd permission behavior.  For instance, the gnome devs departed from decades of unix/linux precedent and decided to reduce root privileges in users' home directories, thereby blowing up my backup scripts.  As you can see, don't get me started. :p

---

### Post by hlxshady on 2010-02-03
Hi quixote,

Thanks for your reply :)

Actually, this situation applies to both drivers mounted by
/etc/fstab
and
manually using "mount" command.

Following is a segment in my fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda6		/mnt/music		ntfs	0	0


and I think I omitted the "options" parameter, or it takes "0" as the parameter ...


Did you mean gfs gives such a privilege to a normal user account?

---

### Post by cdenley on 2010-02-03
I noticed the same thing, but don't understand why or how fuse works. It has nothing to do with fstab, and isn't mounted using nautilus, so I don't see where gvfs would fit in.
```

cdenley@ubuntu:~$ dd if=/dev/zero of=ntfs.img bs=512 count=10240
10240+0 records in
10240+0 records out
5242880 bytes (5.2 MB) copied, 0.112348 s, 46.7 MB/s
cdenley@ubuntu:~$ mkfs.ntfs -f -F ntfs.img
ntfs.img is not a block device.
mkntfs forced anyway.
The sector size was not specified for ntfs.img and it could not be obtained automatically.  It has been set to 512 bytes.
The partition start sector was not specified for ntfs.img and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for ntfs.img and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for ntfs.img and it could not be obtained automatically.  It has been set to 0.
Cluster size has been automatically set to 4096 bytes.
To boot from a device, Windows needs the 'partition start sector', the 'sectors per track' and the 'number of heads' to be set.
Windows will not be able to boot from this device.
Creating NTFS volume structures.
mkntfs completed successfully. Have a nice day.
cdenley@ubuntu:~$ mkdir ntfs
cdenley@ubuntu:~$ sudo mount -o loop ntfs.img ntfs
cdenley@ubuntu:~$ ls -ld ntfs
drwxrwxrwx 1 root root 4096 2010-02-03 16:02 ntfs
cdenley@ubuntu:~$ tail -n 1 /proc/mounts
/dev/loop0 /home/cdenley/ntfs fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0

```
It is the allow_other option, I believe, but I don't know where it is coming from, why it is the default, or how to turn it off.

---

### Post by quixote on 2010-02-07
the "allow_other" must be a default option specified when no options at all are used in the mount command.  ??  I don't know.  Completely guessing.  But both cdenley and hlxshady have mount commands with no options.  I've used mount commands without options, but I didn't even know you could do an fstab line that way.  Try putting in an option or two, just for the hell of it, and see if the behavior changes.  eg ```
/dev/sda6 /mnt/music ntfs **rw** 0 0
```

---


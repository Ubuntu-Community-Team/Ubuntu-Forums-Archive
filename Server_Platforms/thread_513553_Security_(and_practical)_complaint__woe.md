---
title: "Security (and practical) complaint / woe"
date: 2007-07-30
forum: Server Platforms
---

### Post by vexorian on 2007-07-30
When you mount a filesystem that does not support the (ultra well designed) unix permission it is assumed (by the kernel?) that all files got all the permissions.

I think that's great for write and read permissions, but terrible for execution... seriously, why does it assume all files are executables? Let's ignore that it allows any random file from this (obviously alien) filesystem you double click to run, but it also makes the interface much less friendly (Seriously, double click any file and get prompted if you want to run it, it is annoying)

So:
- Is there a way to disable this?
- How could I ask this thing to be changed? I mean I really think it should change...

---

### Post by koenn on 2007-07-30
[QUOTE=vexorian;3106532]
apparently you can choose how you mount a foreign filesystem :
[http://fedoranews.org/contributors/konrad_kosmowski/fat/](http://fedoranews.org/contributors/konrad_kosmowski/fat/)
so maybe it's a question of
- mount options
- how the fs driver handles the permissions

---

### Post by vexorian on 2007-07-30
All right, it is umask so it is up to the distro, and those should probably change it, I guess I can edit my fstab to change the umask thing.

---

### Post by bodhi.zazen on 2007-07-30
What file system are you trying to mount from where and how ?

I would refer you to man mount :

[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

Options and how to implement them depend on filesystem and protocol.

Examples :

> **noexec**
    Do not allow direct execution of any binaries on the mounted file system. (Until recently it was possible to run binaries anyway using a command like /lib/ld*.so /mnt/binary. This trick fails since Linux 2.4.25 / 2.6.0.)

I assume you are asking about FAT/NTFS. This is also configurable :

> **umask=value**

    Set the umask (the bitmask of the permissions that are not present). The default is the umask of the current process. The value is given in octal. 

**dmask=value**
    Set the umask applied to directories only. The default is the umask of the current process. The value is given in octal. 

**fmask=value**
    Set the umask applied to regular files only. The default is the umask of the current process. The value is given in octal.

And on ...

If you can provide more specific information I can give a more specific answer ...

---

### Post by vexorian on 2007-07-30
I do not try to mount, it is what happens when I read the ntfs partitions or my USB disk, but I just learned that I have to mod fstab to change those options...

---

### Post by bodhi.zazen on 2007-07-30
Ah, I see what you are saying.

Well, the "problem" is with NTFS and FAT. The problem does not exist if you stay with Linux partitions (like ext3).

You can mount ext3 on windows ([http://www.fs-driver.org](http://www.fs-driver.org))

Or you can modify fstab ... as you now know ;)

---

### Post by vexorian on 2007-07-30
Yes, I know, the issue was that some of my partitions  are ntfs and also my USB disks are vfat since else I wouldn't be able to mount them on any random computer I'd want...

But I really hope the default behaviour could get fixed, I guess the newcomers are more likely to have disks of these filesystems...

---


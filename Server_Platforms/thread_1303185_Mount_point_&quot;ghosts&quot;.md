---
title: "Mount point &quot;ghosts&quot;"
date: 2009-10-27
forum: Server Platforms
---

### Post by mbt on 2009-10-27
So, let me start by saying first that this *seems* to be a bug to me, but I cannot prove that (yet).

I have Ubuntu 9.10 Server Edition (RC) installed on my server, which is used to host LXC (Linux Container) virtual machines.  (LXC is like FreeBSD's jail functionality.)  Sometimes, a filesystem (usually, but not always, one of the container's root filesystems) will suddenly start returning errors that state that the filesystem is now read-only.  Looking at the output of mount, it still shows as read-write, and looking at dmesg and system logs give no indication about a filesystem panic, or the kernel deciding that it was going to remount anything read-only.  (Note: the filesystem being used is ext4.)

So, I will try to unmount and remount the filesystem so that it's assuredly read-write.  This always fails.  I can unmount the filesystem, but then when I attempt to remount it, I get the error that the directory is busy:

```
mbt@saffron:/srv/vm/trausch.us/spicerack.trausch.us$ sudo mount /srv/vm/trausch.us/spicerack.trausch.us/rootfs
[sudo] password for mbt: 
mount: /dev/mapper/saffron.data-spicerack.trausch.us already mounted or /srv/vm/trausch.us/spicerack.trausch.us/rootfs busy
```Alright, but:

```
mbt@saffron:/srv/vm/trausch.us/spicerack.trausch.us$ sudo umount /dev/mapper/saffron.data-spicerack.trausch.us
umount: /dev/mapper/saffron.data-spicerack.trausch.us: not mounted
mbt@saffron:/srv/vm/trausch.us/spicerack.trausch.us$ 
```And:

```
mbt@saffron:/srv/vm/trausch.us/spicerack.trausch.us$ mv rootfs rootfs.old.2
mv: cannot move `rootfs' to `rootfs.old.2': Device or resource busy
```The logical volume still also shows a usage count of 1.  But there are no files or directories, and when I run:

```
mbt@saffron:/srv/vm/trausch.us/spicerack.trausch.us$ mountpoint rootfs
rootfs is not a mountpoint
```There is, as I mentioned above, zero information regarding filesystem errors, block device errors, or any type of automatic kernel action on a filesystem listed in the kernel log files.  As I cannot move the filesystem's old mountpoint to create a new directory that I can mount in again (and indeed something is holding the logical volume open, but I cannot find what), I would have to apparently reboot to fix this.  Rebooting, not good.  No reason for me to have to take all of the containers down, when just one needs to be bounced.

I'm clueless as to where to start hunting for a solution; the search terms that seem pertinent to this issue are also pertinent to the all-to-frequent "I have open files on my filesystem and umount won't let me unmount it" problem.

---


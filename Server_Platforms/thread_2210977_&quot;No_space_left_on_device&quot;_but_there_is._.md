---
title: "&quot;No space left on device&quot; but there is.  What???"
date: 2014-03-13
forum: Server Platforms
---

### Post by lykwydchykyn on 2014-03-13
I have a server running ubuntu server 12.04.  I'm trying to clean up some old kernels and do updates, but they keep failing with errors like this:

```

mktemp: failed to create directory via template `/tmp/mkinitramfs_XXXXXX': No space left on device
# OR
unable to create `/var/lib/dpkg/updates/tmp.i': No space left on device

```

Thing is, there is over a GB free on /, and I don't have /tmp or /var mounted on any special device.  This is all running in a VMware image.

I did notice this in dmesg:
```

Mar 13 13:32:21 votercentral kernel: [  168.386909] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

```

But I don't see any disk errors indicating that it would mount read-only.  It does appear that I can't write anything to the partition.

I also booted to a liveCD and ran FSCK, but it comes back clean.  I chrooted in to sda1 from the livecd and tried to do the update, but I still get these errors.  What's up???

Any advice?

---

### Post by matt_symes on 2014-03-13
Hi

Do you have enough spare inodes ? Running out of inodes can also cause the error you are seeing.

EDIT:

I'm sure you know this, but for the record

```
df -i
```

for the number of inodes, the number used and the number free.

Kind regards

---

### Post by lykwydchykyn on 2014-03-13
That seems to be it; I have only 123 inodes left.  How did this happen?  How do I get more?
I've never seen this problem in 10 years of using Linux.

EDIT: Ok, I cleaned off some cruft and purged about 10 old kernels and their headers.  That seems to have given me back over 50% of my inodes.  Just weird, 10 years and you still learn stuff.

---

### Post by Lars Noodén on 2014-03-13
I've only heard of it happening once before myself also.  I gather that it is not possible to adjust  the number of inodes after the filesystem is created: "[Be warned that it is not possible to expand the number of inodes on a filesystem after it is created](http://manpages.ubuntu.com/manpages/saucy/en/man8/mke2fs.8.html)".  

The -i option might do the trick when making a new one.  How much space, as opposed to inodes, is left?  That would give an idea as to the desired ratio when creating the new filesystem and restoring from backup.  Do you have a lot of small files?

---

### Post by lykwydchykyn on 2014-03-13
> **Lars Noodén said:**
> I've only heard of it happening once before myself also.  I gather that it is not possible to adjust  the number of inodes after the filesystem is created: "[Be warned that it is not possible to expand the number of inodes on a filesystem after it is created](http://manpages.ubuntu.com/manpages/saucy/en/man8/mke2fs.8.html)".  

The -i option might do the trick when making a new one.  How much space, as opposed to inodes, is left?  That would give an idea as to the desired ratio when creating the new filesystem and restoring from backup.  Do you have a lot of small files?

Yeah, I discovered that too after a quick search.  The data itself is on a separate partition, so it's just the system eating up all those inodes.  Presumably the header files for all those old kernels was eating up the space.  Once I purged all the old kernels and headers I'm down to 42% inode usage.

---


---
title: "ext3:  fsck always finds errors - join me in a test"
date: 2008-02-11
forum: The Cafe
---

### Post by musther on 2008-02-11
I was fiddling around with fsck this morning for various reasons I won't go into.

I did a read-only check on my mounted / partition, and it found errors, so I rebooted to run a full fsck and fix them.  After returning to my system I ran a read-only check again to see the results...  only now I had more errors.

Of course, if somebody says to you "I'm always finding errors on my [insert disk size here] disk", you'd immediately jump to possible hardware errors.  So I tried several different disks, and three different computers - same result.

All the machines were running Ubuntu 7.10 and had ext3 partitions.

So, anyone care to test theirs and see what we find out - remember, I'm interested in people with ext3 partitions?

All you need to is run:

```
sudo fsck -n /
```

to check your root partition, or something like:

```
sudo fsck -n /dev/sdnX
```

where sdnX is something like sda2 for your relevant device.

The -n switch tells fsck not to write anything to the partition, making this safe to do on a mounted partition on a running system.

If you get errors, and would like to run a full fsck to see if that takes care of them, do:

```
sudo touch /forcefsck
```

and then reboot, when you get back up, do the read only check again and see if you still have errors.

Concern?
I don't know.  They're generally things like free inode count errors, but I'm not really sure if that's a bad thing or not...

---

### Post by LaRoza on 2008-02-11
Running a disk check on a disk that is in use usually results in error messages.

---

### Post by mozetti on 2008-02-11
Right - fsck is supposed to be run on unmounted partitions.

---

### Post by roachk71 on 2008-02-17
I've had to move to using ReiserFS and XFS as my filesystems, since fsck showed errors upon every reboot (especially after prelinking my ELF binaries.)

The latest fsck test on my (former) ext2 partitions resulted in fsck dying with exit code 3 on my root partition, after fixing two inodes with zero dtime. At that point, I had lost a couple of directories and mount points; not good at all. :(

This computer has a 250GB Samsung SATA drive; perhaps fsck isn't too SATA-aware yet.

---


---
title: "Drive changing name scheme?"
date: 2008-12-02
forum: Server Platforms
---

### Post by halfelite on 2008-12-02
I have a hardware raid card setup in my machine. When I first installed everything the drive path was /dev/sda. I rebooted the system a few times and made some changes added it to my fstab And everything worked great. Well today I rebooted and it changed to /dev/sdb. There were no hardware changes at all done to the system before the switch. Why did it do this and how can I make it not do it.

---

### Post by Krupski on 2008-12-03
> **halfelite said:**
> I have a hardware raid card setup in my machine. When I first installed everything the drive path was /dev/sda. I rebooted the system a few times and made some changes added it to my fstab And everything worked great. Well today I rebooted and it changed to /dev/sdb. There were no hardware changes at all done to the system before the switch. Why did it do this and how can I make it not do it.

It always does that. Solution is to use UUID instead.

First, open up a terminal and type this:

```

sudo ls -laF /dev/disk/by-uuid

```

You will see an output that looks something like this:

```

lrwxrwxrwx 1 root root  10 2008-12-02 07:54 [COLOR="Red"]**3cea96d5-e9f5-4539-9b6a-6fcde37bc195**[/COLOR] -> ../../sdc5
lrwxrwxrwx 1 root root  10 2008-12-02 07:54 [COLOR="Red"]**bf4ded5e-9dba-4d49-892c-0c673b962326**[/COLOR] -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-12-02 07:54 [COLOR="Red"]**c25d0988-1a85-4df8-8c9d-04a0398be0db**[/COLOR] -> ../../md0

```

The highlighted numbers are the UUID of each drive.

Now, in "/etc/fstab" and in "/boot/grub/menu.lst" and anywhere else you use a drive name, replace:

"/dev/sdc1"

...with...

"UUID=bf4ded5e-9dba-4d49-892c-0c673b962326"

(of course, use your OWN drive name and UUID number, above is just an example).


The name of a drive may change from /dev/sda to /dev/sdb whatever... but the UUID will always stay the same.

Good luck!

-- Roger

---

### Post by halfelite on 2008-12-03
thanks i will give that a try today

---

### Post by gpsmikey on 2008-12-03
You can also name the partitions and use the partition name in the fstab as well which, (to me anyway) is easier to read.

There are a number of threads in this forum on changing device names and fixing the fstab to get the same partition each time.

here are a couple of links you may find helpful -- drives don't always
come up in the same order and as such, may get different names (sda one
time and sde the next time) when the system boots.  Here is some info
on how to deal with that issue:

[http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)
[http://onlyubuntu.blogspot.com/2008/10/some-tips-for-correcting-uuids-in.html](http://onlyubuntu.blogspot.com/2008/10/some-tips-for-correcting-uuids-in.html)
[http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/](http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

mikey

---

### Post by xmastree on 2008-12-14
> **Krupski said:**
> It always does that. Solution is to use UUID instead.

First, open up a terminal and type this:

```

sudo ls -laF /dev/disk/by-uuid

```

Can I jump in here please?

I'm having the same problem with drives moving around, so I'm trying to fix it.

Running the above comand, I get :
```
/mnt$ sudo ls -laF /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 120 2008-12-14 17:51 ./
drwxr-xr-x 6 root root 120 2008-12-14 14:57 ../
lrwxrwxrwx 1 root root  10 2008-12-14 14:57 205C1D665C1D37CC -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-12-14 14:57 7514-09C7 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-12-14 14:57 83f88561-fe3b-4c0b-8d88-f3f0cd751e0c -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-12-14 14:57 d8d58e81-c86a-40a1-8f90-c5ca1b41b465 -> ../../sda5

```

But that's not complete...

If I do this:
```
 mount | grep /dev/sd
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda1 on /mnt/windisk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=512)
/dev/sdc1 on /mnt/sata type vfat (rw,umask=000)
/dev/sdb5 on /mnt/data type vfat (rw)

```

The system has three disks. Primary master (formerly hda) primary slave (formerly hdb) and one SATA

Currently: 
sda is the primary master, with partition #1 for Windows and #6 for linux. #5 is the swap.
sdb5 is the one partition on the primary slave
sdc1 is a SATA disk.

Where's /dev/sdc1 in the above list?

And what's up with sda1 and sdb5, why are the UUID numbers so short?

---


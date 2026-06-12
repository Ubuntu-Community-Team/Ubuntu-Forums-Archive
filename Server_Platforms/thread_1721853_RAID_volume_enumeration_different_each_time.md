---
title: "RAID volume enumeration different each time"
date: 2011-04-05
forum: Server Platforms
---

### Post by mikwit on 2011-04-05
Hi,

I have recently launched Ubunty Server 10.10 x64 alternate edition on my new machine. whole /home directory is on SATA RAID5 (Intel 82801) - 3x320GB -> 640GB.

I want to make this volume to be mounted automagicaly when system starts.
I tried to use /etc/fstab and /etc/mtab but:
1: When use UUID - nothing happends, volume isn't mounting
2: When use device name like /dev/dm-0 which allows to mount volume from console,
    device is enumerated to /dev/dm-1 after restart.

It seems that "something" checks /etc/fstab for entires and when device name is used there it is considered as already registered and device is given diferent ID which obviously isn't present in fstab

Has anyone an idea what's wrong?

---

### Post by ronparent on 2011-04-05
You would probably be better off using the /dev/mapper designation for that purpose. I have noticed in my own system that the /dev/dm-0 and /dev/dm-1 designations often switch. One designates the whole array and the other designates the 1st partition. I see no consistentency in how the system designates the dm- devices. As a matter of fact I find it annoying that one or the other along with an attempt to mount the extended partition create an error that the corresponding file system is not found (of course not).

---


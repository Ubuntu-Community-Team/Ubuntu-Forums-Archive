---
title: "Union filesystems: Unionfs, Aufs, VFS..."
date: 2010-03-15
forum: Server Platforms
---

### Post by Yann2 on 2010-03-15
Hello, I am trying to get one folder to display the content of two other folders. I have a slow server with archived projects, a fast servers with current projects, the slow server share mounted via NFS on the fast server controler, and I want a folder on that fast server controler to display the union of both current and archived folders.

I am a bit troubled by the different options. There is unionfs, which seems to be available only via fuse in Ubuntu server, and not recommended as it's said to be buggy. (1)

There is aufs, which people are campaigning hard to get out of the kernel. (2)

There are talks about a VFS solution being developped but I can't find anything about it...

What is the best solution to use?
thanks

(1) [http://ubuntuforums.org/showthread.php?t=1305391#5](http://ubuntuforums.org/showthread.php?t=1305391#5)
(2) [http://www.mail-archive.com/ubuntu-installer@lists.ubuntu.com/msg00119.html](http://www.mail-archive.com/ubuntu-installer@lists.ubuntu.com/msg00119.html)

---

### Post by awry on 2011-05-09
I totally share your confusion over what union mount filesystem(s) Ubuntu intends to support. Did you ever come to any conclusions?

I am running 10.04 for the foreseeable future, and aufs-tools was removed prior to its release.

The aufs kernel module remains in the linux-image-server build, but is absent from other kernel flavors (e.g. linux-image-virtual). 

The aufs headers are conspicuously absent from any of the kernel-headers flavors, even those with the module itself packaged. So even if you use linux-image-server, there is no way to compile functional aufs-tools against it.

The kernel-space unionfs is not supported at all (perhaps because the 1.x branch had issues), either in the kernel or with user-space tools. unionfs-fuse indeed seems buggy in my experience.

The only conclusion I can draw from all of this is that Ubuntu doesn't support any kernel-space union mounts, and I must roll a custom kernel build and maintain it across my systems, an option I do not relish.

Can anyone shed some light on what happened to unionfs and aufs support, and/or the preferred way to create a stacked, copy-on-write, kernel-space filesystem in ubuntu?

---


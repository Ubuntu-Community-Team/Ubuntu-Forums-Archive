---
title: "btrfs: /dev/btrfs-control missing"
date: 2010-06-14
forum: Server Platforms
---

### Post by doundounba on 2010-06-14
Hi all,

On my main desktop, I have been able to install btrfs-tools, convert an ext3 filesystem, and then mount (and use) the resulting btrfs filesystem.

However, I'm in the process of setting up a server, and on this box I am hitting a snag. I have installed Ubuntu Server 10.04 (64 bit), performed a safe-upgrade (which updated the kernel), and installed btrfs-tools. The problem is that this doesn't appear to have created the requisite /dev/btrfs-control file. So all btrfs operations just exit with the error "failed to open /dev/btrfs-control: No such file or directory".

Is this a known issue with btrfs-tools? Maybe because the kernel installed with Ubuntu server is different I need to do something different? Can anyone point me in the right direction?

```

doundounba@babar:~$ uname -a
Linux babar 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux

doundounba@babar:~$ sudo aptitude show btrfs-tools
Package: btrfs-tools
New: yes
State: installed
Automatically installed: no
Version: 0.19-8
Priority: optional
Section: universe/admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,122k
Depends: e2fslibs (>= 1.37), libc6 (>= 2.7), libcomerr2 (>= 1.01), libuuid1 (>= 2.16-1), zlib1g (>= 1:1.2.0)
Description: Checksumming Copy on Write Filesystem
 Btrfs is a new copy on write filesystem for Linux aimed at implementing advanced features while focusing on fault
 tolerance, repair and easy administration. 
 
 This package contains utilities (mkfs, fsck, btrfsctl) used to work with btrfs and an utility (btrfs-convert) to make
 a btrfs filesystem from an ext3. 
 
 WARNING: Btrfs is under heavy development, and is not suitable for any uses other than benchmarking and review.
Homepage: http://btrfs.wiki.kernel.org/

doundounba@babar:~$ ls -ld /dev/b*
drwxr-xr-x 2 root root 820 2010-06-14 14:15 /dev/block
drwxr-xr-x 2 root root 140 2010-06-14 14:15 /dev/bsg
drwxr-xr-x 3 root root  60 2010-06-14 14:15 /dev/bus

doundounba@babar:~$ 

```

Thanks!

---

### Post by doundounba on 2010-06-16
Hmmmm, looks like all I needed to do first is:

```

$ sudo modprobe btrfs

```

Somehow it seems that on my desktop because I converted and mounted an ext3 filesystem first, the modprobe had happened automatically...

See [https://bugs.launchpad.net/ubuntu/+source/btrfs-tools/+bug/594910]("https://bugs.launchpad.net/ubuntu/+source/btrfs-tools/+bug/594910"). Thanks to Carey Underwood for his help over IRC.

---


---
title: "How stable is ZFS on Ubuntu?"
date: 2013-01-27
forum: Server Platforms
---

### Post by Rukiri on 2013-01-27
I hear good things about ZFS and liked ZFS on one of my freebsd servers, but how stable is it on linux? Is it worth it or should I stick to btrfs? Which I have found to be VERY stable recently (3 months no issues on my main box, going back to ubuntu though as hardware optimization isn't really gaining anything in terms of speed and performance over ubuntu or any binary distro)   

So in a nutshell, is zfs on linux or fuse stable for linux? Or should I just stick to btrfs?

---

### Post by TomB19 on 2013-01-28
zfs-fuse is rock stable, in my opinion.  I've been running it for three years on an array that is currently 16.5TB (10 x 2TB - RAIDZ2) and growing.  I use it on other smaller arrays too.

I don't use zfs-fuse for boot drives, root drives, or home drives.  It would not be appropriate.

boot = EXT2 / SSD
root = EXT2 / SSD
home = EXT4 / SATA3

zfs-fuse is not fast.  I see speeds in the 12~20MBps range (note the capital "B").  These are basically USB 2.0 speeds.

I'm pleased with it because I trust it with my life's work.  I do not trust BTRFS.

... so I'm a slow but sure kind of guy.  I'd love zfs-fuse to be faster but it's fast enough and rock solid.

My hunch is, if you're used to BTRFS, you'll be disappointing with the speed of zfs-fuse.

---

### Post by rubylaser on 2013-01-28
ZFS-Fuse is slow because it runs in user space.  [ZFSonLinux]("http://zfsonlinux.org/") is much faster than the FUSE based version because it is a kernel module.  It is stable at this point and is easy to setup.  If you are between ZFSonLinux and btrfs, I wouldn't hesitate to recommend ZFS over btrfs at this point.

---

### Post by stephanvaningen on 2013-01-28
I am using ZFS on Ubuntu for a few months now. I love it, and definitely because it gives me an easy way to make snapshot backups. Reading about it ([The last word in file systems]("http://hub.opensolaris.org/bin/download/Community+Group+zfs/docs/zfslast.pdf")) made me enormously enthousiastic about it: the stability, the integrity, the possibilities... yummie! :-)

I install it [this way]("http://stephanvaningen.net/wiki/How_to_install_ZFS_on_Ubuntu"), using the ubuntu-zfs package maintained (mainly?) by Darik Horn (Launchpad dajhorn): he also responds to questions and remarks in a very timely manner! I configured it on my machine in [this way]("http://stephanvaningen.net/wiki/How_to_create_a_ZFS_filesystem_in_a_file_server")...

Have fun!

---

### Post by stephanvaningen on 2013-01-28
By the way: ubuntu-zfs is native (so no userland)

---

### Post by stephanvaningen on 2013-01-28
O yeah, I do sometimes still suddenly get a non-running machine after some specific updates, at that time I did remove of linux-headers-`uname -r` and again an apt-get install of linux-headers-`uname -r` which than did the trick (?) ....

---


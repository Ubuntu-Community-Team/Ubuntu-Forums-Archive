---
title: "Unable to mkfs.xfs on a 2TB drive"
date: 2012-01-16
forum: Server Platforms
---

### Post by Gizim on 2012-01-16
Setting up a samba server having some bad speeds with ext4 so I heard that XFS is better for that. I've unmounted my /dev/sdd1 drive and every time I try to mkfs.xfs /dev/sdd1 I get this.

mkfs.xfs: /dev/sdd1 contains a mounted filesystem

cat /proc/mounts 
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=2018796k,nr_inodes=504699,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/disk/by-uuid/134c45a2-0438-4b24-abe2-62779be34855 / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/md0 /media/mailsync ext4 rw,relatime,barrier=1,data=ordered 0 0


/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
none /var/lib/ureadahead/debugfs debugfs rw,relatime 0 0
/dev/md0 /media/mailsync ext4 rw 0 0

---

### Post by gsgleason on 2012-01-18
Show output of ```
sudo blkid|grep 134c45a2-0438-4b24-abe2-62779be34855

```
You do have a filesystem mounted by the UUID, which may be sdd1.

---

### Post by SeijiSensei on 2012-01-18
It doesn't happen to be a component of /dev/md0, does it?

If you're thinking of installing XFS on an external drive, I would suggest you think again unless you intend to connect the external to a uninterruptible power supply.  I tried XFS on an external and lost data any time the power was interrupted for whatever reason.  We're not talking about the occasional file here, either, but dozens of files.

I gave up and returned to ext4.  I don't know what performance problems you think you're having, but I haven't seen any, including streaming video.

I suspect the problem may have as much to do with Samba as with the file system involved.  If both the client and server are running Linux, you should be using NFS.  You can run NFS and Samba together on the same server, too, using one for *nix clients and the other for Windows clients.

---

### Post by rubylaser on 2012-01-18
> **SeijiSensei said:**
> It doesn't happen to be a component of /dev/md0, does it?

If you're thinking of installing XFS on an external drive, I would suggest you think again unless you intend to connect the external to a uninterruptible power supply.  I tried XFS on an external and lost data any time the power was interrupted for whatever reason.  We're not talking about the occasional file here, either, but dozens of files.

I gave up and returned to ext4.  I don't know what performance problems you think you're having, but I haven't seen any, including streaming video.

I suspect the problem may have as much to do with Samba as with the file system involved.  If both the client and server are running Linux, you should be using NFS.  You can run NFS and Samba together on the same server, too, using one for *nix clients and the other for Windows clients.

+1 for avoiding XFS like the plague in this scenario.

---


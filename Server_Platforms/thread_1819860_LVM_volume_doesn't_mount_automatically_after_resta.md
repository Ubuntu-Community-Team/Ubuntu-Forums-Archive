---
title: "LVM volume doesn't mount automatically after restart"
date: 2011-08-06
forum: Server Platforms
---

### Post by drr422 on 2011-08-06
Hello!

I'm trying to setup a ubuntu 11.04 server with LVM and NFS working.  NFS I have working I believe, but LVM seems to be giving me trouble.  When I reboot, I have to manually mount the logical volume each time with:

```
sudo mount /media/data
```

My fstab looks like the following:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf1 during installation
UUID=c82d890e-3722-483f-a640-51f7dcd8745b /               ext4    errors=remo$
# swap was on /dev/sdf5 during installation
UUID=61718cf5-517e-4432-9453-4d187bddf7eb none            swap    sw         $

# LVM
UUID=xiHkPq-R3eN-fNJW-M6Wp-SBmr-g6qB-EG7kqx     /media/data     ext4    rw,noatime  0 2

/dev/vg01/srv           /srv            ext4    rw,noatime 0 2

# NFS
/media/export/data      /media/data     none    bind    0 0 
```

I've been searching for a solution to this, but as of yet I cannot find any.  Anyone have any ideas?

---

### Post by TheR on 2011-08-07
I've got same problems with 10.04 with LVM and iScsi devices. Some thing are starting in wrong order.

I gave up the system way and write everything I needed to /etc/rc.local.

by
TheR

---

### Post by drr422 on 2011-08-07
Thanks for replying, I was just about to install 10.04 to see if it would make a difference.  I'll add the mount command to that startup script to see if I can get it running.

Edit: What I will do is edit /etc/rc.local to include the following commands, in this order:

[> mount /media/data
/etc/init.d/nfs-kernel-server restart

So that when it boots it will run it in the correct order.  I might have to add a delay, but we will see.

---


---
title: "lxd storage pool"
date: 2017-05-24
forum: Virtualisation
---

### Post by umsp on 2017-05-24
Hi,
I'm installing lxd in my home lab in btrfs
root in one btrfs file system and I mounted another btrfs file system sub-volume to /var/lib/lxd

when I try to create new VM complain with this error
# lxc launch ubuntu:14.04 my-ubuntu
error: No storage pool found. Please create a new storage pool.

# lxc storage list
+------+--------+--------+---------+
| NAME | DRIVER | SOURCE | USED BY |
+------+--------+--------+---------+


I assume problem is default storage pool not defined.
I try to create a pool with following command
   lxc storage create default btrfs source=/var/lib/lxd

But failed since trying create another sub-volume to /var/lib/lxd.

How could I edit default storage pool to add /var/lib/lxd?

Thank you,

---

### Post by simosx on 2017-06-06
For btrfs, the storage pool should be created on a device, like /dev/sdc5.
If you do not have spare space for a device, you can use ZFS and create a "loop device".

All these can take place automatically when you run "sudo lxd init" (note: it says "lxd", not "lxc").

To reinitialize LXD, you may get some help from [https://blog.simos.info/how-to-initialize-lxd-again/](https://blog.simos.info/how-to-initialize-lxd-again/)

Also, if you have Ubuntu 16.04, the default LXD is version 2.0.x. It works fine and is great.
Just make sure you know whether you have the LTS LXD version 2.0.x, or whether you have the version from the PPA (currently 2.13). These have a few changes differently.

---


---
title: "change zfs pool for lxd?"
date: 2016-11-17
forum: Virtualisation
---

### Post by jarush on 2016-11-17
I have some new nvme m.2 drives that I created a new ZFS pool on and I'd like to move my containers to that new pool and also update lxd to use the new pool by default.  Anyone know how to do that?

Alternatively, is there a way to destroy the new pool and somehow add those disks to the existing pool, remove the old disks, and change the protection to raidz?  I'm not all that familiar with ZFS.

---


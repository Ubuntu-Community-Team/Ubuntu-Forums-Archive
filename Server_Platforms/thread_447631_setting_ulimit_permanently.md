---
title: "setting ulimit permanently"
date: 2007-05-18
forum: Server Platforms
---

### Post by zarrelli on 2007-05-18
Hi,

I have a problem with pax which fights with "sleep" process

grsec: denied resource overstep by requesting 4096 for RLIMIT_CORE against limit 0 for /init[sl
eep:1985] uid/euid:0/0 gid/egid:0/0, parent /init[init:1] uid/euid:0/0 gid/egid:0/0

I suppose that raising the limit of core_file_size could help:

ulimit -a | grep core
core file size          (blocks, -c) 0

Now core dumps are disabled. So, how to enable ulimit -c 50000 at boot, so that init won't interfere with sleep process?

---

### Post by craigp84 on 2007-05-18
Hi Zarrelli,

> I have a problem with pax which fights with "sleep" process

Define "fights".

Pax as in the archiver?

Sleep as in the shell built in, or as in system hibernation?

From the rest of your post something is trying to coredump. Do you really want core files filling up your disk everytime? Are you sure?

-c

---


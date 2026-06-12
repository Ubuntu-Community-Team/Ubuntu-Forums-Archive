---
title: "Cannot decrypt luks  partition at boot"
date: 2015-07-27
forum: Server Platforms
---

### Post by rjonasz on 2015-07-27
I've been trying to resolve an issue unlocking a luks encrypted  partition on boot using Ubuntu 14.04 server. I've set it up to automatically  unlock after the root partition's password has been entered by adding  the target entry into /etc/initramfs-tools/conf.d/cryptroot. I have 6  drives in this server and 5 unlock fine. The 6th errors out with  unkonwn fs or bad options or password. I can unlock the partition after  boot using the derived key from cryptroot. I've tried to zero out the  drive and start over but the problem persists. Can anyone give me any  pointers on how to solve this? The drive is used as a cache device for  the zfs file system.

---


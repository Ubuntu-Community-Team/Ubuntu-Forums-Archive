---
title: "Can't set Kyber IO Scheduler?"
date: 2018-11-08
forum: Server Platforms
---

### Post by phixion2 on 2018-11-08
Hello,

I am trying to set kyber io scheduler as default on Ubuntu Server 18.04LTS.

I used to set it like so, on Ubuntu 16.04LTS:

```
nano /etc/default/grub
scsi_mod.use_blk_mq=y
update-grub
nano /etc/udev/rules.d/60-schedulers.rules
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="1", ATTR{queue/scheduler}="kyber"

```

I've also added "kyber-iosched" to /etc/modules-load.d/modules.conf, yet when I reboot it's still displaying [cfq] for my scheduler.

Any ideas?

Many thanks.

---


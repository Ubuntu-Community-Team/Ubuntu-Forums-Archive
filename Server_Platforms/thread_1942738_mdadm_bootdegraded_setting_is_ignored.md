---
title: "mdadm bootdegraded setting is ignored"
date: 2012-03-18
forum: Server Platforms
---

### Post by brickZA on 2012-03-18
Hi,

Using ubuntu 10.04 LTS (amd64) I've set up a software RAID1 array. The raid array is not my boot device. I wanted the (headless) sever to boot up even if there is a problem with the raid, since it is headless, so I ran dpkg-reconfig mdadm and told it to allow degraded boot.

Now I decided it would be a better idea to set nobootwait in fstab on the raid mountpoint, but not allow a degraded array to be autostarted. This makes sure that the server always boots, but seems to be safer.

The problem is that I cannot get the old behaviour restored. I have tried both dpkg-reconfigure mdadm, checked that the files in /etc/initramfs-tools/conf.d/mdadm are updated, manually ran update-initrd -k all -u, and also tried putting bootdegraded=false on the grub command line, but nothing seems to work. If I physically remove one of the hdds the system merrily boots up and mounts the degraded array.

---


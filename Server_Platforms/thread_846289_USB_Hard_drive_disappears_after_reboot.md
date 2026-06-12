---
title: "USB Hard drive disappears after reboot"
date: 2008-07-01
forum: Server Platforms
---

### Post by robgolding63 on 2008-07-01
Hi,

I have an Ubuntu 8.04 server that hosts some Virtual Machines, and it has an external USB hard drive attached for backups.

After I reboot, the USB hard drive is not detected, and doesn't even show up in **lsusb**. The drive itself is spun down, so I suspect unplugging it and plugging it back in again will allow the O/S to detect it again. This is unacceptable for a server though, so is there a command I can run at startup to "refresh" the USB devices, and get the drive connected, or any other way of solving this problem?

Thanks,

Rob

---

### Post by robgolding63 on 2008-07-03
Does anyone have any information to offer on this subject?

Now the drive seems to be appearing in **lsusb** after a reboot, and it is being mounted - then unmounted it seems straight away. When browing to **/mnt/** and issuing an **ls** command, I get the following error:
```

rob@vhost:/mnt$ ls
ls: cannot access Backup: Input/output error
Backup  Exchange  test  vhd  VMs

```

But then if I unmount the drive, and remount it again it works fine.

I have changed the fstab entry for the drive to use the UUID instead of it's device name, but I don't know whether this will have an effect.

Rob

---


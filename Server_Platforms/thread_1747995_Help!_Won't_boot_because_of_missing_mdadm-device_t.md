---
title: "Help! Won't boot because of missing mdadm-device that is not really missing"
date: 2011-05-03
forum: Server Platforms
---

### Post by apeganz on 2011-05-03
edit: Problem solved, when I removed the faulty drive I reconnected the working one as master (before it was the slave), which my BIOS apparently didn't like. Also, I found another drive in a sock drawer (not literally ;)), so I'm even back to a raid1 with 2 disks :D

Hi,

this weekend one of the two disks in my mdadm raid1 containing / died on  me, so naturally my machine would no longer boot. so I removed the dead  device from the array, leaving me with a working one-disk raid1 array  (I know, not the most useful thing in the world). but I still get  dropped to a initramfs-shell on boot with a message the device with uuid  db7... could not be found.

cat /proc/cmdline says the kernel is trying to find / on that device
ls -l /dev/disk/by-uuid/ says that is my one-disk device
mdadm -D says that device is active
mdadm --manage --run says that device is busy, so I guess it's running already (?)

I'm sure I'm missing something probably terribly simple here. Can you help me figure out what it is?

Thanks for your help,
Alex

---


---
title: "Identical devices with udev"
date: 2010-01-12
forum: Server Platforms
---

### Post by soltanis on 2010-01-12
Hey.

I have two identical hard drives; same make, same manufacturer, same model, and same capacity, which I'm trying to run in a RAID1 mirroring scheme. The problem: configuration files for md arrays only lets me use device names, such as /dev/sdb and /dev/sdc. To keep these the same (and in the same order) when I boot I wanted to write a udev rule for them.

Unfortunately, I have no way to differentiate between these two drives, as they seem to be identical. Normal methods of differentiating by size or model name wont work. I think I can use UUIDs; but I neither know how to get the UUID of a device/partition, nor do I know how to use it (if it is possible) in a udev rule.

Help?

Solution:
run
udevadm info --query=all --path=/sys/block/sdb # or whatever block dev

Look for and use "ID_SERIAL_SHORT" which is unique even for identically manufactured disks. Write a udev rule based on this property.

---

### Post by BkkBonanza on 2010-01-12
Use a command like,

udevadm info --query=all --path=/sys/block/sda/

Look for ID_SERIAL_SHORT and create a udev rule to match that and set device name.

You can also do this with UUID in /etc/fstab if you can find the UUID. 
Try,
dir /dev/disk/by-uuid/

Oh ya, can also find serial id with,
dir /dev/disk/by-id/

---

### Post by soltanis on 2010-01-13
You, sir, are awesome. Thank you for the answer. Marking as solved.

---


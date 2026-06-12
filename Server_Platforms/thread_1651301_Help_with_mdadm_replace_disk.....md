---
title: "Help with mdadm replace disk...."
date: 2010-12-22
forum: Server Platforms
---

### Post by RocKKer on 2010-12-22
I have been running a RAID 5 array with 4X 1TB disks. I recently got 4X 2TB disks with the idea of replacing the 1TB disks one disk at a time with 2TB (with full resync/recovery with each addition) to grow my array. In the end I'll grow the components to utilize all the new space.

I have successfully added the new disk to my array but the new disk was added as a spare, so I think I didn't do something correctly.

Here are my steps:
Stop server and remove/replace 1 old disk with 1 new bigger disk.

start server - mdadm noticed disk was missing and I think I chose an option to not start/or fix the array(yet).

fdisk'ed new disk.

Assembled and start the array with the surviving disks:
```
mdadm -A -s
```  

Add my new device to array:
```
mdadm /dev/md0 -a /dev/sda1
```

Mdadm happily complied with all the above and used the surviving 3 disks in degraded mode as expected and started to resync with my new disk. However my new device (/dev/sda1) shows as "spare rebuilding". To avoid the new device being added as a spare I think I should have removed the old device before adding the new device. Maybe something like this?

```
mdadm /dev/md0 --fail /dev/sda1 --remove /dev/sda1 --add /dev/sda1
```

Is there a way (once the re-syncing finishes) to change this new device from spare to "normal" member?

---


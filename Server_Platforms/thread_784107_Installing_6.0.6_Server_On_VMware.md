---
title: "Installing 6.0.6 Server On VMware ?"
date: 2008-05-06
forum: Server Platforms
---

### Post by KevinD_Atl on 2008-05-06
[FONT="Tahoma"]I can imagine the install to be prety straight forward, but I'm wondering about the the disk partitioning. I really don't wan to break the host!

Host- Ubuntu D 7.04
- VMware Server[/FONT]

---

### Post by /etc/init.d/ on 2008-05-06
The "disk" that appears to the virtual machine is really just a file on the "real" (host) disk.  This means that, by default, the partitions of the host are not exposed to or touchable by the virtual machine at all.

Also, the file that appears as the virtual disk will grow to fit, meaning if you select a 15Gb virtual disk for the VM but you only fill 2Gb of it, the disk file will only use 2Gb on the host.

---

### Post by windependence on 2008-05-06
> **/etc/init.d/ said:**
> The "disk" that appears to the virtual machine is really just a file on the "real" (host) disk.  This means that, by default, the partitions of the host are not exposed to or touchable by the virtual machine at all.

Also, the file that appears as the virtual disk will grow to fit, meaning if you select a 15Gb virtual disk for the VM but you only fill 2Gb of it, the disk file will only use 2Gb on the host.

This happens only if you set it up that way. Dynamic disks are supposed to be a bit slower than preallocated disks but I can't see too much difference myself. Of course YMMV.

You can set up a static disk if you want by pre-allocating space for the disk. They say static disks are a bit faster. BTW, these usually also can be grown manually if necessary also.

-Tim

---

### Post by /etc/init.d/ on 2008-05-07
> **windependence said:**
> This happens only if you set it up that way. 
The key words there are "only if you set it up that way."  The things I stated are the default settings, because if you don't want to risk altering your physical partitions, they are the safest defaults.

---

### Post by KevinD_Atl on 2008-05-07
[FONT="Georgia"]It came up and installed great. It moves along pretty well and doesn't eat up much CPU in the virtual environment. Now, I am starting to realize how much I hate the VI editor![/FONT]

---


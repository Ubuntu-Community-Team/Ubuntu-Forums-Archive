---
title: "External USB drive lost on reboot"
date: 2008-03-12
forum: Server Platforms
---

### Post by SumnerBoy on 2008-03-12
I have a external USB drive I use for backing up to. When I view the file system configuration in Webmin I see the two lines below... 

```
/mnt/maxtor/ Linux Native Filesystem (ext3) Partition with ID c4bbe385-7f58-417b-a6f6-02bfbf9bff23 No Yes 
/mnt/maxtor Linux Native Filesystem (ext3) SCSI device B partition 1 Yes No
```

However if I reboot the second entry disappears and /mnt/maxtor is empty - i.e. not mounted to my USB drive.

What am I missing here? My fstab file contains the following line;

```
UUID=c4bbe385-7f58-417b-a6f6-02bfbf9bff23  /mnt/maxtor/  ext3  suid,dev,exec  0  0
```

Firstly - why are there two entries in the Webmin file system list and what do they mean? And secondly why is the mount not created after a reboot?

If I unplug and then plug in the USB drive once booted it is mounted correctly without any intervention.

Any ideas?

---

### Post by MJN on 2008-03-12
> **SumnerBoy said:**
> And secondly why is the mount not created after a reboot?
 
If I unplug and then plug in the USB drive once booted it is mounted correctly without any intervention.
 
Any ideas?
 
This is likely because the USB sub-system is brought up after fstab is parsed for mount requirements. Hence, by the time the USB bus is enabled, and the drives on it detected, left to settle and made ready for mounting it's too late.
 
The best way around this, with minimal/nil consequences, would be to add **mount -av** to the **/etc/rc.local** script.
 
rc.local is executed at the end of all run-level initialisation processes and hence by the time it is called the USB bus, and drives on it, will be ready and waiting. The -a mounts all partitions listed in /etc/fstab (unless they are already mounted) and -v outputs what's happened - this info will then be available in the logs for your information.
 
Mathew

---

### Post by SumnerBoy on 2008-03-12
Thanks Mathew - that has done the trick!

---


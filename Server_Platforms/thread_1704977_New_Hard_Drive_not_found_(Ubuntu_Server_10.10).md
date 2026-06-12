---
title: "New Hard Drive not found (Ubuntu Server 10.10)"
date: 2011-03-11
forum: Server Platforms
---

### Post by idny on 2011-03-11
Hello,
Been searching for an answer but have yet to find a resolution.

I have Ubuntu 10.10 running on a HP Proliant DL380.
The Server has 1 SCSI disk install which runs the Ubuntu OS.

I recently added a new SCSI drive to the system (hot swap)
Run fdisk -ls

But it does not show the device.

I've also run
```
sudo rescan-scsi-bus.sh -w -l
```

which returned
```
0 new device(s) found.
0 device(s) removed.

```

I've have 4 other scsi bays which have the same result.
Can anyone help here? I need to be able to see the drive before i can even mount/format

Thanks
Idny

---

### Post by SeijiSensei on 2011-03-11
What does "dmesg" show?  Does it only list one drive?

---

### Post by idny on 2011-04-04
late reply on this one.

Turns out the RAID controller was previously taken out and replaced with a new one.
The new one was not configured correctly to see all drives.

Sorted now

---


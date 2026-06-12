---
title: "Swap partition fails to mount at boot up"
date: 2012-05-14
forum: Server Platforms
---

### Post by MakOwner on 2012-05-14
I just did an install on a server using the minimal install CD for 12.04.

I usually install / and swap on the same disk, but this time around I have two identical SATA disks and put / on /dev/sda and swap on /dev/sdb

The swap partition was created and formatted and the entry is in fstab by UUID.  During each boot swap fails to mount and a message is displayed - the boot continues but no swap space is allocated.  
I can log in, and "sudo swapon UUID={the uuid in /etc/fstab}" and "sudo swapon /dev/sdb1" and the swap partition mounts right up.

I don't see any issues in dmesg or the boot logs  of the disk taking too long to come on line.  smartctl -a shows the disk as healthy.

Short of putting swap back on the same disk, anyone have any ideas what could be causing this?

---

### Post by wilee-nilee on 2012-05-14
Personally I use /dev/sdaX rather than a UUID this is just an example of a partition on a sda drive. Mainly I do this as I resize partitions and reinstall OS's at a whim and it is just easier.

---

### Post by SeijiSensei on 2012-05-14
Here is the entry in my /etc/fstab for swap for reference

```
UUID=58e6b339-eac1-4acd-a9f2-d640f9b8b8bf   none   swap    sw    0       0
```

Does your system's entry have all the same parameters but just a different UUID?  You don't have quotes around the UUID perchance?

---

### Post by MakOwner on 2012-05-14
> **SeijiSensei said:**
> Here is the entry in my /etc/fstab for swap for reference

```
UUID=58e6b339-eac1-4acd-a9f2-d640f9b8b8bf   none   swap    sw    0       0
```

Does your system's entry have all the same parameters but just a different UUID?  You don't have quotes around the UUID perchance?

Yup.  The installer built the /etc/fstab.

---


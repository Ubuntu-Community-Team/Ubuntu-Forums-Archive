---
title: "SCSI device changes with each reboot, mounting by UUID does not work"
date: 2011-10-08
forum: Server Platforms
---

### Post by dallingham on 2011-10-08
I have a NFS file server running 11.04. The system as a single SATA drive for the OS, and an exported file system. The file system is a hardware RAID array on a QLogic ISP2532 Fibre Channel card. 

The SATA drive is mapped by UUID (on installation) , and mounts correctly on reboot. The RAID array was added after installation. On each reboot, it comes up as a different device. Usually as either /dev/sdb, /dev/sde, /dev/sdf, or /dev/sdg. So I cannot reliably mount this by device in the fstab file.

I have used blkid to determine the UUID of the device, and have added the device to the fstab using the UUID, but the system will not mount the drive this way. No errors are reported, but the drive is simply ignored.

The drive can be mounted using the mount command using the scsi device name.

Running blkid shows:

/dev/sdb: UUID="7cd5fdd2-2813-4d56-a4c1-8e0eb82eb8f1" TYPE="jfs" 

And the fstab file has:

UUID=7cd5fdd2-2813-4d56-a4c1-8e0eb82eb8f1 /home	jfs	rw,users,noauto,noatime	0	0

Am I doing something incorrect on try to mount by UUID?

---

### Post by CharlesA on 2011-10-08
Does the mount work with just the device name instead of the uuid?

Try a basic mount from the commandline and see what happens.

```
sudo mount UUID=7cd5fdd2-2813-4d56-a4c1-8e0eb82eb8f1 -t jfs /path/to/mountpoint
```

---

### Post by dallingham on 2011-10-08
Yes, the mount with the device name works properly.

mount -t jfs /dev/sdb /home

works properly. I have not tried the mount with the UUID yet. I will have to schedule downtime on the server to try that.

The problem just started to happen after I had to replace the fibre channel card.

---

### Post by CharlesA on 2011-10-08
Yeah, try it manually using the uuid and see if it works, then try it via fstab - add the entry to fstab then run:

```
sudo mount -a
```

to see if it mounted ok.

---

### Post by dallingham on 2011-10-15
Turns out the problem was that the array was set up for a failover, multipath environment. So the array would show up as two different devices, with the same UUID.

---

### Post by CharlesA on 2011-10-15
Wow, I would have never thought of that.

Glad you got it figured out. :)

---


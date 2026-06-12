---
title: "DRBD resource configuration using UUIDs?"
date: 2010-11-10
forum: Server Platforms
---

### Post by The Foz on 2010-11-10
I have set up mirroring of shared documents between my server and my laptop, using DRBD ([http://www.drbd.org/home/what-is-drbd/](http://www.drbd.org/home/what-is-drbd/)).

I am very happy with the results, with one small exception. DRBD defines resources to mirror in terms of disk device names like this:

```
resource dave {
  startup {
	become-primary-on df-server1;
  }
  on df-server1 {
	device /dev/drbd2;
	disk /dev/sda3;
	address 192.168.0.2:7790;
	meta-disk internal;
  }
  on acer-laptop {
	device /dev/drbd2;
	disk /dev/sda4;
	address 192.168.0.100:7790;
	meta-disk internal;
  }
}
```

On the laptop there is normally only one disk, so the partition that I am using is always going to be called /dev/sda4. 

On the server, however, I have several disks. There is no guarantee that the disks will be connected in the same order, and get the same device names, after each reboot. This is why it is recommended that you use UUIDs in /etc/fstab to manage mounting. Using device names in drbd.conf could mean that I will have to redo the DRBD configuration after rebooting, which is not ideal-

Does anyone know if it is possible to define DRBD resources in terms of UUIDs instead of device names? If so, what is the syntax?

Failing that, does anyone know how to force Ubuntu to always assign the same device name to a disk on boot-up?

---

### Post by The Foz on 2011-08-19
Bump.

---


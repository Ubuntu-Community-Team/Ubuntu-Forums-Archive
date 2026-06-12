---
title: "Flash Booting for reliability &amp; RAID rebuilding"
date: 2008-05-07
forum: Server Platforms
---

### Post by McLogic on 2008-05-07
Hard disks fail. If they fail at an unattended system, they are more of a problem. 

Software RAID-5 under Linux has a single-point of failure at boot time. Either the MBR and boot files are on a non-RAID boot drive, or they sits on the first disk of the RAID array. If the boot device fails, the system will not boot (hence the name "boot device").

A server could be booted off of cheap flash memory devices and then start/rebuild the systems RAID array. This would make the system more reliable. It could allow the system to send a call for help over the network in case of disk failure. Maintenance is then easy, people just replace drives (don't touch the software).

Look at the Infrant (now Netgear) ReadyNAS products. These products are Samba/NFS/FTP/RSYNC/webDAV, DHCP, and print servers that feature disk-failure-resistant storage. The downside is that they are slow and expensive.

[http://www.readynas.com/?p=214](http://www.readynas.com/?p=214)

The X-RAID  appears to be just software RAID5 (ext3 + lvm2 + md + mdadm) and scripts to start RAID rebuilds. It is easy, just put drives in and the array expands or rebuilds a lost drive. If the OS is on the flash memory, it is less likely to fail, and so the system will boot and run the detection/rebuilding scripts.

I don't know if this is best done with **chroot** switching, odd mount points & directory structures, or live-CD-like (and Eee-PC-like) **Union-FS** tricks. 

Any input?

---

### Post by windependence on 2008-05-07
Well my experience has not been good with software RAID. Now, I try to avoid it when possible. Even hardware RAID can be difficult to recover if the RAID controller goes bad.

-Tim

---

### Post by McLogic on 2008-05-21
> **windependence said:**
> Well my experience has not been good with software RAID. Now, I try to avoid it when possible. Even hardware RAID can be difficult to recover if the RAID controller goes bad. -Tim

Yes, software RAID is a real PITA. The idea here is to make it more automated and reliable. 

Hardware RAID can also be a problem when the hardware card fails. Hardware RAID is just software RAID running on a system-on-card, using the card's CPU and RAM, rather then the host system's. A hardware RAID card boots off of the on-card flash. 

The on-card flash has some kind of OS and some kind of RAID utilities. The card is constantly checking for failures and drives that have been replaced, then it turns on indicator lights/buzzers and rebuilds the array after a new drive is inserted.

While it would take some work, I see no reason that software RAID couldn't have a mode that functioned like hardware RAID. The main reliability advantages of hardware RAID are booting from flash (flash is much more reliable then spinning disks), and having more testing.

Is anyone interested in this?
Has anyone tried anything like this?

---


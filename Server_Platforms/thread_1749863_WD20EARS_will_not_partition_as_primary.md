---
title: "WD20EARS will not partition as primary"
date: 2011-05-04
forum: Server Platforms
---

### Post by J_brand on 2011-05-04
I am trying to build my second home file server after building an experimental x386 unit.

Gigabyte x64 Motherboard with 3core processor and 4GB RAM
10 1.5TB SATA HDD (Mostly WD15EARS and W15EADS)
2 2TB SATA2 HDD (WD20EARS)
I want to create a RAID 6 Array of the 10 1.5TB drives and (1.5 TB partitons of the 2 TB drives) the remaining 0.5TB of the 2 TB drives will be used for RAID 1 arrays (SWAP, root and usr)

When i partition the drives the 1.5 TB drives can be Primary or Logical.  The 2 TB drives do not give me this option.

For the 2 TB drives:
- i can partition into 8GB Swap, 20 GB root, 474GB usr and 1.5TB RAID6.
- When i select (Physical partition for RAID) I CANNOT change the Bootable FLag to ON.  It always stay OFF.  If i use other file systems such as exf4 it can be changed to ON.
- when i continue with the installation it fails while installing GRUB.

Questions:
Why does my 2TB drive not allow me the choice of Primary or Logical?
Is the Bootable Flag = Off the reason GRUB will not install?
How can I achieve my goal of using the 2TB drives for RAID 1 and RAID 6

Please gear your responses for a novice.

---

### Post by J_brand on 2011-05-08
Issue resolved, it turns out the 2 Tb drives where formatted as GUID.  Reformatted for MBR and no issues.

---


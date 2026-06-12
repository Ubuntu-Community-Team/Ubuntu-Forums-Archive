---
title: "Can't I install ubunt-server on server Dell ?"
date: 2010-03-25
forum: Server Platforms
---

### Post by jfabrizio on 2010-03-25
I bought a server Dell PowerEdge T110 chassis Tower with Suse Enterprise pre-installed.

The features of the server are:
1 16X DVD+/-RW ROM Drive SATA with SATA Cable for Win2K8 R2
1 iDRAC6  Embedded BMC
1 8GB di memoria (4x2GB UDIMM dual rank) 1.066MHz
2  500GB SATA 7.200rpm 3,5" disco rigido cablato
1 C17 cablato *** R1  per SAS 6iR/PERC H200, esattamente 2 unità SAS/SATA cablate
1 PERC  H200 controller RAID
1 Processore Intel Xeon X3430 (2,4GHz, cache  8MB, Turbo)
1 Keyboard : Italian (QWERTY) Dell Standard Quietkey USB  Keyboard Black
1 Dell Black 2 Button USB Scroll Optical Mouse

There is a RAID 1 with 2 disk of 500GB. 

I try to install ubuntu but the installation procedure is stopped on "Detect disks"

> "No disk drive was detected. If you know the name of the driver needed by your drive, you can select it from the list"


Is it a problem of detection of raid controller?

Thanks.

---

### Post by jfabrizio on 2010-03-25
[update...]

I try to run ubuntu-desktop from cd. Ubuntu starts correctly and I launch GPARTED and I see this partition:

- sda1 (fat32): 73MB
- sda2 (lvm2): 8 GB --> Inf: Logical volume Management is not  yet supported
- sda3 (ext3):  213 MB
- sda4 (extended): 496 GB
    - sda5 (swap): 2 GB
    - sda6 (lvm2): 454 GB -->Inf: Logical volume Management is not  yet supported

---


---
title: "DVD burner not recognised as a burner"
date: 2009-02-26
forum: Server Platforms
---

### Post by finite9 on 2009-02-26
I posted this a while ago under a different heading (brasero cannot access burner) that was probably too misleading.  Got no answers so posting again:

I have Ubuntu Server 8.10 with a LiteOn SOHW-1653S DVD-RW burner, with CS0M firmware.

When I run Brasero and try to erase a DVD-RW or format a CD-RW, the dialogue box says I have no media inserted and all controls are ghosted out apart from cancel.

If I boot into the 8.10 Live CD and run Brasero, and try to erase the same DVD-RW I tried earlier, then Brasero correclty identifies my burner as SOHW-1653S in the devices box.

Seems like an issue with Ubuntu Server/kernel/my installation.

Does anyone have any tips on what the issue could be?

```
andrew@montblanc:~$ sudo lshw -class disk
[sudo] password for andrew:
  *-cdrom
       description: DVD writer
       product: DVDRW SOHW-1653S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CS0M
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

```

---

### Post by finite9 on 2009-03-01
Ok, I've identified the problem: AHCI is enabled on all my drive controllers, which is what I want, but my DVD-ROM drive is PATA.  I remember that when I installed my hard drive using PATA drive with controller set to IDE compatible that it would not boot at all when I changed the controller to AHCI.

Now when I set the 2 controllers to IDE compatible in the BIOS, it recognises the drive in Brasero (but still has problems blanking a DVD-RW disc).

I want to use AHCI, so I have to fix the DVD drive.  Does anyone know if buying a SATA to PATA converter cable and running the PATA DVD-ROM on the SATA controller will fix the issue or do I need to buy a SATA DVD-ROM drive if Im going to persist on using AHCI?

---

### Post by finite9 on 2009-03-05
yeah.  I ordered a SATA DVD-RW drive instead.

Googled and saw that there were issues with my Jmicron controller (which drives the PATA port) and PATA devices when running other SATA devices on the ICH10 controller in AHCI mode.

---


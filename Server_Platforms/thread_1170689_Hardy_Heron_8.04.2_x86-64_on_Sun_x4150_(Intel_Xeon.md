---
title: "Hardy Heron 8.04.2 x86-64 on Sun x4150 (Intel Xeon) - Installation problems with CD"
date: 2009-05-26
forum: Server Platforms
---

### Post by enigma_0Z on 2009-05-26
I'm trying to install Ubuntu Hardy Heron (8.04.2) for x86-64 CPU's on a Sun x4150 server, and I've hit a snag. The x4150 has two quad-core Intel Xeon processors.

FWIW, I have no problems (at least so far) with the x86 installation CD, it's only the 64-bit version that I have trouble with. Based on the info below, I'm not sure to suspect an incompatibility/hardware issue, a software error, or an improper CD (it boots up just fine).

I can't seem to get past the part of the installer where it tries to find the CD and continue with the installation. I could just do a net-based install instead, but I'm afraid that there's going to be some issues with the cdrom even once I get ubuntu installed. I believe that the CD-ROM is an internally-attached USB cdrom drive. I tried heading to a shell via ctrl-alt-f2 and manually mounting the cdrom/loading the proper modules, but sr_mod, usb_storage, and cdrom were all already loaded. Trying:

```

mount /dev/scd0 /cdrom

```

Only says:

```

mount: /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 is write-protected, mounting read-only
mount: Mounting /dev/scd0 on /cdrom failed: Invalid argument

```

And the relevant dmesg output...

From loading the modules:
```

usb-storage: device scan complete
scsi 10:0:0:0: CD-ROM           TSSTcorp CD/DVDW TS-T632A SR03 PQ: 0 ANSI: 0
scsi 10:0:0:0: Attached scsi generic sg7 type 5
Driver 'sr' needs updating - please use bus_type methods
sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Uniform CD-ROM driver revision 3.20
sr 10:0:0:0: Attached scsi CD-ROM sr0

```

And this repeats every time we try to mount the drive:

```

Attempt to access beyond end of device
sr0:rw=0, want=64, limit=4
isofs_fill_super bread failed, dev=sr0, iso_blknum=16k, block=16

```

---


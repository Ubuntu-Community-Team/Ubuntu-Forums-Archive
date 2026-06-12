---
title: "Help Mounting CD-ROM on Server"
date: 2010-08-12
forum: Server Platforms
---

### Post by jbhagan on 2010-08-12
I could use some help mounting a CD-ROM on Ubuntu 8.04 Server.

The server is a virtual machine running on VMware ESXi 4.0. My goal is to install VMware tools. I have "inserted" the CD using VMware's management console.

I've googled and tried several commands but I'm clueless... Help would be appreciated.

Here's some output from "dmesg | less"
******
[    9.049123] ata1.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
[    9.205070] ata1.00: configured for UDMA/33
[    9.205257] ata2: port disabled. ignoring.
[    9.205498] scsi 0:0:0:0: CD-ROM            NECVMWar VMware IDE CDR00 1.00 PQ: 0 ANSI: 5
[    9.533754] Driver 'sr' needs updating - please use bus_type methods
[    9.535677] sr0: scsi3-mmc drive: 1x/1x xa/form2 cdda tray
[    9.535681] Uniform CD-ROM driver Revision: 3.20
[    9.535718] sr 0:0:0:0: Attached scsi CD-ROM sr0
******

This is the output from "cat /proc/scsi/scsi"
******
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: NECVMWar Model: VMware IDE CDR00 Rev: 1.00
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: VMware   Model: Virtual disk     Rev: 1.0
  Type:   Direct-Access                    ANSI  SCSI revision: 02
******

---

### Post by FuturePilot on 2010-08-12
Try
```
sudo mount /dev/sr0 /media/cdrom
```

---

### Post by jbhagan on 2010-08-13
FuturePilot, thanks for the response!

> **FuturePilot said:**
> Try
```
sudo mount /dev/sr0 /media/cdrom
```

When I try this I get:
"mount: you must specify the filesystem type"

So I googled and then tried:
```
sudo mount -t udf /dev/sr0 /media/cdrom
mount: mount point /media/cdrom does not exist
```

Any other thoughts?

---

### Post by jbhagan on 2010-08-13
Ok, so overnight the VMware virtual CD ejected. I "re-inserted" so to speak and it is working. Here's what I had to do:

create the subfolder "cdrom" under /media
then:

```
sudo mount /dev/sr0 /media/cdrom
```

This also worked:

```
sudo mount -t iso9660 /dev/sr0 /media/cdrom
```

And for my fellow noobs out there, to unmount:

```
sudo umount /media/cdrom
```


Thanks again for the assistance FuturePilot!

---


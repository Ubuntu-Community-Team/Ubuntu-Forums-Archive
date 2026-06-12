---
title: "CD/DVD Drive No longer mountable?"
date: 2010-10-12
forum: System76 Support
---

### Post by maestrofjp on 2010-10-12
I have a Serval Pro System76 with Ubuntu 10.04 Lucid installed.  For some reason in the past couple of weeks, I no longer have a CD/DVD drive available.

It looks like the kernel sees the drive based off the dmsg log.  I have a bunch output from commands below.  Does anybody have an idea what is wrong?

Best,
.pjf

The dmsg logs shows this:

[FONT=Courier New][    2.365556] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.378597] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TM00, max UDMA/100
[    2.378613] ata2.00: applying bridge limits
[    2.391947] ata2.00: configured for UDMA/100
[    2.407573] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TM00 PQ: 0 ANSI: 5
[    2.413232] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.413237] Uniform CD-ROM driver Revision: 3.20
[    2.413340] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.413378] sr 1:0:0:0: Attached scsi generic sg1 type 5
[/FONT]
Using this command "dmesg | grep CD" shows this:[FONT=Courier New]
[    2.378597] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TM00, max UDMA/100
[    2.407573] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TM00 PQ: 0 ANSI: 5
[    2.413237] Uniform CD-ROM driver Revision: 3.20
[    2.413340] sr 1:0:0:0: Attached scsi CD-ROM sr0[/FONT]

Using command "cat /etc/fstab" show this:

[FONT=Courier New]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc    proc    defaults    0    0
# / was on /dev/sda1 during installation
UUID=2c20b79b-bb2c-4422-9d48-d1cc487b189f    /    ext3    errors=remount-ro    0    1    # /dev/sda1
# /home was on /dev/sda3 during installation
UUID=46ad1127-89ed-4d27-886e-3ad3898f9243    /home    ext3    defaults    02    # /dev/sda3
# swap was on /dev/sda2 during installation
UUID=4dcb7a74-0f73-4f1f-9215-a1dcef29549e    none    swap    sw    0    0# /dev/sda2[/FONT]

Using command "sudo fdisk -l" shows this:

[FONT=Courier New]Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca2e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14648437+  83  Linux
/dev/sda2            1824        2796     7803710+  83  Linux
/dev/sda3            2796       38914   290119075+  83  Linux[/FONT]

---

### Post by maestrofjp on 2010-10-12
The output from "sudo lshw -C disk" shows this:

  *-disk                  
       description: ATA Disk
       product: ST9320423AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0002
       serial: 5VH1KQFP
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000ca2e0
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TM00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by thomasaaron on 2010-10-14
I think we may have already helped you via email. If not, please contact us at support...at...system76...dot...com and we will get you a new drive.

---


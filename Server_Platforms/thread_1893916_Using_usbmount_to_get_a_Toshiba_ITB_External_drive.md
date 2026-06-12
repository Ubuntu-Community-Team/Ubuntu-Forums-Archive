---
title: "Using usbmount to get a Toshiba ITB External drive working"
date: 2011-12-11
forum: Server Platforms
---

### Post by matthewboh on 2011-12-11
I have a USB 1Tb Toshiba drive - works great on my Ubuntu 11.10 desktop, but I'm trying to mount it onto my Ubuntu 11.10 server.

I've installed usbmount on the server and updated the usbmount.conf file to include NTFS files - here's the updated line in usbmount.conf

```
FILESYSTEMS="vfat ext2 ext3 ext4 hfsplus ntfs"
```

I plug-in the USB drive, and get the following messages in SYSLOG

```
Dec 11 10:30:27 liza kernel: [ 5306.590882] usb 2-1.1: new high speed USB device number 6 using ehci_hcd
Dec 11 10:30:27 liza kernel: [ 5306.704559] scsi9 : usb-storage 2-1.1:1.0
Dec 11 10:30:31 liza kernel: [ 5310.996775] scsi 9:0:0:0: Direct-Access     Toshiba  External USB HDD      PQ: 0 ANSI: 4
Dec 11 10:30:32 liza kernel: [ 5311.028891] sd 9:0:0:0: Attached scsi generic sg2 type 0
Dec 11 10:30:32 liza kernel: [ 5311.031319] sd 9:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 11 10:30:32 liza kernel: [ 5311.037704] sd 9:0:0:0: [sdb] Write Protect is off
Dec 11 10:30:32 liza kernel: [ 5311.037709] sd 9:0:0:0: [sdb] Mode Sense: 38 00 00 00
Dec 11 10:30:32 liza kernel: [ 5311.044075] sd 9:0:0:0: [sdb] No Caching mode page present
Dec 11 10:30:32 liza kernel: [ 5311.050889] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Dec 11 10:30:32 liza kernel: [ 5311.071264] sd 9:0:0:0: [sdb] No Caching mode page present
Dec 11 10:30:32 liza kernel: [ 5311.077987] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Dec 11 10:30:32 liza kernel: [ 5311.113958]  sdb: sdb1
Dec 11 10:30:32 liza kernel: [ 5311.128049] sd 9:0:0:0: [sdb] No Caching mode page present
Dec 11 10:30:32 liza kernel: [ 5311.134794] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Dec 11 10:30:32 liza kernel: [ 5311.141473] sd 9:0:0:0: [sdb] Attached SCSI disk
Dec 11 10:30:32 liza ata_id[1944]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Dec 11 10:30:32 liza usbmount[1954]: /dev/sdb does not contain a filesystem or disklabel

```

Here's the syslog messages from one of the desktops that successfully mounts the drive
```
Dec 11 11:30:55 mlb-dell kernel: [167931.260082] usb 1-8: new high speed USB device number 6 using ehci_hcd
Dec 11 11:30:56 mlb-dell kernel: [167931.420190] scsi6 : usb-storage 1-8:1.0
Dec 11 11:30:56 mlb-dell mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8"
Dec 11 11:30:56 mlb-dell mtp-probe: bus: 1, device: 6 was not an MTP device
Dec 11 11:30:59 mlb-dell kernel: [167935.145368] scsi 6:0:0:0: Direct-Access     Toshiba  External USB HDD      PQ: 0 ANSI: 4
Dec 11 11:30:59 mlb-dell kernel: [167935.149475] sd 6:0:0:0: Attached scsi generic sg2 type 0
Dec 11 11:30:59 mlb-dell kernel: [167935.149541] sd 6:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 11 11:30:59 mlb-dell kernel: [167935.155929] sd 6:0:0:0: [sdb] Write Protect is off
Dec 11 11:30:59 mlb-dell kernel: [167935.155944] sd 6:0:0:0: [sdb] Mode Sense: 38 00 00 00
Dec 11 11:30:59 mlb-dell kernel: [167935.162061] sd 6:0:0:0: [sdb] No Caching mode page present
Dec 11 11:30:59 mlb-dell kernel: [167935.162068] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Dec 11 11:30:59 mlb-dell kernel: [167935.176272] sd 6:0:0:0: [sdb] No Caching mode page present
Dec 11 11:30:59 mlb-dell kernel: [167935.176279] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Dec 11 11:30:59 mlb-dell kernel: [167935.207468]  sdb: sdb1
Dec 11 11:30:59 mlb-dell kernel: [167935.221932] sd 6:0:0:0: [sdb] No Caching mode page present
Dec 11 11:30:59 mlb-dell kernel: [167935.221946] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Dec 11 11:30:59 mlb-dell kernel: [167935.221956] sd 6:0:0:0: [sdb] Attached SCSI disk
Dec 11 11:30:59 mlb-dell ata_id[31323]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Dec 11 11:31:02 mlb-dell ntfs-3g[31340]: Version 2011.4.12AR.4 external FUSE 28
Dec 11 11:31:02 mlb-dell ntfs-3g[31340]: Mounted /dev/sdb1 (Read-Write, label "TOSHIBA EXT", NTFS 3.1)
Dec 11 11:31:02 mlb-dell ntfs-3g[31340]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Dec 11 11:31:02 mlb-dell ntfs-3g[31340]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Dec 11 11:31:02 mlb-dell ntfs-3g[31340]: Global ownership and permissions enforced, configuration type 7
```
But nothing shows up under /media and if I do an "ls" on all of the usb points, there's nothing.  Any ideas?

---

### Post by WasMeHere on 2011-12-11
Hi matthewboh,

What do ```
sudo fdisk -lu     # and
sudo blkid
``` tell you?

Can you mount your USB 1Tb Toshiba drive manually with ***mount***?
(assuming you know the UUID or Label)

```
sudo mkdir /media/Toshiba-1TB
sudo mount -U <uuid> -t auto /media/Toshiba-1TB     # or
sudo mount -L <label> -t auto /media/Toshiba-1TB    # or (but the device id [COLOR="Red"]/dev/sdb1[/COLOR] may change)
sudo mount -t auto /dev/sdb1 /media/Toshiba-1TB
```

Is there a 'normal' partition [COLOR="Red"]/dev/sdb1[/COLOR]? or is the file system directly in [COLOR="Red"]sdb[/COLOR] (or is usbmount assuming that)? Or does usbmount need a label (that you can make easily using gparted)?

---

### Post by matthewboh on 2011-12-13
Thanks Ollie!

> sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c934e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

Disk /dev/mapper/liza-root: 491.2 GB, 491220107264 bytes
255 heads, 63 sectors/track, 59720 cylinders, total 959414272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/liza-root doesn't contain a valid partition table

Disk /dev/mapper/liza-swap_1: 8577 MB, 8577351680 bytes
255 heads, 63 sectors/track, 1042 cylinders, total 16752640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/liza-swap_1 doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4904652

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523119   976760536    7  HPFS/NTFS/exFAT

and 

>  sudo blkid
/dev/sda5: UUID="TgBLLN-8qap-Tvqa-LsrK-fIHu-zAGT-zERNKW" TYPE="LVM2_member" 
/dev/sda1: UUID="af056555-62e8-4c6f-a315-ff1cf9aef5cc" TYPE="ext2" 
/dev/mapper/liza-root: UUID="ce433598-db33-4acd-a1c1-f24cc0526bff" TYPE="ext4" 
/dev/mapper/liza-swap_1: UUID="f54c531d-af28-40cd-a6a9-a654e0be41f4" TYPE="swap" 
/dev/sdb1: LABEL="TOSHIBA EXT" UUID="2EB2C52EB2C4FAFB" TYPE="ntfs"

and

> sudo mkdir /media/Toshiba-1TB
mlb@liza:/media$ sudo mount -t auto /dev/sdb1 /media/Toshiba-1TB
mlb@liza:/media$ ls /media/Toshiba-1TB
amanda    autorun      autorun.new  Music                      samba
Ancestry  autorun.inf  bigdrive     Quick Reference Guide.pdf  Setup.exe

So it's kind of surprising that usbmount doesn't work - ideas?

---

### Post by WasMeHere on 2011-12-14
> **matthewboh said:**
> 
```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4904652

Device Boot Start End Blocks Id System
/dev/sdb1 2048 1953523119 976760536 7 HPFS/NTFS/exFAT 
```
So it's kind of surprising that usbmount doesn't work - ideas?

Is the file system ***exFAT***, a proprietary file system owned by Microsoft and delivered on many USB drives nowadays? Some time ago that file system was not possible to mount at all in linux. Please check with Windows if it is exFAT!

But you can mount it with mount. Otherwise, if it is ntfs (as stated by blkid) I don't know the reason why mount works, but not usbmount, maybe because there is a space in the label
> ```
/dev/sdb1: LABEL="TOSHIBA EXT" UUID="2EB2C52EB2C4FAFB" TYPE="ntfs" 
```

---

### Post by jglick on 2012-10-08
I have a similar problem with a Toshiba external USB drive. The description in [https://bugzilla.redhat.com/show_bug.cgi?id=759783](https://bugzilla.redhat.com/show_bug.cgi?id=759783) matches my case. It is set up with a single ext4 partition using LUKS encryption, and previously it sufficed to just attach the USB cable and I would be prompted (in GNOME 3 Shell) for a drive password, after which the partition would be mounted. But today nothing happens and my log file shows &#8220;ata_id[&#8230;]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument&#8221;. I can mount manually using &#8216;cryptsetup luksOpen&#8217; and &#8216;mount&#8217;.

---


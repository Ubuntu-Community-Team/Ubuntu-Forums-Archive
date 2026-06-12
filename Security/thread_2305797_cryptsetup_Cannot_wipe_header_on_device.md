---
title: "cryptsetup: Cannot wipe header on device"
date: 2015-12-09
forum: Security
---

### Post by lads on 2015-12-09
I am trying to encrypt an external hard drive on Ubuntu 14.04 followig [this guide]("http://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/"). I have previously ran *badblocks* that return zero errors; I am also sure the disk is not mounted:
```

$ findmnt /dev/sdb
$ findmnt /dev/sdb1
$
```

Whenever I try the initialisation with cryptsetup I get this same error:

```
$ sudo cryptsetup -y -v luksFormat /dev/sdb1

WARNING!
========
This will overwrite data on /dev/sdb1 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter passphrase: 
Verify passphrase: 
Cannot wipe header on device /dev/sdb1.
Command failed with code 5: Cannot wipe header on device /dev/sdb1.
```

*dmesg* is not reporting anything out of the ordinary:

```
$ dmesg
[ 3208.032228] usb 2-1.4: new high-speed USB device number 7 using ehci-pci
[ 3208.140990] usb 2-1.4: New USB device found, idVendor=059f, idProduct=0651
[ 3208.141001] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3208.141024] usb 2-1.4: Product: LaCie Hard Drive USB
[ 3208.141031] usb 2-1.4: Manufacturer: LaCie
[ 3208.141037] usb 2-1.4: SerialNumber: 10000E000BD8A671
[ 3208.177576] usb-storage 2-1.4:1.0: USB Mass Storage device detected
[ 3208.178112] scsi4 : usb-storage 2-1.4:1.0
[ 3208.178183] usbcore: registered new interface driver usb-storage
[ 3209.176917] scsi 4:0:0:0: Direct-Access     SEAGATE  ST3160812A       3.AA PQ: 0 ANSI: 2
[ 3209.177561] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3209.181342] sd 4:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[ 3209.182337] sd 4:0:0:0: [sdb] Write Protect is off
[ 3209.182348] sd 4:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 3209.183339] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3209.201618]  sdb: sdb1
[ 3209.229465] sd 4:0:0:0: [sdb] Attached SCSI disk
```

In the log a strange message is reporting something with block 0:

```
$ tail /var/log/syslog
Dec  8 09:18:20 MekanikDestruktiwKommandoh kernel: [ 3698.016311] end_request: critical target error, dev sdb, sector 0
Dec  8 09:18:28 MekanikDestruktiwKommandoh wpa_supplicant[1188]: wlan0: CTRL-EVENT-SCAN-STARTED 
```

I have tried writing zeros over sector zero, but cryptsetup returns the same error:

```
$ sudo dd if=/dev/zero of=/dev/sdb1 bs=1M count=10
10+0 records in
10+0 records out
10485760 bytes (10 MB) copied, 0.564427 s, 18.6 MB/s
```

I also tried to wipe the whole thing, but again I recieve a message I can not interpret:

```
$ sudo wipefs -a /dev/sdb
wipefs: WARNING: /dev/sdb: appears to contain 'dos' partition table
```

Any ideas what is going on here? Thank you.

---

### Post by sudodus on 2015-12-09
Try to use the guided standard method of making an encrypted disk. See for example the following link (actually made for testing, but it works also for making a system that you intend to use - but install a released version of Ubuntu).

[Install (entire disk with lvm and encryption) in Ubuntu Desktop amd64 for Trusty Daily](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/108409/testcases/1451/results)

---

### Post by lads on 2015-12-09
> **sudodus said:**
> Try to use the guided standard method of making an encrypted disk. See for example the following link (actually made for testing, but it works also for making a system that you intend to use - but install a released version of Ubuntu).

[Install (entire disk with lvm and encryption) in Ubuntu Desktop amd64 for Trusty Daily](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/108409/testcases/1451/results)

Thanks for replying. I am not looking to install the system on this disk, however.

---

### Post by sudodus on 2015-12-09
> **lads said:**
> Thanks for replying. I am not looking to install the system on this disk, however.

???

---

### Post by lads on 2015-12-10
> **sudodus said:**
> ???

This is an external hard drive that I intend to use as a backup for some critical stuff that I prefer to keep encrypted. I do not wish to make it bootable, it is a somewhat bulky piece of hardware. All I want is an encrypted partition expanding over the whole disk.

Thank you.

---

### Post by sudodus on 2015-12-10
I see.

I have not used cryptsetup as a standalone program, so I cannot help you with details. Let us hope someone, who reads this thread, knows better and can help you :-)

---

### Post by sudodus on 2015-12-10
I will move the thread to the security subforum in order to increase the chances that people who can help will find it.

---


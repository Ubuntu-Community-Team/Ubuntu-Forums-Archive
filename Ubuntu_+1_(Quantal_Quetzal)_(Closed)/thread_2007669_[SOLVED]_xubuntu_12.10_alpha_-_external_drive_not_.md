---
title: "[SOLVED] xubuntu 12.10 alpha - external drive not detected"
date: 2012-06-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by plasmafusion on 2012-06-21
hi all.
just got a new desktop and stuck xubuntu 12.10 alpha on there. this is all running fine on my laptop.
everything's ok except for the fact that my external hard drive isn't detected. this is a bit of a problem as it has all my backups on it and i can't, therefore, restore anything to the new system.
it was plugged in and detected when i installed (to clean partitions).
running dmesg after unplugging it and plugging it back in gives me...

```
[  221.646717] usb 1-3: new high-speed USB device number 5 using ehci_hcd
[  221.781323] scsi8 : usb-storage 1-3:1.0
[  222.780073] scsi 8:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[  222.781806] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  222.782560] sd 8:0:0:0: [sdb] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[  222.784887] sd 8:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  222.786748] sd 8:0:0:0: [sdb] Asking for cache data failed
[  222.786755] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  222.788921] sd 8:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  222.789793] sd 8:0:0:0: [sdb] Asking for cache data failed
[  222.789798] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  222.801075]  sdb: sdb1
[  222.803927] sd 8:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  222.804794] sd 8:0:0:0: [sdb] Asking for cache data failed
[  222.804801] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  222.804807] sd 8:0:0:0: [sdb] Attached SCSI disk
```

but nothing is mounted in /media and it doesn't appear if i issue a df.
lsusb gives
> Bus 001 Device 005: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 004 Device 002: ID 1c4f:000e SiGma Micro Genius KB-120 Keyboard
Bus 005 Device 002: ID 046d:c052 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ever though it's a 1TB drive.
could do with some suggestions if anyone has any ideas.
cheers.

---

### Post by Elfy on 2012-06-21
Yep - [https://bugs.launchpad.net/bugs/1014632](https://bugs.launchpad.net/bugs/1014632)

Install udisks2

Reboot and it should be there.

Please post Quantal bugs in the Quantal forum.

BE useful if you me too the bug as well.

I'd not be wanting to run it as a production system atm as an aside :)

---

### Post by plasmafusion on 2012-06-21
yup...that did the trick.
i really appreciate you help and quick reply.
added to the launchpad bug.

(and sorry for posting in the wrong section...)

---

### Post by Elfy on 2012-06-21
> **plasmafusion said:**
> yup...that did the trick.
i really appreciate you help and quick reply.
added to the launchpad bug.

(and sorry for posting in the wrong section...)

It was only quick because I am trying to do daily testing on the xubuntu iso's ... 

If you want to help - they'd love it in xubuntu-devel :)

---

### Post by plasmafusion on 2012-06-21
i always run ubuntu alphas until the rc comes out...then move onto something else until the next one.

---

### Post by Elfy on 2012-06-21
more or less the same here :)

---

### Post by jerrylamos on 2012-06-22
I test with a USB hard drive, really a left over laptop drive in a $10 case.  Has been working fine except today 22 June i386.iso on a USB flash drive,

Booted the USB flash drive tried installing onto the USB hard drive things ran slower and slower then nothing.  Tried again no go.  Wild guess maybe ubiquity didn't like two USB drives.  

So I booted the .iso file on the usb hard drive direct by appending this to the /etc/grub.d/40_custom and doing sudo update-grub, sudo grub-install /dev/sdb  in this case I'm set up to boot off the USB hard drive.
```

menuentry "quantal sdb6" {
set isofile="/quantal-desktop-i386.iso"
insmod part_gpt
loopback loop (hd0,6)$isofile 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}
```
Do note the funny that hd0,6 worked but hd1,6 as the b drive should have.
After rebooting in terminal Ctrl-Alt-t do df and look for the appropriate /isoodevice entry in this case:
/dev/sdb6        ...    /isodevice
then do a sudo umount -r -l /dev/sdb6
Then install.

Did it with i386 and amd64 today fine (well, a launchpad bug investigation).

Have fun,

Jerry

---


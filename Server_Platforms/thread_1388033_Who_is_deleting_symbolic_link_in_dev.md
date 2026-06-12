---
title: "Who is deleting symbolic link in /dev?"
date: 2010-01-22
forum: Server Platforms
---

### Post by jeffbarish on 2010-01-22
I create a symbolic link for /dev/sr0 to cdrom because a library that I use is hardwired to /dev/cdrom.  After a reboot, the symbolic link is gone.  Who is deleting it, and how can I make him stop?

---

### Post by BobVila on 2010-01-22
That was me. Sorry.

In all seriousness, /dev resides only in memory and is created by udev at boot. You'll need to write a startup script to create the symlink if you want it (semi-)permanent. You might be able to add something into udev to do this as well, but I've never monkeyed with it, so I'm blank on the particulars.

---

### Post by sisco311 on 2010-01-22
> **jeffbarish said:**
> I create a symbolic link for /dev/sr0 to cdrom because a library that I use is hardwired to /dev/cdrom.  After a reboot, the symbolic link is gone.  Who is deleting it, and how can I make him stop?

Let's try to write an udev rule.

What's the output of
```
udevadm info --query=all --name=sr0
```?

---

### Post by jeffbarish on 2010-01-22
Wow.  I didn't realize that /dev exists only in memory.  No wonder.  I'll have to read about udev as it's new to me.

Here's the output of udevadm:

$ udevadm info --query=all --name=sr0    
P: /devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sr0
N: sr0                                                                 
S: block/11:0                                                          
S: scd0
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
S: cdrom2
S: cdrw2
S: dvd2
S: dvdrw2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sr0
E: MAJOR=11
E: MINOR=0
E: DEVNAME=/dev/sr0
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_CDROM=1
E: ID_CDROM_CD_R=1
E: ID_CDROM_CD_RW=1
E: ID_CDROM_DVD=1
E: ID_CDROM_DVD_R=1
E: ID_CDROM_DVD_RAM=1
E: ID_CDROM_MRW=1
E: ID_CDROM_MRW_W=1
E: ID_VENDOR=MATSHITA
E: ID_VENDOR_ENC=MATSHITA
E: ID_MODEL=DVD-RAM_UJ875AS
E: ID_MODEL_ENC=DVD-RAM\x20UJ875AS\x20
E: ID_REVISION=1.00
E: ID_TYPE=cd
E: ID_BUS=scsi
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ACL_MANAGE=1
E: GENERATED=1
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/11:0 /dev/scd0 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0 /dev/cdrom2 /dev/cdrw2 /dev/dvd2 /dev/dvdrw2


Hey.  Is this also how my network interfaces get named?  I've been wondering why they are eth0 or wlan0 on some platforms but eth1 or wlan1 on others.  I'd like to find a way to guarantee consistency.

---

### Post by cdenley on 2010-01-22
> **jeffbarish said:**
> 
Hey.  Is this also how my network interfaces get named?  I've been wondering why they are eth0 or wlan0 on some platforms but eth1 or wlan1 on others.  I'd like to find a way to guarantee consistency.

Look at this file:
/etc/udev/rules.d/70-persistent-net.rules

---

### Post by sisco311 on 2010-01-22
Create a new file in /etc/ude/rules.d
```
gksu gedit /etc/udev/rules.d/99-my-cdrom-rule.rules
```
and add this line to the file:
```
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
```
save the file, cross your fingers and reboot.

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by jeffbarish on 2010-01-22
You got it.  Thanks to all.

---


---
title: "Sheevaplug: USB won't mount at boot as per fstab"
date: 2010-02-08
forum: Server Platforms
---

### Post by khaan on 2010-02-08
Hi,

I've just started playing around with my Sheevaplug. I'm planning to run it with an SD card to store all my server data and a USB stick to regularly back up some of it.

My problem is that the 2 partitions on my SD card mount fine at boot, but my USB stick's single partition does not. Could it be that the mounts specified in fstab are done before my USB device has finished getting alive? Or any other idea?

Mounting the USB stick manually works perfectly well.

fstab
```
# <file system> <mount point> <type> <options> <dump> <pass>

/dev/sda1       /media/usb1   ext2   defaults  0      0
/dev/mmcblk0p1  /media/sd1    ext2   defaults  0      0
/dev/mmcblk0p2  /media/sd2    ext2   defaults  0      0

```

dmesg after boot
```
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
orion-ehci orion-ehci.0: Marvell Orion EHCI
orion-ehci orion-ehci.0: new USB bus registered, assigned bus number 1
orion-ehci orion-ehci.0: irq 19, io mem 0xf1050000
orion-ehci orion-ehci.0: USB 2.0 started, EHCI 1.00
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usbcore: registered new interface driver ums-datafab
usbcore: registered new interface driver ums-freecom
usbcore: registered new interface driver ums-jumpshot
usbcore: registered new interface driver ums-sddr09
usbcore: registered new interface driver ums-sddr55
mice: PS/2 mouse device common for all mice
rtc-mv rtc-mv: rtc core: registered rtc-mv as rtc0
i2c /dev entries driver
cpuidle: using governor ladder
cpuidle: using governor menu
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
mmc0: mvsdio driver initialized, lacking card detect (fall back to polling)
Registered led device: plug:green:health
mv_xor_shared mv_xor_shared.0: Marvell shared XOR driver
mv_xor_shared mv_xor_shared.1: Marvell shared XOR driver
mv_xor mv_xor.0: Marvell XOR: ( xor cpy )
mv_xor mv_xor.1: Marvell XOR: ( xor fill cpy )
mv_xor mv_xor.2: Marvell XOR: ( xor cpy )
mv_xor mv_xor.3: Marvell XOR: ( xor fill cpy )
usbcore: registered new interface driver usbhid
usbhid: v2.6:USB HID core driver
oprofile: using timer interrupt.
TCP cubic registered
NET: Registered protocol family 17
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
lib80211: common routines for IEEE802.11 drivers
lib80211_crypt: registered algorithm 'NULL'
rtc-mv rtc-mv: setting system clock to 2010-02-08 21:27:10 UTC (1265664430)
UBIFS: mounted UBI device 0, volume 0, name "rootfs"
UBIFS: file system size:   515321856 bytes (503244 KiB, 491 MiB, 3994 LEBs)
UBIFS: journal size:       25804800 bytes (25200 KiB, 24 MiB, 200 LEBs)
UBIFS: media format:       w4/r0 (latest is w4/r0)
UBIFS: default compressor: lzo
UBIFS: reserved for root:  4952683 bytes (4836 KiB)
VFS: Mounted root (ubifs filesystem) on device 253:1.
Freeing init memory: 140K
usb 1-1: new high speed USB device using orion-ehci and address 2
mmc0: host does not support reading read-only switch. assuming write-enable.
mmc0: new high speed SDHC card at address 6752
mmcblk0: mmc0:6752 SD16G 14.9 GiB 
 mmcblk0: p1 p2
usb 1-1: configuration #1 chosen from 1 choice
scsi0 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
eth0: link up, 100 Mb/s, full duplex, flow control disabled
scsi 0:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
sd 0:0:0:0: Attached scsi generic sg0 type 0
usb-storage: device scan complete
sd 0:0:0:0: [sda] 31277056 512-byte hardware sectors: (16.0 GB/14.9 GiB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
sd 0:0:0:0: [sda] Assuming drive cache: write through
sd 0:0:0:0: [sda] Assuming drive cache: write through
 sda: sda1
sd 0:0:0:0: [sda] Attached SCSI removable disk
NET: Registered protocol family 10
```

In the dmesg
```
usb-storage: device scan complete
```
comes after
```
EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
```
which makes me think the USB stick has missed the fstab train the 2 SD card partitions are on. And changing the order of the entries in fstab does not make any difference either.

Any idea?
Thanks in advance!


PS: No, I'm not planning to reboot my Sheevaplug every 5 minutes, but I like things to be nice and clean.

---


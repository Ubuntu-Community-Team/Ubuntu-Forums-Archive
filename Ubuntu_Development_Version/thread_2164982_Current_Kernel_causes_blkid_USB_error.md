---
title: "Current Kernel causes blkid USB error"
date: 2013-08-02
forum: Ubuntu Development Version
---

### Post by VMC on 2013-08-02
I have a USB flash stick that I thought Ubuntu couldn't install. I accidentally left it in, and 5 minutes later it recognized it. 
This scenario played in both current Precise and current Saucy installs. After trying with previous distros, I determined it was something current.

After goggling around for a while, I determined it may be the kernel, which it was. So using the mainline kernels I installed kernel "3.2.37-030237-generic" from around January 2013. The USB now works. "kernel 3.8.0-28-generic" fails.

Now I'm unsure if I need to find the last kernel that works or just try and make sense on a Launchpad bug report. Any ideas? Anyone else try USB flash disk recently. I though it was just one 8GB, but later I found several more that fails.

Here's the *syslog* report that shows the failure and a "*blkid -o udev*" 30 times failure. Right after that it installs the flash disk:

```
Aug  2 09:04:10 u kernel: [  168.632651] usb 1-8: new high-speed USB device number 8 using ehci-pciAug  2 09:04:10 u kernel: [  168.767840] usb 1-8: New USB device found, idVendor=090c, idProduct=1000
Aug  2 09:04:10 u kernel: [  168.767853] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug  2 09:04:10 u kernel: [  168.767860] usb 1-8: Product: Flash Disk
Aug  2 09:04:10 u kernel: [  168.767866] usb 1-8: Manufacturer: USB 2.0
Aug  2 09:04:10 u kernel: [  168.767871] usb 1-8: SerialNumber: A128000000000155
Aug  2 09:04:10 u kernel: [  168.769010] scsi8 : usb-storage 1-8:1.0
Aug  2 09:04:10 u mtp-probe: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-8"
Aug  2 09:04:10 u mtp-probe: bus: 1, device: 8 was not an MTP device
Aug  2 09:04:11 u kernel: [  169.767608] scsi 8:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
Aug  2 09:04:11 u kernel: [  169.769779] sd 8:0:0:0: Attached scsi generic sg2 type 0
Aug  2 09:04:11 u kernel: [  169.775569] sd 8:0:0:0: [sdb] 15858688 512-byte logical blocks: (8.11 GB/7.56 GiB)
Aug  2 09:04:11 u kernel: [  169.776673] sd 8:0:0:0: [sdb] Write Protect is off
Aug  2 09:04:11 u kernel: [  169.776679] sd 8:0:0:0: [sdb] Mode Sense: 43 00 00 00
Aug  2 09:04:11 u kernel: [  169.777794] sd 8:0:0:0: [sdb] No Caching mode page present
Aug  2 09:04:11 u kernel: [  169.777800] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Aug  2 09:04:42 u kernel: [  200.587034] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:05:13 u kernel: [  231.587589] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:05:44 u kernel: [  262.492379] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:06:15 u kernel: [  293.397169] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:06:15 u kernel: [  293.538184] sd 8:0:0:0: [sdb] No Caching mode page present
Aug  2 09:06:15 u kernel: [  293.538198] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Aug  2 09:06:34 u anacron[972]: Job `cron.daily' started
Aug  2 09:06:34 u anacron[2005]: Updated timestamp for job `cron.daily' to 2013-08-02
Aug  2 09:06:46 u kernel: [  324.301955] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:07:17 u kernel: [  355.206745] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:07:48 u kernel: [  386.239198] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:08:19 u kernel: [  417.144005] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:08:19 u kernel: [  417.329224]  sdb: sdb1
Aug  2 09:08:19 u kernel: [  417.333429] sd 8:0:0:0: [sdb] No Caching mode page present
Aug  2 09:08:19 u kernel: [  417.333444] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Aug  2 09:08:50 u kernel: [  448.048817] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:08:53 u AptDaemon: INFO: Quitting due to inactivity
Aug  2 09:08:53 u AptDaemon: INFO: Quitting was requested
Aug  2 09:09:20 u udevd[1998]: timeout '/sbin/blkid -o udev -p /dev/sdb'
Aug  2 09:09:21 u kernel: [  478.953591] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:09:21 u udevd[1998]: timeout: **killing '/sbin/blkid -o udev -p /dev/sdb**' [2070]
Aug  2 09:09:52  udevd[1998]: last message repeated 30 times
Aug  2 09:09:52 u kernel: [  509.922247] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:09:52 u udevd[1998]: timeout: killing '/sbin/blkid -o udev -p /dev/sdb' [2070]
Aug  2 09:10:23  udevd[1998]: last message repeated 30 times
Aug  2 09:10:23 u kernel: [  540.890890] usb 1-8: reset high-speed USB device number 8 using ehci-pci
Aug  2 09:10:23 u udevd[1998]: '/sbin/blkid -o udev -p /dev/sdb' [2070] terminated by signal 9 (Killed)
Aug  2 09:10:23 u kernel: [  541.025401] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Aug  2 09:10:23 u udevd[1998]: timeout 'udisks-part-id /dev/sdb'
```

Right after the last timeout it installs. This is a constant 5 minute window.

Here's *syslog* with kernel that works:
```
Aug  2 14:18:23 u kernel: [ 1419.012107] usb 1-8: new high-speed USB device number 9 using ehci_hcdAug  2 14:18:24 u kernel: [ 1419.148565] scsi9 : usb-storage 1-8:1.0
Aug  2 14:18:24 u mtp-probe: checking bus 1, device 9: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-8"
Aug  2 14:18:24 u mtp-probe: bus: 1, device: 9 was not an MTP device
Aug  2 14:18:25 u kernel: [ 1420.149853] scsi 9:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
Aug  2 14:18:25 u kernel: [ 1420.151908] sd 9:0:0:0: Attached scsi generic sg4 type 0
Aug  2 14:18:25 u kernel: [ 1420.155292] sd 9:0:0:0: [sdd] 15858688 512-byte logical blocks: (8.11 GB/7.56 GiB)
Aug  2 14:18:25 u kernel: [ 1420.156394] sd 9:0:0:0: [sdd] Write Protect is off
Aug  2 14:18:25 u kernel: [ 1420.156403] sd 9:0:0:0: [sdd] Mode Sense: 43 00 00 00
Aug  2 14:18:25 u kernel: [ 1420.157510] sd 9:0:0:0: [sdd] No Caching mode page present
Aug  2 14:18:25 u kernel: [ 1420.157518] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug  2 14:18:25 u kernel: [ 1420.163544] sd 9:0:0:0: [sdd] No Caching mode page present
Aug  2 14:18:25 u kernel: [ 1420.163555] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug  2 14:18:25 u kernel: [ 1420.213491]  sdd: sdd1
Aug  2 14:18:25 u kernel: [ 1420.217811] sd 9:0:0:0: [sdd] No Caching mode page present
Aug  2 14:18:25 u kernel: [ 1420.217823] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug  2 14:18:25 u kernel: [ 1420.217832] sd 9:0:0:0: [sdd] Attached SCSI removable disk
Aug  2 14:18:25 u ntfs-3g[2472]: Version 2012.1.15AR.1 external FUSE 28
Aug  2 14:18:25 u ntfs-3g[2472]: Mounted /dev/sdd1 (Read-Write, label "MUSIC", NTFS 3.1)
Aug  2 14:18:25 u ntfs-3g[2472]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Aug  2 14:18:25 u ntfs-3g[2472]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdd1,blkdev,blksize=4096
Aug  2 14:18:25 u ntfs-3g[2472]: Global ownership and permissions enforced, configuration type 7

``` It installs immediately. 

I'll see if anyone else experience this same issue, before I file a bug report. Its a obscure error and unsure what to look for at Launchpad.

---

### Post by VMC on 2013-08-10
Fix released. Here's the patch:```

--- a/drivers/scsi/scsi.c    2013-08-06 11:06:38.358141689 -0400
+++ b/drivers/scsi/scsi.c    2013-08-06 11:08:27.455094545 -0400
@@ -1031,6 +1031,9 @@ int scsi_get_vpd_page(struct scsi_device
 {
     int i, result;
 
+    if (sdev->skip_vpd_pages)
+        goto fail;
+
     /* Ask for all the pages supported by this device */
     result = scsi_vpd_inquiry(sdev, buf, 0, buf_len);
     if (result)
```

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1207934")

---

### Post by VMC on 2013-08-17
Update. The latest Saucy has the fix installed. I went ahead and install it into my Ubuntu 12.04 system from the mainline kernels, so I can use all my USB devices.

---

### Post by launchpad-mfraz on 2013-08-23
I've recently started seeing this when mouting an Hi-MD drive in Kubuntu 13.04.
Aug 23 15:50:23 Rachael kernel: [13266.199878] usb 2-2: new high-speed USB device number 3 using ehci-pci
Aug 23 15:50:23 Rachael kernel: [13266.337635] usb 2-2: New USB device found, idVendor=054c, idProduct=0287
Aug 23 15:50:23 Rachael kernel: [13266.337639] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 23 15:50:23 Rachael kernel: [13266.337642] usb 2-2: Product: Hi-MD
Aug 23 15:50:23 Rachael kernel: [13266.337644] usb 2-2: Manufacturer: Sony
Aug 23 15:50:23 Rachael kernel: [13266.337646] usb 2-2: SerialNumber: 02000129E482
Aug 23 15:50:23 Rachael kernel: [13266.532203] scsi9 : usb-storage 2-2:1.0
Aug 23 15:50:23 Rachael mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2"
Aug 23 15:50:23 Rachael mtp-probe: bus: 2, device: 3 was not an MTP device
Aug 23 15:50:24 Rachael kernel: [13267.532844] scsi 9:0:0:0: Direct-Access     SONY     Hi-MD WALKMAN    1000 PQ: 0 ANSI: 0 CCS
Aug 23 15:50:24 Rachael kernel: [13267.533294] sd 9:0:0:0: Attached scsi generic sg4 type 0
Aug 23 15:50:24 Rachael kernel: [13267.540863] sd 9:0:0:0: [sdd] Attached SCSI removable disk
Aug 23 15:50:27 Rachael kernel: [13269.944854] sd 9:0:0:0: [sdd] 494023 2048-byte logical blocks: (1.01 GB/964 MiB)
Aug 23 15:50:27 Rachael kernel: [13269.948283] sd 9:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 23 15:50:57 Rachael kernel: [13300.203667] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:51:28 Rachael udevd[936]: timeout '/sbin/blkid -o udev -p /dev/sdd'
Aug 23 15:51:28 Rachael kernel: [13331.193471] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:51:29 Rachael udevd[936]: timeout: killing '/sbin/blkid -o udev -p /dev/sdd' [4711]
Aug 23 15:51:59  udevd[936]: last message repeated 30 times
Aug 23 15:51:59 Rachael kernel: [13362.151146] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:52:00 Rachael udevd[936]: timeout: killing '/sbin/blkid -o udev -p /dev/sdd' [4711]
Aug 23 15:52:05  udevd[936]: last message repeated 5 times
Aug 23 15:52:06 Rachael udevd[936]: timeout: killing '/sbin/blkid -o udev -p /dev/sdd' [4711]
Aug 23 15:52:30  udevd[936]: last message repeated 24 times
Aug 23 15:52:30 Rachael kernel: [13393.236599] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:52:30 Rachael kernel: [13393.378142] sd 9:0:0:0: [sdd] 494023 2048-byte logical blocks: (1.01 GB/964 MiB)
Aug 23 15:52:31 Rachael udevd[936]: timeout: killing '/sbin/blkid -o udev -p /dev/sdd' [4711]
Aug 23 15:53:01  udevd[936]: last message repeated 30 times
Aug 23 15:53:01 Rachael kernel: [13424.130375] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:53:02 Rachael udevd[936]: timeout: killing '/sbin/blkid -o udev -p /dev/sdd' [4711]
Aug 23 15:53:32  udevd[936]: last message repeated 30 times
Aug 23 15:53:32 Rachael kernel: [13455.152042] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:53:33 Rachael udevd[936]: timeout: killing '/sbin/blkid -o udev -p /dev/sdd' [4711]
Aug 23 15:54:03  udevd[936]: last message repeated 30 times
Aug 23 15:54:03 Rachael kernel: [13486.109599] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:54:04 Rachael udevd[936]: timeout: killing '/sbin/blkid -o udev -p /dev/sdd' [4711]
Aug 23 15:54:34  udevd[936]: last message repeated 30 times
Aug 23 15:54:34 Rachael kernel: [13517.067301] usb 2-2: reset high-speed USB device number 3 using ehci-pci
Aug 23 15:54:34 Rachael udevd[936]: '/sbin/blkid -o udev -p /dev/sdd' [4711] terminated by signal 9 (Killed)
Aug 23 15:54:34 Rachael udevd[936]: timeout 'udisks-part-id /dev/sdd'
Aug 23 15:54:34 Rachael kernel: [13517.385930]  sdd: unknown partition table

---

### Post by VMC on 2013-08-23
Those were the exact messages I got also, before updating the kernel.

---


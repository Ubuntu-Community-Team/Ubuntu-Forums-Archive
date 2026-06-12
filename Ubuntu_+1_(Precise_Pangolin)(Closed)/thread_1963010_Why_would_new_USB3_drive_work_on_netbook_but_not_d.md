---
title: "Why would new USB3 drive work on netbook but not desktop?"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tehowe on 2012-04-21
This is a wierd one...

I plug this new Hitachi 3TB external drive into my desktop with USB3, and it shows up in disk utility as 3TB and will not format. Syslog spits this out when I plug it in

```
Apr 21 21:13:11 galt kernel: [298201.876093] usb 2-3: new high-speed USB device number 24 using ehci_hcd
Apr 21 21:13:12 galt mtp-probe: checking bus 2, device 24: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3"
Apr 21 21:13:12 galt kernel: [298202.021992] scsi31 : uas
Apr 21 21:13:12 galt mtp-probe: bus: 2, device: 24 was not an MTP device
Apr 21 21:13:21 galt kernel: [298211.255448] scsi 31:0:0:0: Direct-Access     Hitachi  Hitachi HDS72303 A5C0 PQ: 0 ANSI: 4
Apr 21 21:13:24 galt lvpnc[3235]: [linkState.c:327] Ping ok but DNS Down from:172.27.0.7 to 198.41.0.4 135.23 ms
Apr 21 21:13:27 galt kernel: [298217.808111] scsi 31:0:0:0: uas_eh_abort_handler tag 0
Apr 21 21:13:27 galt kernel: [298217.808128] scsi 31:0:0:0: uas_eh_device_reset_handler tag 0
Apr 21 21:13:27 galt kernel: [298217.808137] scsi 31:0:0:0: uas_eh_target_reset_handler tag 0
Apr 21 21:13:27 galt kernel: [298217.808144] scsi 31:0:0:0: uas_eh_bus_reset_handler tag 0
Apr 21 21:13:27 galt kernel: [298217.920078] usb 2-3: reset high-speed USB device number 24 using ehci_hcd
Apr 21 21:13:28 galt kernel: [298218.054755] scsi 31:0:0:0: Device offlined - not ready after error recovery
Apr 21 21:13:28 galt kernel: [298218.054837] scsi 31:0:0:0: rejecting I/O to offline device
Apr 21 21:13:28 galt kernel: [298218.054861] scsi 31:0:0:0: rejecting I/O to offline device
Apr 21 21:13:28 galt kernel: [298218.056295] scsi 31:0:0:1: Enclosure         Hitachi  SES              A5C0 PQ: 0 ANSI: 4
Apr 21 21:13:28 galt kernel: [298218.056760] scsi 31:0:0:2: uas_eh_device_reset_handler tag -1
Apr 21 21:13:28 galt kernel: [298218.056771] scsi 31:0:0:2: uas_eh_target_reset_handler tag -1
Apr 21 21:13:28 galt kernel: [298218.056779] scsi 31:0:0:2: uas_eh_bus_reset_handler tag -1
Apr 21 21:13:28 galt kernel: [298218.172108] usb 2-3: reset high-speed USB device number 24 using ehci_hcd
Apr 21 21:13:28 galt kernel: [298218.306001] scsi 31:0:0:2: Device offlined - not ready after error recovery
Apr 21 21:13:28 galt kernel: [298218.306272] sd 31:0:0:0: Attached scsi generic sg8 type 0
Apr 21 21:13:28 galt kernel: [298218.306550] ses 31:0:0:1: Attached Enclosure device
Apr 21 21:13:28 galt kernel: [298218.306722] ses 31:0:0:1: Attached scsi generic sg9 type 13
Apr 21 21:13:58 galt kernel: [298248.800129] sd 31:0:0:0: uas_eh_abort_handler tag 0
Apr 21 21:13:58 galt kernel: [298248.800147] sd 31:0:0:0: uas_eh_device_reset_handler tag 0
Apr 21 21:13:58 galt kernel: [298248.800156] sd 31:0:0:0: uas_eh_target_reset_handler tag 0
Apr 21 21:13:58 galt kernel: [298248.800163] sd 31:0:0:0: uas_eh_bus_reset_handler tag 0
Apr 21 21:13:58 galt kernel: [298248.912137] usb 2-3: reset high-speed USB device number 24 using ehci_hcd
Apr 21 21:13:59 galt kernel: [298249.046722] sd 31:0:0:0: Device offlined - not ready after error recovery
Apr 21 21:13:59 galt kernel: [298249.046775] sd 31:0:0:0: rejecting I/O to offline device
Apr 21 21:13:59 galt kernel: [298249.046784] sd 31:0:0:0: rejecting I/O to offline device
Apr 21 21:13:59 galt kernel: [298249.046786] sd 31:0:0:0: rejecting I/O to offline device
Apr 21 21:13:59 galt kernel: [298249.046788] sd 31:0:0:0: [sdg] READ CAPACITY failed
Apr 21 21:13:59 galt kernel: [298249.046790] sd 31:0:0:0: [sdg]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 21 21:13:59 galt kernel: [298249.046792] sd 31:0:0:0: [sdg] Sense not available.
Apr 21 21:13:59 galt kernel: [298249.046795] sd 31:0:0:0: rejecting I/O to offline device
Apr 21 21:13:59 galt kernel: [298249.046798] sd 31:0:0:0: [sdg] Write Protect is off
Apr 21 21:13:59 galt kernel: [298249.046800] sd 31:0:0:0: [sdg] Mode Sense: 00 00 00 00
Apr 21 21:13:59 galt kernel: [298249.046801] sd 31:0:0:0: rejecting I/O to offline device
Apr 21 21:13:59 galt kernel: [298249.046803] sd 31:0:0:0: [sdg] Asking for cache data failed
Apr 21 21:13:59 galt kernel: [298249.046805] sd 31:0:0:0: [sdg] Assuming drive cache: write through
Apr 21 21:13:59 galt kernel: [298249.046980] sd 31:0:0:0: [sdg] Attached SCSI disk
Apr 21 21:13:59 galt ata_id[7195]: unable to open '/dev/sdg'

```

Plug it in using USB 2, and disk utility doesn't even know how big the partition is.

Meanwhile, I plug it into my netbook on USB 2 and it comes up in Nautilus as a 3GB NTFS drive with no problems.

Any ideas?

---

### Post by 23dornot23d on 2012-04-21
Could possibly be a BIOS issue ..... unless it worked ok before on a earlier version .....

Just had a [[COLOR=Blue]_quick search around_[/COLOR]]("https://www.google.com/search?q=P55+%28Asus%29+USB3.0+enabled+boards&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=en&client=firefox-a&hs=GN7&rls=org.mozilla:en-US%3Aofficial&sclient=psy-ab&q=USB3.0+enabled+boards+problems&oq=USB3.0+enabled+boards+problems&aq=f&aqi=&aql=&gs_nf=1&gs_l=serp.3...22600.22899.2.23535.4.3.0.0.0.1.272.634.0j1j2.3.0.5MMBuqrywK0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=e4ccbfb3a99689c7") ..... but without knowing what desktop and motherboard
its hard to say .....

---

### Post by dcstar on 2012-04-21
> **tehowe said:**
> 
.........
Meanwhile, I plug it into my netbook on USB 2 and it comes up in Nautilus as a 3GB NTFS drive with no problems.

Any ideas?

Different hardware.

The desktop's USB ports may not be powering the device sufficiently, or they are just not supported by the kernel correctly.

---

### Post by 23dornot23d on 2012-04-22
This is a interesting read - its long and its from a USER that has problems between
rear and and front USB 3.0 ports ....

[http://communities.intel.com/thread/27066?start=0&tstart=0](http://communities.intel.com/thread/27066?start=0&tstart=0)

Although it is related to Windows and not aimed at Linux ...... the fact that front and 
rear ports on the same machine work differently ..... may give you a point to check .....

See if there is any difference on your desktop machine .... if it has front and rear
USB ports ......

As said it would be interesting if a USB device could be plugged in that measures transfer rates / power etc ....... but it is mentioned in that thread ..... about the type and quality of the connecting cable from the motherboard to the front ports ......

What motherboard and what Desktop Case is it ..... maybe there is a similarity ..... to the 
above thread .....

Hope some of this is of use .....

---

### Post by tehowe on 2012-04-22
My mobo's an 'Asus M4A88TD-V EVO/USB3', and it's driven by an AMD Phenom 1090T CPU.

I don't think the problem is inherent to USB3 itself, as I can plug in a WD MyPassport drive which comes up just fine.

I don't think the problem is power, because the MyPassport is powered by the USB3 port, while this Hitachi 'Turbo Desk Pro' has its own supply.

I've three front ports but they're all USB2, two on the case (Antec) and one on a front-mounted multimedia reader... none of these ports work for this drive. 

The two USB3 ports are at the back. They won't work. There's an additional two USB2 ports at the back which won't work either, for this drive.

For reference, here's what happens when I plug in the working WD MyPassport over USB3

```
Apr 22 07:10:23 galt kernel: [ 1744.040255] usb 9-1: new SuperSpeed USB device number 5 using xhci_hcd
Apr 22 07:10:23 galt kernel: [ 1744.061090] scsi20 : usb-storage 9-1:1.0
Apr 22 07:10:23 galt mtp-probe: checking bus 9, device 5: "/sys/devices/pci0000:00/0000:00:0a.0/0000:03:00.0/usb9/9-1"
Apr 22 07:10:23 galt mtp-probe: bus: 9, device: 5 was not an MTP device
Apr 22 07:10:24 galt kernel: [ 1745.060934] scsi 20:0:0:0: Direct-Access     WD       My Passport 0740 1003 PQ: 0 ANSI: 6
Apr 22 07:10:24 galt kernel: [ 1745.061258] scsi 20:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Apr 22 07:10:24 galt kernel: [ 1745.062771] sd 20:0:0:0: Attached scsi generic sg10 type 0
Apr 22 07:10:24 galt kernel: [ 1745.062966] ses 20:0:0:1: Attached Enclosure device
Apr 22 07:10:24 galt kernel: [ 1745.063141] ses 20:0:0:1: Attached scsi generic sg11 type 13
Apr 22 07:10:29 galt iptables: -j LOG: kernel: [ 1750.115343] [UFW BLOCK]  {TCP} nx-in-f188.1e100.net(209.85.175.188):5228 -> 172.27.0.60:60303
Apr 22 07:10:30 galt kernel: [ 1750.977639] sd 20:0:0:0: [sdi] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
Apr 22 07:10:30 galt kernel: [ 1750.978776] sd 20:0:0:0: [sdi] Write Protect is off
Apr 22 07:10:30 galt kernel: [ 1750.978788] sd 20:0:0:0: [sdi] Mode Sense: 47 00 10 08
Apr 22 07:10:30 galt kernel: [ 1750.979515] sd 20:0:0:0: [sdi] No Caching mode page present
Apr 22 07:10:30 galt kernel: [ 1750.979525] sd 20:0:0:0: [sdi] Assuming drive cache: write through
Apr 22 07:10:30 galt kernel: [ 1750.984365] sd 20:0:0:0: [sdi] No Caching mode page present
Apr 22 07:10:30 galt kernel: [ 1750.984375] sd 20:0:0:0: [sdi] Assuming drive cache: write through
Apr 22 07:10:30 galt kernel: [ 1750.999678]  sdi: sdi1
Apr 22 07:10:30 galt kernel: [ 1751.002895] sd 20:0:0:0: [sdi] No Caching mode page present
Apr 22 07:10:30 galt kernel: [ 1751.002905] sd 20:0:0:0: [sdi] Assuming drive cache: write through
Apr 22 07:10:30 galt kernel: [ 1751.002913] sd 20:0:0:0: [sdi] Attached SCSI disk
Apr 22 07:10:30 galt ata_id[5474]: HDIO_GET_IDENTITY failed for '/dev/sdi': Invalid argument
Apr 22 07:10:49 galt kernel: [ 1769.344387] EXT4-fs (dm-4): mounted filesystem with ordered data mode. Opts: (null)

```Here's hooking up the Hitachi to the desktop USB3 port again

```
Apr 22 07:12:45 galt kernel: [ 1885.364219] usb 9-2: new SuperSpeed USB device number 6 using xhci_hcd
Apr 22 07:12:45 galt mtp-probe: checking bus 9, device 6: "/sys/devices/pci0000:00/0000:00:0a.0/0000:03:00.0/usb9/9-2"
Apr 22 07:12:45 galt kernel: [ 1885.390276] scsi21 : uas
Apr 22 07:12:45 galt mtp-probe: bus: 9, device: 6 was not an MTP device
Apr 22 07:12:57 galt kernel: [ 1897.498530] scsi 21:0:0:0: Direct-Access     Hitachi  Hitachi HDS72303 A5C0 PQ: 0 ANSI: 4
Apr 22 07:12:57 galt kernel: [ 1897.498999] sd 21:0:0:0: [sdj] 732566016 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Apr 22 07:12:57 galt kernel: [ 1897.499143] sd 21:0:0:0: [sdj] Write Protect is off
Apr 22 07:12:57 galt kernel: [ 1897.499151] sd 21:0:0:0: [sdj] Mode Sense: 4b 00 10 08
Apr 22 07:12:57 galt kernel: [ 1897.499163] sd 21:0:0:0: Attached scsi generic sg12 type 0
Apr 22 07:12:57 galt kernel: [ 1897.499412] xhci_hcd 0000:03:00.0: WARN Set TR Deq Ptr cmd invalid because of stream ID configuration
Apr 22 07:12:57 galt kernel: [ 1897.499453] xhci_hcd 0000:03:00.0: ERROR Transfer event for disabled endpoint or incorrect stream ring
Apr 22 07:13:07 galt kernel: [ 1907.496089] sd 21:0:0:0: uas_eh_abort_handler tag 0
Apr 22 07:13:07 galt kernel: [ 1907.496099] sd 21:0:0:0: uas_eh_device_reset_handler tag 0
Apr 22 07:13:07 galt kernel: [ 1907.496106] sd 21:0:0:0: uas_eh_target_reset_handler tag 0
Apr 22 07:13:07 galt kernel: [ 1907.496112] sd 21:0:0:0: uas_eh_bus_reset_handler tag 0
Apr 22 07:13:07 galt kernel: [ 1907.609153] usb 9-2: reset SuperSpeed USB device number 6 using xhci_hcd
Apr 22 07:13:07 galt kernel: [ 1907.626332] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b800
Apr 22 07:13:07 galt kernel: [ 1907.626344] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b840
Apr 22 07:13:07 galt kernel: [ 1907.626352] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b880
Apr 22 07:13:07 galt kernel: [ 1907.626359] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b8c0
Apr 22 07:13:07 galt kernel: [ 1907.628087] usb 9-2: URB BAD STATUS -108
Apr 22 07:13:07 galt kernel: [ 1907.628378] sd 21:0:0:0: uas_eh_device_reset_handler tag 0
Apr 22 07:13:07 galt kernel: [ 1907.628388] sd 21:0:0:0: uas_eh_target_reset_handler tag 0
Apr 22 07:13:07 galt kernel: [ 1907.628395] sd 21:0:0:0: uas_eh_bus_reset_handler tag 0
Apr 22 07:13:07 galt kernel: [ 1907.741114] usb 9-2: reset SuperSpeed USB device number 6 using xhci_hcd
Apr 22 07:13:07 galt kernel: [ 1907.758481] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b800
Apr 22 07:13:07 galt kernel: [ 1907.758492] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b840
Apr 22 07:13:07 galt kernel: [ 1907.758500] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b880
Apr 22 07:13:07 galt kernel: [ 1907.758507] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801a747b8c0
Apr 22 07:13:07 galt kernel: [ 1907.760197] sd 21:0:0:0: Device offlined - not ready after error recovery
Apr 22 07:13:07 galt kernel: [ 1907.760251] sd 21:0:0:0: [sdj] Asking for cache data failed
Apr 22 07:13:07 galt kernel: [ 1907.760262] sd 21:0:0:0: [sdj] Assuming drive cache: write through
Apr 22 07:13:07 galt kernel: [ 1907.760796] sd 21:0:0:0: [sdj] Attached SCSI disk
Apr 22 07:13:07 galt ata_id[5616]: unable to open '/dev/sdj'
```

And then finally, an example of the Hitachi playing nice with an Acer 1410 netbook over USB2

```
Apr 22 07:21:55 akston kernel: [52174.928063] usb 2-1: new high-speed USB device number 5 using ehci_hcd
Apr 22 07:21:55 akston kernel: [52175.063332] scsi8 : usb-storage 2-1:1.0
Apr 22 07:21:55 akston mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1"
Apr 22 07:21:55 akston mtp-probe: bus: 2, device: 5 was not an MTP device
Apr 22 07:22:10 akston kernel: [52190.363693] scsi 8:0:0:0: Direct-Access     Hitachi  Hitachi HDS72303 A5C0 PQ: 0 ANSI: 4
Apr 22 07:22:10 akston kernel: [52190.365256] sd 8:0:0:0: Attached scsi generic sg2 type 0
Apr 22 07:22:10 akston kernel: [52190.366906] sd 8:0:0:0: [sdc] 732566016 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Apr 22 07:22:10 akston kernel: [52190.369769] sd 8:0:0:0: [sdc] Write Protect is off
Apr 22 07:22:10 akston kernel: [52190.369776] sd 8:0:0:0: [sdc] Mode Sense: 4b 00 10 08
Apr 22 07:22:10 akston kernel: [52190.371443] sd 8:0:0:0: [sdc] No Caching mode page present
Apr 22 07:22:10 akston kernel: [52190.371451] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Apr 22 07:22:10 akston kernel: [52190.373235] sd 8:0:0:0: [sdc] 732566016 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Apr 22 07:22:10 akston kernel: [52190.378518] sd 8:0:0:0: [sdc] No Caching mode page present
Apr 22 07:22:10 akston kernel: [52190.378526] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Apr 22 07:22:10 akston kernel: [52190.396218]  sdc: sdc1
Apr 22 07:22:10 akston kernel: [52190.397394] sd 8:0:0:0: [sdc] 732566016 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Apr 22 07:22:10 akston kernel: [52190.398905] sd 8:0:0:0: [sdc] No Caching mode page present
Apr 22 07:22:10 akston kernel: [52190.398912] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Apr 22 07:22:10 akston kernel: [52190.398918] sd 8:0:0:0: [sdc] Attached SCSI disk
Apr 22 07:22:10 akston ata_id[10053]: HDIO_GET_IDENTITY failed for '/dev/sdc': Invalid argument
Apr 22 07:22:13 akston ntfs-3g[10077]: Version 2012.1.15AR.1 external FUSE 28
Apr 22 07:22:13 akston ntfs-3g[10077]: Mounted /dev/sdc1 (Read-Write, label "Hitachi", NTFS 3.1)
Apr 22 07:22:13 akston ntfs-3g[10077]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Apr 22 07:22:13 akston ntfs-3g[10077]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdc1,blkdev,blksize=4096
Apr 22 07:22:13 akston ntfs-3g[10077]: Global ownership and permissions enforced, configuration type 7

```

---

### Post by tehowe on 2012-04-22
> **tehowe said:**
> My mobo's an 'Asus M4A88TD-V EVO/USB3', and it's driven by an AMD Phenom 1090T CPU.

I don't think the problem is inherent to USB3 itself, as I can plug in a WD MyPassport drive which comes up just fine.

I don't think the problem is power, because the MyPassport is powered by the USB3 port, while this Hitachi 'Turbo Desk Pro' has its own supply.

I've three front ports but they're all USB2, two on the case (Antec) and one on a front-mounted multimedia reader... none of these ports work for this drive. 

The two USB3 ports are at the back. They won't work. There's an additional two USB2 ports at the back which won't work either, for this drive.


I've updated the bios to the latest version (v.2001, not the year!) and still no dice. It remains 'offlined' by the kernel and has 'URB BAD STATUS -108'

---

### Post by dcstar on 2012-04-24
The answer remains the same to the question of this thread: Different hardware.

The USB3 drive is incompatible with the hardware on that machine. Report it as a kernel bug.

---

### Post by tehowe on 2012-04-24
> **dcstar said:**
> The answer remains the same to the question of this thread: Different hardware.

The USB3 drive is incompatible with the hardware on that machine. Report it as a kernel bug.

Hi, fair enough, I'll return the drive and file a kernel bug, that goes against the 'linux' package by the looks of it.

Readers can find it here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987882](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987882)

Thanks

---


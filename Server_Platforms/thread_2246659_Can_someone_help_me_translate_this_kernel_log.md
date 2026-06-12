---
title: "Can someone help me translate this kernel log?"
date: 2014-10-02
forum: Server Platforms
---

### Post by MakOwner on 2014-10-02
It's a wall of text, so I am putting in a link to a text file, rather than pasting it here.
If it's prefereable to put it here, let me know and I will.

I have an external enclosure with a SAS expander, connected via an LSI1068E quad port PCIe card.
The shelf is purchased surplus.
 
After 8 - 12 hours of mostly idle utilization (maybe I/O to one disk) the shelf and all of the disks disappear off the bus.
There is another identical shelf attached to a different port on the same LSI1068E card where this does nto happen.

I'm tryng to determine if the shelf/SAS expander, the SAS cable or the port on the LSI1068E may be the source of the issue.

Can anyone tell me if there is enough information in this log to make that determination?


kern.log snippet of the event -> [http://www.rose-dale.com/shelf_fail.txt]("http://www.rose-dale.com/shelf_fail.txt")

---

### Post by MakOwner on 2014-10-06
No one?
Anyone even have a hint as to where I could take this?

---

### Post by nerdtron on 2014-10-06
How many drives do you have? How many are attached to the SAS controller? So you configured software raid in Ubuntu?
```
Oct  2 08:14:09 PE850-07 kernel: [65082.987565] md/raid:md127: Disk failure on sdj1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65082.987565] md/raid:md127: Operation continuing on 11 devices.
Oct  2 08:14:09 PE850-07 kernel: [65082.991391] md/raid:md127: Disk failure on sdc1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65082.991391] md/raid:md127: Operation continuing on 10 devices.
Oct  2 08:14:09 PE850-07 kernel: [65082.993033] md/raid:md127: Disk failure on sdk1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65082.993033] md/raid:md127: Operation continuing on 9 devices.
Oct  2 08:14:09 PE850-07 kernel: [65082.994552] md/raid:md127: Disk failure on sdg1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65082.994552] md/raid:md127: Operation continuing on 8 devices.
Oct  2 08:14:09 PE850-07 kernel: [65082.995964] md/raid:md127: Disk failure on sdi1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65082.995964] md/raid:md127: Operation continuing on 7 devices.
Oct  2 08:14:09 PE850-07 kernel: [65082.999401] md/raid:md127: Disk failure on sdh1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65082.999401] md/raid:md127: Operation continuing on 6 devices.
Oct  2 08:14:09 PE850-07 kernel: [65083.001027] md/raid:md127: Disk failure on sdf1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65083.001027] md/raid:md127: Operation continuing on 5 devices.
Oct  2 08:14:09 PE850-07 kernel: [65083.002436] md/raid:md127: Disk failure on sde1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65083.002436] md/raid:md127: Operation continuing on 4 devices.
Oct  2 08:14:09 PE850-07 kernel: [65083.003835] md/raid:md127: Disk failure on sdm1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65083.003835] md/raid:md127: Operation continuing on 3 devices.
Oct  2 08:14:09 PE850-07 kernel: [65083.006244] md/raid:md127: Disk failure on sdd1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65083.006244] md/raid:md127: Operation continuing on 2 devices.
Oct  2 08:14:09 PE850-07 kernel: [65083.078416] md/raid:md127: Disk failure on sdl1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65083.078416] md/raid:md127: Operation continuing on 1 devices.
Oct  2 08:14:09 PE850-07 kernel: [65083.140062] md/raid:md127: Disk failure on sdo1, disabling device.
Oct  2 08:14:09 PE850-07 kernel: [65083.140062] md/raid:md127: Operation continuing on 0 devices.
Oct  2 08:14:17 PE850-07 kernel: [65091.121368] mptsas: ioc0: add expander: num_phys 25, sas_addr (0x500194000090623f)
Oct  2 08:14:17 PE850-07 kernel: [65091.377565] mptsas: ioc0: attaching ssp device: fw_channel 0, fw_id 13, phy 24, sas_addr 0x500194000090623e
Oct  2 08:14:17 PE850-07 kernel: [65091.387861] scsi 4:0:14:0: Enclosure         RACKABLE SE3016-SAS       0227 PQ: 0 ANSI: 5
Oct  2 08:14:17 PE850-07 kernel: [65091.395319] ses 4:0:14:0: Attached Enclosure device
Oct  2 08:14:17 PE850-07 kernel: [65091.399510] ses 4:0:14:0: Attached scsi generic sg3 type 13
Oct  2 08:14:23 PE850-07 kernel: [65097.055350] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 0, phy 0, sas_addr 0x5001940000906200
Oct  2 08:14:23 PE850-07 kernel: [65097.062123] scsi 4:0:15:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:23 PE850-07 kernel: [65097.066481] sd 4:0:15:0: [sdz] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:23 PE850-07 kernel: [65097.069449] sd 4:0:15:0: Attached scsi generic sg4 type 0
Oct  2 08:14:23 PE850-07 kernel: [65097.106278] sd 4:0:15:0: [sdz] Write Protect is off
Oct  2 08:14:23 PE850-07 kernel: [65097.106288] sd 4:0:15:0: [sdz] Mode Sense: 73 00 00 08
Oct  2 08:14:23 PE850-07 kernel: [65097.109064] sd 4:0:15:0: [sdz] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:23 PE850-07 kernel: [65097.126984] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 1, phy 1, sas_addr 0x5001940000906201
Oct  2 08:14:23 PE850-07 kernel: [65097.129768] scsi 4:0:16:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:23 PE850-07 kernel: [65097.131424] sd 4:0:16:0: Attached scsi generic sg5 type 0
Oct  2 08:14:23 PE850-07 kernel: [65097.132760] sd 4:0:16:0: [sdaa] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:23 PE850-07 kernel: [65097.171321] sd 4:0:16:0: [sdaa] Write Protect is off
Oct  2 08:14:23 PE850-07 kernel: [65097.171333] sd 4:0:16:0: [sdaa] Mode Sense: 73 00 00 08
Oct  2 08:14:23 PE850-07 kernel: [65097.175523] sd 4:0:16:0: [sdaa] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:23 PE850-07 kernel: [65097.175820] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 2, phy 2, sas_addr 0x5001940000906202
Oct  2 08:14:23 PE850-07 kernel: [65097.179858] scsi 4:0:17:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:23 PE850-07 kernel: [65097.180887] sd 4:0:17:0: Attached scsi generic sg6 type 0
Oct  2 08:14:23 PE850-07 kernel: [65097.183403] sd 4:0:17:0: [sdab] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:23 PE850-07 kernel: [65097.197574]  sdz: sdz1
Oct  2 08:14:23 PE850-07 kernel: [65097.215924] sd 4:0:17:0: [sdab] Write Protect is off
Oct  2 08:14:23 PE850-07 kernel: [65097.215934] sd 4:0:17:0: [sdab] Mode Sense: 73 00 00 08
Oct  2 08:14:23 PE850-07 kernel: [65097.218501] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 3, phy 3, sas_addr 0x5001940000906203
Oct  2 08:14:23 PE850-07 kernel: [65097.218725] sd 4:0:17:0: [sdab] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:23 PE850-07 kernel: [65097.222154] scsi 4:0:18:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:23 PE850-07 kernel: [65097.222959] sd 4:0:18:0: Attached scsi generic sg7 type 0
Oct  2 08:14:23 PE850-07 kernel: [65097.225408] sd 4:0:18:0: [sdac] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:23 PE850-07 kernel: [65097.237661]  sdaa: sdaa1
Oct  2 08:14:23 PE850-07 kernel: [65097.250922] sd 4:0:15:0: [sdz] Attached SCSI disk
Oct  2 08:14:23 PE850-07 kernel: [65097.274208] sd 4:0:18:0: [sdac] Write Protect is off
Oct  2 08:14:23 PE850-07 kernel: [65097.274218] sd 4:0:18:0: [sdac] Mode Sense: 73 00 00 08
Oct  2 08:14:23 PE850-07 kernel: [65097.276791] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 4, phy 4, sas_addr 0x5001940000906204
Oct  2 08:14:23 PE850-07 kernel: [65097.277022] sd 4:0:18:0: [sdac] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:23 PE850-07 kernel: [65097.279263] scsi 4:0:19:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:23 PE850-07 kernel: [65097.280348] sd 4:0:19:0: Attached scsi generic sg8 type 0
Oct  2 08:14:23 PE850-07 kernel: [65097.281423] sd 4:0:19:0: [sdad] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:23 PE850-07 kernel: [65097.282484]  sdab: sdab1
Oct  2 08:14:23 PE850-07 kernel: [65097.291919] sd 4:0:16:0: [sdaa] Attached SCSI disk
Oct  2 08:14:23 PE850-07 kernel: [65097.320501] sd 4:0:19:0: [sdad] Write Protect is off
Oct  2 08:14:23 PE850-07 kernel: [65097.320510] sd 4:0:19:0: [sdad] Mode Sense: 73 00 00 08
Oct  2 08:14:23 PE850-07 kernel: [65097.323705] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 5, phy 5, sas_addr 0x5001940000906205
Oct  2 08:14:23 PE850-07 kernel: [65097.323934] sd 4:0:19:0: [sdad] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:23 PE850-07 kernel: [65097.325703] scsi 4:0:20:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:23 PE850-07 kernel: [65097.326569] sd 4:0:20:0: Attached scsi generic sg9 type 0
Oct  2 08:14:23 PE850-07 kernel: [65097.328869] sd 4:0:20:0: [sdae] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:23 PE850-07 kernel: [65097.338091] sd 4:0:17:0: [sdab] Attached SCSI disk
Oct  2 08:14:23 PE850-07 kernel: [65097.340542]  sdac: sdac1
Oct  2 08:14:23 PE850-07 kernel: [65097.375508] sd 4:0:20:0: [sdae] Write Protect is off
Oct  2 08:14:23 PE850-07 kernel: [65097.375517] sd 4:0:20:0: [sdae] Mode Sense: 73 00 00 08
Oct  2 08:14:23 PE850-07 kernel: [65097.378364] sd 4:0:20:0: [sdae] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:23 PE850-07 kernel: [65097.386857]  sdad: sdad1
Oct  2 08:14:23 PE850-07 kernel: [65097.395316] sd 4:0:18:0: [sdac] Attached SCSI disk
Oct  2 08:14:23 PE850-07 kernel: [65097.441847]  sdae: sdae1
Oct  2 08:14:24 PE850-07 kernel: [65097.498011] sd 4:0:19:0: [sdad] Attached SCSI disk
Oct  2 08:14:24 PE850-07 kernel: [65097.523796] sd 4:0:20:0: [sdae] Attached SCSI disk
Oct  2 08:14:41 PE850-07 kernel: [65114.467935] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 6, phy 7, sas_addr 0x5001940000906207
Oct  2 08:14:41 PE850-07 kernel: [65114.473742] scsi 4:0:21:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:41 PE850-07 kernel: [65114.474534] sd 4:0:21:0: Attached scsi generic sg10 type 0
Oct  2 08:14:41 PE850-07 kernel: [65114.475616] sd 4:0:21:0: [sdaf] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:41 PE850-07 kernel: [65114.521855] sd 4:0:21:0: [sdaf] Write Protect is off
Oct  2 08:14:41 PE850-07 kernel: [65114.521865] sd 4:0:21:0: [sdaf] Mode Sense: 73 00 00 08
Oct  2 08:14:41 PE850-07 kernel: [65114.526184] sd 4:0:21:0: [sdaf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:41 PE850-07 kernel: [65114.526489] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 9, phy 10, sas_addr 0x500194000090620a
Oct  2 08:14:41 PE850-07 kernel: [65114.531825] scsi 4:0:22:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:41 PE850-07 kernel: [65114.532748] sd 4:0:22:0: Attached scsi generic sg11 type 0
Oct  2 08:14:41 PE850-07 kernel: [65114.533761] sd 4:0:22:0: [sdag] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:41 PE850-07 kernel: [65114.575457] sd 4:0:22:0: [sdag] Write Protect is off
Oct  2 08:14:41 PE850-07 kernel: [65114.575468] sd 4:0:22:0: [sdag] Mode Sense: 73 00 00 08
Oct  2 08:14:41 PE850-07 kernel: [65114.579680] sd 4:0:22:0: [sdag] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:41 PE850-07 kernel: [65114.579980] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 10, phy 11, sas_addr 0x500194000090620b
Oct  2 08:14:41 PE850-07 kernel: [65114.584057] scsi 4:0:23:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:41 PE850-07 kernel: [65114.585086] sd 4:0:23:0: Attached scsi generic sg12 type 0
Oct  2 08:14:41 PE850-07 kernel: [65114.586398] sd 4:0:23:0: [sdah] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:41 PE850-07 kernel: [65114.588282]  sdaf: sdaf1
Oct  2 08:14:41 PE850-07 kernel: [65114.632046] sd 4:0:23:0: [sdah] Write Protect is off
Oct  2 08:14:41 PE850-07 kernel: [65114.632056] sd 4:0:23:0: [sdah] Mode Sense: 73 00 00 08
Oct  2 08:14:41 PE850-07 kernel: [65114.634900] sd 4:0:23:0: [sdah] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:41 PE850-07 kernel: [65114.641614] sd 4:0:21:0: [sdaf] Attached SCSI disk
Oct  2 08:14:41 PE850-07 kernel: [65114.641812]  sdag: sdag1
Oct  2 08:14:41 PE850-07 kernel: [65114.721468] sd 4:0:22:0: [sdag] Attached SCSI disk
Oct  2 08:14:41 PE850-07 kernel: [65114.722606]  sdah: sdah1
Oct  2 08:14:41 PE850-07 kernel: [65114.834518] sd 4:0:23:0: [sdah] Attached SCSI disk
Oct  2 08:14:46 PE850-07 kernel: [65119.660334] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 7, phy 8, sas_addr 0x5001940000906208
Oct  2 08:14:46 PE850-07 kernel: [65119.701589] scsi 4:0:24:0: Direct-Access     ATA      Hitachi HUA72107 A70M PQ: 0 ANSI: 5
Oct  2 08:14:46 PE850-07 kernel: [65119.702427] sd 4:0:24:0: Attached scsi generic sg13 type 0
Oct  2 08:14:46 PE850-07 kernel: [65119.703481] sd 4:0:24:0: [sdai] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:46 PE850-07 kernel: [65119.876530] sd 4:0:24:0: [sdai] Write Protect is off
Oct  2 08:14:46 PE850-07 kernel: [65119.876542] sd 4:0:24:0: [sdai] Mode Sense: 73 00 00 08
Oct  2 08:14:46 PE850-07 kernel: [65119.887535] sd 4:0:24:0: [sdai] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:46 PE850-07 kernel: [65119.887835] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 8, phy 9, sas_addr 0x5001940000906209
Oct  2 08:14:46 PE850-07 kernel: [65119.893275] scsi 4:0:25:0: Direct-Access     ATA      Hitachi HUA72107 AB0A PQ: 0 ANSI: 5
Oct  2 08:14:46 PE850-07 kernel: [65119.894111] sd 4:0:25:0: Attached scsi generic sg14 type 0
Oct  2 08:14:46 PE850-07 kernel: [65119.895100] sd 4:0:25:0: [sdaj] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:46 PE850-07 kernel: [65120.066776] sd 4:0:25:0: [sdaj] Write Protect is off
Oct  2 08:14:46 PE850-07 kernel: [65120.066801] sd 4:0:25:0: [sdaj] Mode Sense: 73 00 00 08
Oct  2 08:14:46 PE850-07 kernel: [65120.077421] sd 4:0:25:0: [sdaj] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:46 PE850-07 kernel: [65120.083058]  sdai: sdai1
Oct  2 08:14:46 PE850-07 kernel: [65120.273108]  sdaj: sdaj1
Oct  2 08:14:46 PE850-07 kernel: [65120.438396] sd 4:0:24:0: [sdai] Attached SCSI disk
Oct  2 08:14:47 PE850-07 kernel: [65120.644969] sd 4:0:25:0: [sdaj] Attached SCSI disk
Oct  2 08:14:56 PE850-07 kernel: [65130.161476] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 11, phy 14, sas_addr 0x500194000090620e
Oct  2 08:14:56 PE850-07 kernel: [65130.168367] scsi 4:0:26:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Oct  2 08:14:56 PE850-07 kernel: [65130.171654] sd 4:0:26:0: Attached scsi generic sg15 type 0
Oct  2 08:14:56 PE850-07 kernel: [65130.173494] sd 4:0:26:0: [sdak] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Oct  2 08:14:56 PE850-07 kernel: [65130.195984] sd 4:0:26:0: [sdak] Write Protect is off
Oct  2 08:14:56 PE850-07 kernel: [65130.195994] sd 4:0:26:0: [sdak] Mode Sense: 73 00 00 08
Oct  2 08:14:56 PE850-07 kernel: [65130.203432] sd 4:0:26:0: [sdak] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:56 PE850-07 kernel: [65130.258499]  sdak: sdak1
Oct  2 08:14:56 PE850-07 kernel: [65130.327865] sd 4:0:26:0: [sdak] Attached SCSI disk
Oct  2 08:14:58 PE850-07 kernel: [65131.911920] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 12, phy 15, sas_addr 0x500194000090620f
Oct  2 08:14:58 PE850-07 kernel: [65131.916865] scsi 4:0:27:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
Oct  2 08:14:58 PE850-07 kernel: [65131.917681] sd 4:0:27:0: Attached scsi generic sg16 type 0
Oct  2 08:14:58 PE850-07 kernel: [65131.919275] sd 4:0:27:0: [sdal] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
Oct  2 08:14:58 PE850-07 kernel: [65131.958339] sd 4:0:27:0: [sdal] Write Protect is off
Oct  2 08:14:58 PE850-07 kernel: [65131.958350] sd 4:0:27:0: [sdal] Mode Sense: 73 00 00 08
Oct  2 08:14:58 PE850-07 kernel: [65131.962579] sd 4:0:27:0: [sdal] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  2 08:14:58 PE850-07 kernel: [65132.024721]  sdal: sdal1
Oct  2 08:14:58 PE850-07 kernel: [65132.166319] sd 4:0:27:0: [sdal] Attached SCSI disk
```
Either you change the slot on where the card is inserted or you changed the ports of all hard drives or all hard drives are failing or the SAS controller is misbehaving. I'm guessing it is the latter. Might as well get another controller.

---

### Post by MakOwner on 2014-10-06
It's a 12 disk RAID6 under mdadm, so the controller and shelf are just JBOD.
It's a 16 slot SGI Rackable enclosure (really old, long since surplussed) out of 6 shelves total, I have two of these shelves exhibiting the same behavior on two different controllers connected to different servers.
Both are running a trusty server install kernel though. One was an upgrade, one was a fresh install.  Other identical shelves operate on both these systems without issue.

I have pulled the first drive that fails in the events thinking it may be a hard drive going nuts on the bus and causing this.  So far this has not worked.

I'm wondering at this point if it's a firmware issue on the SAS expander, but I have no idea how to check for version.

---

### Post by nerdtron on 2014-10-06
Even with a JBOD controller, there should be prompt during BIOS/POST setup that you can key press to enter the JBOD controller setup. Maybe you can see there the firmware version of the controller.

---

### Post by MakOwner on 2014-10-06
> **nerdtron said:**
> Even with a JBOD controller, there should be prompt during BIOS/POST setup that you can key press to enter the JBOD controller setup. Maybe you can see there the firmware version of the controller.

I can see the controller version -- and I have walked through the BIOS to confirm settings between the different controllers I have.
It's the firmware in the SAS expander in the shelf that may be at issue - or at least is my current uninformed guess.
Or, I haven't found the drive that's really causing the issue.  
That's what I hope it is.

---


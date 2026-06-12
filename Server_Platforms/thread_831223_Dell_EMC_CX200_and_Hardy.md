---
title: "Dell EMC CX200 and Hardy"
date: 2008-06-16
forum: Server Platforms
---

### Post by Rever75 on 2008-06-16
Hi,
  I am having problems connecting my Ubuntu install to my EMC CX200. I have a storage group defined with a raid group associated to it. I can see the devices be created but cannot fdisk them at all. Here is what I see in 
**_dmesg_**

```
[   92.790369] qla2xxx 0000:02:06.0: Found an ISP2312, irq 20, iobase 0xf8836000
[   92.790524] qla2xxx 0000:02:06.0: Configuring PCI space...
[   92.790716] qla2xxx 0000:02:06.0: Configure NVRAM parameters...
[   92.800685] scsi 0:0:0:0: Direct-Access     DELL     Virtual Disk 0   V1.0 PQ: 0 ANSI: 2
[   92.824839] scsi 0:1:0:0: Direct-Access     FUJITSU  MAS3367NC        5B08 PQ: 0 ANSI: 3
[   92.827359] scsi 0:1:1:0: Direct-Access     FUJITSU  MAS3367NC        5B08 PQ: 0 ANSI: 3
[   92.881572] qla2xxx 0000:02:06.0: Verifying loaded RISC code...
[   93.068176] ata1.00: ATAPI: HL-DT-STDVD-ROM GDR8082N, 0106, max UDMA/33
[   93.207738] qla2xxx 0000:02:06.0: Allocated (412 KB) for firmware dump...
[   93.257957] ata1.00: configured for UDMA/33
[   93.267672] scsi3 : qla2xxx
[   93.267913] qla2xxx 0000:02:06.0: 
[   93.267914]  QLogic Fibre Channel HBA Driver: 8.02.00-k5
[   93.267915]   QLogic QLA2340 - 133MHz PCI-X to 2Gb FC, Single Channel
[   93.267916]   ISP2312: PCI-X (133 MHz) @ 0000:02:06.0 hdma+, host#=3, fw=3.03.20 IPX
[   93.267951] ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 16 (level, low) -> IRQ 21
[   93.268013] qla2xxx 0000:01:06.0: Found an ISP2312, irq 21, iobase 0xf8838000
[   93.268118] qla2xxx 0000:01:06.0: Configuring PCI space...
[   93.268300] qla2xxx 0000:01:06.0: Configure NVRAM parameters...
[   93.358587] qla2xxx 0000:01:06.0: Verifying loaded RISC code...
[   93.418775] scsi: waiting for bus probes to complete ...
[   93.497404] qla2xxx 0000:01:06.0: Allocated (412 KB) for firmware dump...
[   93.557340] scsi4 : qla2xxx
[   93.557572] qla2xxx 0000:01:06.0: 
[   93.557573]  QLogic Fibre Channel HBA Driver: 8.02.00-k5
[   93.557574]   QLogic QLA2340 - 133MHz PCI-X to 2Gb FC, Single Channel
[   93.557575]   ISP2312: PCI-X (100 MHz) @ 0000:01:06.0 hdma+, host#=4, fw=3.03.20 IPX
[   93.871524] scsi 0:1:6:0: Processor         PE/PV    1x5 SCSI BP      1.1  PQ: 0 ANSI: 2
[   93.883287] qla2xxx 0000:02:06.0: LOOP UP detected (2 Gbps).
[   94.152405] qla2xxx 0000:01:06.0: LOOP UP detected (2 Gbps).
[   94.345650] scsi 3:0:0:0: Direct-Access     DGC      LUNZ             0206 PQ: 0 ANSI: 4
[   94.635352] scsi 4:0:0:0: Direct-Access     DGC      LUNZ             0206 PQ: 0 ANSI: 4
[   99.777246] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8082N 0106 PQ: 0 ANSI: 5
[   99.785925] Driver 'sd' needs updating - please use bus_type methods
[   99.786095] sd 0:0:0:0: [sda] 71091456 512-byte hardware sectors (36399 MB)
[   99.786131] sd 0:0:0:0: [sda] Write Protect is off
[   99.786135] sd 0:0:0:0: [sda] Mode Sense: 06 00 00 00
[   99.786185] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   99.786351] sd 0:0:0:0: [sda] 71091456 512-byte hardware sectors (36399 MB)
[   99.786374] sd 0:0:0:0: [sda] Write Protect is off
[   99.786377] sd 0:0:0:0: [sda] Mode Sense: 06 00 00 00
[   99.786415] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   99.786420]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   99.798747]  sda5 >
[   99.798897] sd 0:0:0:0: [sda] Attached SCSI removable disk
[   99.799583] sd 3:0:0:0: [sdb] READ CAPACITY failed
[   99.799586] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   99.799591] sd 3:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[   99.799595] sd 3:0:0:0: [sdb] Add. Sense: Logical unit not supported
[   99.799874] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   99.799969] sd 3:0:0:0: [sdb] Asking for cache data failed
[   99.800025] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   99.800126] sd 3:0:0:0: [sdb] Attached SCSI disk
[   99.800749] sd 4:0:0:0: [sdc] READ CAPACITY failed
[   99.800751] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   99.800754] sd 4:0:0:0: [sdc] Sense Key : Illegal Request [current] 
[   99.800758] sd 4:0:0:0: [sdc] Add. Sense: Logical unit not supported
[   99.801036] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[   99.801132] sd 4:0:0:0: [sdc] Asking for cache data failed
[   99.801184] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   99.801277] sd 4:0:0:0: [sdc] Attached SCSI disk
```

**_lsscsi give me ..._**
```
[0:0:0:0]    disk    DELL     Virtual Disk 0   V1.0  /dev/sda
[0:1:0:0]    disk    FUJITSU  MAS3367NC        5B08  -       
[0:1:1:0]    disk    FUJITSU  MAS3367NC        5B08  -       
[0:1:6:0]    process PE/PV    1x5 SCSI BP      1.1   -       
[1:0:0:0]    cd/dvd  HL-DT-ST DVD-ROM GDR8082N 0106  /dev/scd0
[3:0:0:0]    disk    DGC      LUNZ             0206  /dev/sdb
[4:0:0:0]    disk    DGC      LUNZ             0206  /dev/sdc
[7:0:0:0]    disk    NETAPP   LUN              0.2   /dev/sdd

```
 
sudo fdisk /dev/sdc or /dev/sdb gives me Unable to open sdb. Any help would be greatly appreciated.

---

### Post by Thomy23 on 2008-11-18
yeah i can confirm the issue, the same problem here (Sun X4150 with a Qlogic HBA attached to a EMC CX300):


```

[0:0:0:0]    disk    Sun      xen              V1.0  /dev/sda
[0:1:0:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:1:1:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:1:2:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:1:3:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:3:0:0]    enclosu ADAPTEC  Virtual SGPIO  0 0001  -       
[0:3:1:0]    enclosu ADAPTEC  Virtual SGPIO  1 0001  -       
[3:0:0:0]    disk    DGC      LUNZ             0216  /dev/sdb
[10:0:0:0]   cd/dvd  TSSTcorp CD/DVDW TS-T632A SR03  /dev/scd0

```

Still no ideas??

---

### Post by Thomy23 on 2008-11-18
I found a solution (and this i perhaps a hint), this is how i did it:

Googeling the internet let me found out that you get this error message, when the Storage Processor isn't properly configured. In my case, the sp (from an EMC CX300) denied access to the storage pool as the FC HBA wasn't registered. I registered the HBA through the Webinterface and rebootet my Sun. After this, i could access the underlaying devicenodes.

lsscsi now gave me:

```

[0:0:0:0]    disk    Sun      xen              V1.0  /dev/sda
[0:1:0:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:1:1:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:1:2:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:1:3:0]    disk    HITACHI  H101414SCSUN146G SA23  -       
[0:3:0:0]    enclosu ADAPTEC  Virtual SGPIO  0 0001  -       
[0:3:1:0]    enclosu ADAPTEC  Virtual SGPIO  1 0001  -       
[1:0:0:0]    disk    DGC      RAID 5           0216  /dev/sdb
[1:0:0:1]    disk    DGC      RAID 5           0216  /dev/sdc
[1:0:0:2]    disk    DGC      RAID 5           0216  /dev/sdd
[1:0:0:3]    disk    DGC      RAID 5           0216  /dev/sde
[10:0:0:0]   cd/dvd  TSSTcorp CD/DVDW TS-T632A SR03  /dev/scd0

```


Hope it helped :)



Greets Thomy

---


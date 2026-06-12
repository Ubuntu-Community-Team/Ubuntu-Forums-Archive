---
title: "Error rebooting Ubuntu 10.04"
date: 2012-10-09
forum: Server Platforms
---

### Post by palomino5 on 2012-10-09
I've rebooted my ubuntu server and now I can only access to it with rescue method.
I've found some partition table errors in dmesg. How can I fix it??:confused::confused:

Thanks!

There are the last 100 lines of the dmesg:

0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 8c:89:a5:1d:e8:e5
0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
e1000e 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
e1000e 0000:03:00.0: setting latency timer to 64
e1000e 0000:03:00.0: irq 27 for MSI/MSI-X
e1000e 0000:03:00.0: Disabling ASPM L0s
0000:03:00.0: eth1: (PCI Express:2.5GB/s:Width x1) 8c:89:a5:1d:e8:e6
0000:03:00.0: eth1: Intel(R) PRO/1000 Network Connection
0000:03:00.0: eth1: MAC: 2, PHY: 2, PBA No: ffffff-0ff
tun: Universal TUN/TAP device driver, 1.6
tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
input: PC Speaker as /devices/platform/pcspkr/input/input2
i2c /dev entries driver
piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
ata4: SATA link down (SStatus 0 SControl 300)
ata3: SATA link down (SStatus 0 SControl 300)
k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
w83627ehf: Found W83627DHG chip at 0xa10
Software Watchdog Timer: 0.07 initialized. soft_noboot=0 soft_margin=60 sec (nowayout= 0)
md: linear personality registered for level -1
md: raid0 personality registered for level 0
md: raid1 personality registered for level 1
device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
cpuidle: using governor ladder
TCP cubic registered
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
sit0: Disabled Privacy Extensions
ip6tnl0: Disabled Privacy Extensions
NET: Registered protocol family 17
powernow-k8: Found 1 Quad-Core AMD Opteron(tm) Processor 1385 processors (4 cpu cores) (version 2.20.00)
powernow-k8:    0 : pstate 0 (2700 MHz)
powernow-k8:    1 : pstate 1 (2000 MHz)
powernow-k8:    2 : pstate 2 (1500 MHz)
powernow-k8:    3 : pstate 3 (800 MHz)
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: ATA-8: Hitachi HDS721010DLE630, MS2OA5Q0, max UDMA/133
ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
ata2.00: ATA-8: Hitachi HDS721010DLE630, MS2OA5Q0, max UDMA/133
ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
ata2.00: configured for UDMA/133
ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
ata1.00: configured for UDMA/133
scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72101 MS2O PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
sd 0:0:0:0: [sda] 4096-byte physical blocks
scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72101 MS2O PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
sd 1:0:0:0: [sdb] 4096-byte physical blocks
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb:
 sda: sdb1 sdb2 sdb3 sdb4 < sda1 sda2 sda3 sda4 < sdb5 sda5 sdb6 >
 sda6 >
sd 1:0:0:0: [sdb] Attached SCSI disk
sd 0:0:0:0: [sda] Attached SCSI disk
Freeing unused kernel memory: 636k freed
aufs test_add:252:busybox[1177]: uid/gid/perm /squash 0/0/0755, 0/0/01777
md: bind<sdb6>
md: bind<sda6>
raid1: raid set md3 active with 2 out of 2 mirrors
md3: detected capacity change from 0 to 389633933312
 md3: unknown partition table
md: bind<sdb5>
md: bind<sda5>
raid1: raid set md2 active with 2 out of 2 mirrors
md2: detected capacity change from 0 to 584452079616
 md2: unknown partition table
md: bind<sdb3>
md: bind<sda3>
raid1: raid set md1 active with 2 out of 2 mirrors
md1: detected capacity change from 0 to 20971454464
 md1: unknown partition table
md: bind<sdb1>
md: bind<sda1>
raid1: raid set md0 active with 2 out of 2 mirrors
md0: detected capacity change from 0 to 1048510464
 md0: unknown partition table
e1000e 0000:02:00.0: irq 26 for MSI/MSI-X
e1000e 0000:02:00.0: irq 26 for MSI/MSI-X
ADDRCONF(NETDEV_UP): eth0: link is not ready
e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
0000:02:00.0: eth0: 10/100 speed: disabling TSO
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Loading iSCSI transport class v2.0-870.
iscsi: registered transport (tcp)

---


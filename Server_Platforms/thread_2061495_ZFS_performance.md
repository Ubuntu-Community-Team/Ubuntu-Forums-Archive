---
title: "ZFS performance"
date: 2012-09-22
forum: Server Platforms
---

### Post by eldaria on 2012-09-22
Hi everyone.

I been running Ubuntu server for years and recently built a new server and decided to go for ZFS.
It has been running for a while and I have a suspicion that I'm not getting the performance that I should be getting.
I was reading about scrub speed and see others getting way better scrub speed than i'm getting.
For example I saw people complaining about getting only 200MB/s, I'm getting 23MB/s.

I'm wondering if you guys have any idea what is going on?

iostat while scrub is running:
```
                                                    capacity     operations    bandwidth
pool                                             alloc   free   read  write   read  write
-----------------------------------------------  -----  -----  -----  -----  -----  -----
z1pool                                            654G  13.0T    200      0  19.2M      0
  raidz1                                          654G  13.0T    200      0  19.2M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0055446        -      -    187      0  5.05M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053866        -      -    197      0  5.16M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053751        -      -    180      0  4.70M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0076270        -      -    193      0  5.08M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0054484        -      -    188      0  4.97M      0
cache                                                -      -      -      -      -      -
  scsi-SATA_SAMSUNG_SSD_830S0XYNEAC667938-part7  67.0G  7.99M      6      1  28.0K  8.00K
-----------------------------------------------  -----  -----  -----  -----  -----  -----

```

This is a status while scrub:
```

  pool: z1pool
 state: ONLINE
 scan: scrub in progress since Sat Sep 22 21:06:29 2012
    54.0G scanned out of 654G at 23.7M/s, 7h11m to go
    0 repaired, 8.27% done
config:

	NAME                                             STATE     READ WRITE CKSUM
	z1pool                                           ONLINE       0     0     0
	  raidz1-0                                       ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0055446    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053866    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053751    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0076270    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0054484    ONLINE       0     0     0
	cache
	  scsi-SATA_SAMSUNG_SSD_830S0XYNEAC667938-part7  ONLINE       0     0     0

errors: No known data errors

```

Parameters of the pool:
```
zpool get all z1pool 
NAME    PROPERTY       VALUE       SOURCE
z1pool  size           13.6T       -
z1pool  capacity       4%          -
z1pool  altroot        -           default
z1pool  health         ONLINE      -
z1pool  guid           10343916700434118591  default
z1pool  version        28          default
z1pool  bootfs         -           default
z1pool  delegation     on          default
z1pool  autoreplace    off         default
z1pool  cachefile      -           default
z1pool  failmode       wait        default
z1pool  listsnapshots  off         default
z1pool  autoexpand     off         default
z1pool  dedupditto     0           default
z1pool  dedupratio     1.17x       -
z1pool  free           13.0T       -
z1pool  allocated      654G        -
z1pool  readonly       off         -
z1pool  ashift         12          local
z1pool  comment        -           default

```

CPU 0/8:
```
cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
stepping	: 9
microcode	: 0x12
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips	: 6800.36
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

Memory Info:
```
cat /proc/meminfo 
MemTotal:       16123836 kB
MemFree:         1248828 kB
Buffers:          185812 kB
Cached:           993060 kB
SwapCached:           24 kB
Active:          1188644 kB
Inactive:         548216 kB
Active(anon):     660836 kB
Inactive(anon):   324096 kB
Active(file):     527808 kB
Inactive(file):   224120 kB
Unevictable:          16 kB
Mlocked:              16 kB
SwapTotal:      15624188 kB
SwapFree:       15614892 kB
Dirty:                44 kB
Writeback:             0 kB
AnonPages:        558296 kB
Mapped:           106396 kB
Shmem:            426944 kB
Slab:             695896 kB
SReclaimable:     223236 kB
SUnreclaim:       472660 kB
KernelStack:        4424 kB
PageTables:        28520 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    23686104 kB
Committed_AS:    3029052 kB
VmallocTotal:   34359738367 kB
VmallocUsed:     9353120 kB
VmallocChunk:   34345641904 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      262144 kB
DirectMap2M:    16218112 kB
```

lshw:
```
lshw
lnx                       
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=40AE3A27-DAD7-DD11-9AD2-10BF487F57A9
  *-core
       description: Motherboard
       product: P8H77-I
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: MT7025030700992
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0809
          date: 08/01/2012
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 2400MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal unified
     *-memory:0 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C9D3/8G
             vendor: Kingston
             physical id: 0
             serial: D51A447C
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-memory:1
          description: System Memory
          physical id: 58
          slot: System board or motherboard
        *-bank
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C9D3/8G
             vendor: Kingston
             physical id: 0
             serial: D81A397C
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-memory:2 UNCLAIMED
          physical id: 2
     *-memory:3 UNCLAIMED
          physical id: 3
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Ivy Bridge PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42
        *-display
             description: VGA compatible controller
             product: Ivy Bridge Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: Panther Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:44 memory:f7c00000-f7c0ffff
        *-communication
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:46 memory:f7c1a000-f7c1a00f
        *-usb:1
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7c18000-f7c183ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:f7c10000-f7c13fff
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: Panther Point PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 09
                serial: 10:bf:48:7f:57:a9
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.4 03/27/12 ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:45 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-usb:2
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7c17000-f7c173ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Panther Point 6 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             logical name: scsi5
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7c16000-f7c167ff
           *-disk:0
                description: ATA Disk
                product: SAMSUNG SSD 830
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: CXM0
                serial: S0XYNEAC667938
                size: 119GiB (128GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009a474
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: 3b09f931-bbc3-48bc-83d1-4f16ac75f91a
                   size: 94MiB
                   capacity: 94MiB
                   capabilities: primary bootable journaled extended_attributes huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-09-08 09:01:03 filesystem=ext4 lastmountpoint=/boot modified=2012-09-08 09:11:50 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-09-08 09:11:50 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 119GiB
                   capacity: 119GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 37GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 14GiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 66GiB
           *-disk:1
                description: ATA Disk
                product: WDC WD30EFRX-68A
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 80.0
                serial: WD-WMC1T0055446
                size: 2794GiB (3TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=15001c06-e8f3-9441-bc0e-269f79aade11
              *-volume:0
                   description: EFI partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   serial: fb5266ca-465a-d842-8078-95625d5c85b9
                   capacity: 2794GiB
                   configuration: name=zfs
              *-volume:1
                   description: EFI partition
                   physical id: 9
                   bus info: scsi@1:0.0.0,9
                   logical name: /dev/sdb9
                   serial: 9e0647e6-2902-7649-89c0-b6569dda50ad
                   capacity: 8191KiB
           *-disk:2
                description: ATA Disk
                product: WDC WD30EFRX-68A
                vendor: Western Digital
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: 80.0
                serial: WD-WMC1T0053866
                size: 2794GiB (3TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=724734ae-ce6a-e444-a6db-52ee95a2e00f
              *-volume:0
                   description: EFI partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdc1
                   serial: 69074475-4191-5b43-9ff3-d18ccf4a9f09
                   capacity: 2794GiB
                   configuration: name=zfs
              *-volume:1
                   description: EFI partition
                   physical id: 9
                   bus info: scsi@2:0.0.0,9
                   logical name: /dev/sdc9
                   serial: 74c9775f-333e-d847-8ca1-face4729e6d0
                   capacity: 8191KiB
           *-disk:3
                description: ATA Disk
                product: WDC WD30EFRX-68A
                vendor: Western Digital
                physical id: 3
                bus info: scsi@3:0.0.0
                logical name: /dev/sdd
                version: 80.0
                serial: WD-WMC1T0053751
                size: 2794GiB (3TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=01487491-96a5-af4a-b721-e3134fdac37a
              *-volume:0
                   description: EFI partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdd1
                   serial: 7c4631eb-fcf3-7b45-a542-58ad0c1139de
                   capacity: 2794GiB
                   configuration: name=zfs
              *-volume:1
                   description: EFI partition
                   physical id: 9
                   bus info: scsi@3:0.0.0,9
                   logical name: /dev/sdd9
                   serial: 93834b5a-f5b0-a24c-8419-9e4c8aa3b87c
                   capacity: 8191KiB
           *-disk:4
                description: ATA Disk
                product: WDC WD30EFRX-68A
                vendor: Western Digital
                physical id: 4
                bus info: scsi@4:0.0.0
                logical name: /dev/sde
                version: 80.0
                serial: WD-WMC1T0076270
                size: 2794GiB (3TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=7143955a-18cc-5e4a-8f94-c28b8a4f4e7b
              *-volume:0
                   description: EFI partition
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sde1
                   serial: 2a9543f5-b59d-304c-bea3-299eed7b5cd7
                   capacity: 2794GiB
                   configuration: name=zfs
              *-volume:1
                   description: EFI partition
                   physical id: 9
                   bus info: scsi@4:0.0.0,9
                   logical name: /dev/sde9
                   serial: 5e418a4f-7ac6-ba46-8213-06eae8ef2f6d
                   capacity: 8191KiB
           *-disk:5
                description: ATA Disk
                product: WDC WD30EFRX-68A
                vendor: Western Digital
                physical id: 5
                bus info: scsi@5:0.0.0
                logical name: /dev/sdf
                version: 80.0
                serial: WD-WMC1T0054484
                size: 2794GiB (3TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=71c900d1-e6f5-a543-97ff-4477f610318a
              *-volume:0
                   description: EFI partition
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdf1
                   serial: 18ce94a3-cb8e-1842-8be4-56282f0b757a
                   capacity: 2794GiB
                   configuration: name=zfs
              *-volume:1
                   description: EFI partition
                   physical id: 9
                   bus info: scsi@5:0.0.0,9
                   logical name: /dev/sdf9
                   serial: f01aeb85-d317-5344-8033-fdd097c9b593
                   capacity: 8191KiB
        *-serial UNCLAIMED
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7c15000-f7c150ff ioport:f040(size=32)
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh

```

---

### Post by TheFu on 2012-09-22
Did you compile the kernel ZFS module or are you using FUSE?  It would expect the FUSE drivers to suck, performance wise. I wouldn't expect a desktop SATA controller to be very impressive either.

Looks like a nice setup - cache.  Are those WDs all Raptors or Black models?  The cheap "green" models are known to have issues when used in disk arrays.

Phoronix does ZFS comparisons with other file systems every 3-6 months. I couldn't easily find the last one, but here's another.
[http://www.phoronix.com/scan.php?page=article&item=linux_kqzfs_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_kqzfs_benchmarks&num=1)

Sorry, I'm not much help.

---

### Post by eldaria on 2012-09-22
I'm using the [http://ppa.launchpad.net/zfs-native/stable/](http://ppa.launchpad.net/zfs-native/stable/)
So it should not be FUSE but compiled.

The disks are WD Red drives.

I have been thinking about getting a dedicated RAID SATA card to hook the disks to.
The motherboard has a single 16X PCIe that is not in use currently.
However I first want to make sure it is not something else going on before I go out and buy additional hardware.

---

### Post by TheFu on 2012-09-22
Well, I don't think that ZFS will use the HW-RAID card in RAID mode. It needs JBOD access, correct?

Seems to me that you have a fantastic experience with that hardware.  I use softwareRAID, mdadm, with (4) almost 6 yr old Seagate 320G sata disks and get pretty crap performance around 25Mbps.  Seeing much faster performance with a single 1TB Black drive - 70Mbps writes are normal.

I'll read up on that link - thanks!   I've wanted to use ZFS, but not FUSE and not by having to support it manually outside the package manager.  I did 10 yrs supporting manually maintained kernels - never again.

Just as a last ditch comment, have you tuned the **hdparm** and **/sbin/blockdev **for your controller and disks?

I'll check back in the morning.

---

### Post by eldaria on 2012-09-22
You are correct ZFS don't care for RAID, it wants direct access to the drive, that much I figured. :-)

Also one should define the raw disk, not a partition.
My only exception to that is my Cache disk that is on an SSD that is also my boot, root and swap so I could not give it the raw disk for cache.

However I read that dedicated Raid controllers have better I/O, also currently only two of the disks the SSD and one WD are on 6G ports, the other 4 WD are on 3G ports.

About my setup, well I was working it out during a long time, not sure if you are into Hardware porn. ;-) Here are some pictures.
[https://picasaweb.google.com/111219670934402531217/NewServer2012?authkey=Gv1sRgCK_enqKnkd2jgAE]("https://picasaweb.google.com/111219670934402531217/NewServer2012?authkey=Gv1sRgCK_enqKnkd2jgAE")

Do tell more about tuning with hdparm, and blockdev. :-)

I did some DD tests and i'm getting weird results, large block size gives me amazing performance, but the smaller the block size the worse performance I get.

```

root@lnx:/z1pool/Media# dd if=/dev/zero of=zerofile.000 bs=48K count=10000000
10000000+0 records in
10000000+0 records out
491520000000 bytes (492 GB) copied, 160.175 s, 3.1 GB/s

root@lnx:/z1pool/Media# dd if=zerofile.000 of=/dev/null bs=48K
10000000+0 records in
10000000+0 records out
491520000000 bytes (492 GB) copied, 91.5435 s, 5.4 GB/s

```

If I drop the Block Size I get very different results.
```

root@lnx:/z1pool/Media# dd if=/dev/zero of=zerofile.000 bs=1K count=10000000
10000000+0 records in
10000000+0 records out
10240000000 bytes (10 GB) copied, 51.5894 s, 198 MB/s

root@lnx:/z1pool/Media# dd if=zerofile.000 of=/dev/null bs=1K
10000000+0 records in
10000000+0 records out
10240000000 bytes (10 GB) copied, 57.411 s, 178 MB/s

```

---

### Post by eldaria on 2012-09-22
Small update, I corrected the disk type, it is not Black drives, It is Red drives.

---

### Post by rubylaser on 2012-09-23
Since you have a dedupratio parameter of 1.17x it appears that you have dedup on.  Deduplication requires a massive amount of RAM to perform decently.  Have you tried this test with dedup off? 

Also, I don't see a mention if you have compression turned on (you should with your hardware).  /dev/zero will give unrealistic results if you are using compression. Also, don't run the write and read back to back as ZFS will continue writing data to disk after write operations return complete. Something like this will return more accurate results:

```
dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M
```

Here's my 9 disk raidz2 on Openindiana running the above test with an old AMD 4600X2 processor and 8GB of RAM w/ no ZIL or cache drives and a mix of Hitachi, Seagate, and WD green drives.

```
root@fileserver:/tank# dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M

10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 32.1057 s, 327 MB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 19.0481 s, 550 MB/s
```

---

### Post by eldaria on 2012-09-23
I have turned off dedupe, it still shows it though, I guess it will keep already written data as dedupe.

I do have compression on on the mount I was testing, did not think about that. lol.

So I created a new test mount, only thing I have there is atime=off.

```

root@lnx:/z1pool/test# zpool get all z1pool
NAME    PROPERTY       VALUE       SOURCE
z1pool  size           13.6T       -
z1pool  capacity       4%          -
z1pool  altroot        -           default
z1pool  health         ONLINE      -
z1pool  guid           10343916700434118591  default
z1pool  version        28          default
z1pool  bootfs         -           default
z1pool  delegation     on          default
z1pool  autoreplace    off         default
z1pool  cachefile      -           default
z1pool  failmode       wait        default
z1pool  listsnapshots  off         default
z1pool  autoexpand     off         default
z1pool  dedupditto     0           default
z1pool  dedupratio     1.17x       -
z1pool  free           13.0T       -
z1pool  allocated      654G        -
z1pool  readonly       off         -
z1pool  ashift         12          local
z1pool  comment        -           default

root@lnx:/z1pool/test# zfs get dedup
NAME           PROPERTY  VALUE          SOURCE
z1pool         dedup     off            default
z1pool/Backup  dedup     off            local
z1pool/Media   dedup     off            default
z1pool/test    dedup     off            default

root@lnx:/z1pool/test# zfs get compression
NAME           PROPERTY     VALUE     SOURCE
z1pool         compression  off       default
z1pool/Backup  compression  on        local
z1pool/Media   compression  on        local
z1pool/test    compression  off       local

root@lnx:/z1pool/test# dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 19.2263 s, 545 MB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 13.8487 s, 757 MB/s

root@lnx:/z1pool/test# zpool scrub -s z1pool

root@lnx:/z1pool/test# dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 16.3289 s, 642 MB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 11.7979 s, 889 MB/s

root@lnx:/z1pool/test# dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 17.2174 s, 609 MB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 9.93469 s, 1.1 GB/s

root@lnx:/z1pool/test# zfs set compression=on z1pool/test

root@lnx:/z1pool/test# dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 1.92519 s, 5.4 GB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 0.904744 s, 11.6 GB/s

```

---

### Post by eldaria on 2012-09-23
But a scrub is still going at 20-25MB/s

Going to try and remove the deuped files, will move everything from the mount that had deupe activated to one that only has compression, then move it back.

---

### Post by rubylaser on 2012-09-23
Are you giving the scrub time to build up speed?  It always starts slow, and then ramps up as it goes. Mine starts around 6 MB/s and after 30 minutes or so it's up to 350MB/s - 400MB/s.  What do you transfer speeds look like if you run that command I posted?

---

### Post by eldaria on 2012-09-23
I did not watch it the whole time but last night it finished in 1 hour 59 minutes.
Given that I have about 654GB, that should give an average of 94MB/s, not that great.

But I do get excellent transfer speed with your command, I posted them above unfortunately I fogot to separate it from the rest. Here it is again:

Compression off:
```
root@lnx:/z1pool/test# dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 17.2174 s, 609 MB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 9.93469 s, 1.1 GB/s

```

Compression on:
```
root@lnx:/z1pool/test# dd if=/dev/zero of=zerofile.000 bs=1M count=10000; sleep 30 ; dd if=zerofile.000 of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 1.92519 s, 5.4 GB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 0.904744 s, 11.6 GB/s

```

However dropping the block size reduces the speed significantly, but it seems the CPU will spike too 99% on the dd process, so I guess it is not zfs causing the bottleneck here.

Is there some other way to test the performance, I read about Bonnie, but I can't figure out how to read the results, or compare them.

---

### Post by rubylaser on 2012-09-24
With 16GB of RAM, those results are hitting RAM.  To test the disks properly, you'll really need to use a count that will yield files at least 2x the amount of RAM you have, and with compression turned on , your dd values aren't really realistic anymore, although they look awesome :)

Here's an [old post of mine]("http://ubuntuforums.org/showpost.php?p=10360282&postcount=2") talking about setting up bonnie.

---


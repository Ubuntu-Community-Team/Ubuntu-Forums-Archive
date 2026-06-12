---
title: "Cannot access the running instance from client"
date: 2011-12-12
forum: Ubuntu Cloud and Juju
---

### Post by logskish on 2011-12-12
Hi, I sum how managed to run instances under UEC (Ubuntu 10.04 server 64bit).

Here are my configurations !
```

CLC,CC,WS3, SC  (Frontend) - 10.184.17.29
NC - 10.184.17.30

Hwinfo - Intel quadcore (Q8300), 500GB, 4GB RAM, VT-x enabled in both the systems

I bundled the images which were given under eucalyptus website. ([ubuntu 9.04 x86-64bit]("http://open.eucalyptus.com/wiki/EucalyptusUserImageCreatorGuide_v1.6")) 

My query is .. I can only access (ping & ssh) my running instance only in  my frontend. I cannot ping or ssh my instances from my client, but i  can see the console output from client nd see the status of my running  state vm thro' elastic fox. 


Is there any specific log that i need to provide @! 
[U][B]
Here are my configuration files ..! [/B][/U]
[U]
Eucalyptus.conf
[/U]
/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
NODES="10.184.17.30"
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"

_eucalyptus.local.conf_

VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="10.184.17.1"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="192.168.0.100-192.168.0.150"

_VIEW INSTANCES FROM THE CLIENT_

euca-describe-instances 
RESERVATION    r-45CA0852    admin    default
INSTANCE    i-463407D1    emi-39711602    192.168.0.100    172.19.1.2    running    key1    0        m1.large    2011-12-09T14:33:44.348Z    cluster1    eki-AE6117D9    eri-16D9191E


_CONSOLE OUTPUT FROM THE CLIENT_

euca-get-console-output i-463407D1
i-463407D1
2011-12-12T08:05:02.914Z
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=/dev/sda1 console=ttyS0
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffb000 (usable)
[    0.000000]  BIOS-e820: 000000001fffb000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffbc000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x1fffb max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fffb000 (usable)
[    0.000000]  modified: 000000001fffb000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fffbc000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000001fffb000
[    0.000000] last_map_addr: 1fffb000 end: 1fffb000
[    0.000000] RAMDISK: 1f7a9000 - 1ffeffec
[    0.000000] ACPI: RSDP 000F8920, 0014 (r0 BOCHS )
[    0.000000] ACPI: RSDT 1FFFDE10, 0034 (r1 BOCHS  BXPCRSDT        1 BXPC        1)
[    0.000000] ACPI: FACP 1FFFFE40, 0074 (r1 BOCHS  BXPCFACP        1 BXPC        1)
[    0.000000] ACPI: DSDT 1FFFDFD0, 1E22 (r1   BXPC   BXDSDT        1 INTL 20090123)
[    0.000000] ACPI: FACS 1FFFFE00, 0040
[    0.000000] ACPI: SSDT 1FFFDF80, 0044 (r1 BOCHS  BXPCSSDT        1 BXPC        1)
[    0.000000] ACPI: APIC 1FFFDE90, 007A (r1 BOCHS  BXPCAPIC        1 BXPC        1)
[    0.000000] ACPI: HPET 1FFFDE50, 0038 (r1 BOCHS  BXPCHPET        1 BXPC        1)
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 001fffb000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [001f7a9000 - 001ffeffec]          RAMDISK ==> [001f7a9000 - 001ffeffec]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000] found SMP MP-table at [ffff8800000f8970] 000f8970
[    0.000000] kvm-clock: cpu 0, msr 0:a6d881, boot clock
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0001fffb
[    0.000000] ACPI: PM-Timer IO Port: 0xb008
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 high level)
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dffbc000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] kvm-clock: cpu 0, msr 0:1014881, primary cpu clock
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 126612
[    0.000000] Kernel command line: root=/dev/sda1 console=ttyS0
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] Detected 9975.232 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [ttyS0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.004000] allocated 5242880 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Memory: 490716k/524268k available (4760k kernel code, 492k absent, 32540k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.024011] Calibrating delay loop (skipped) preset value.. 4987.61 BogoMIPS (lpj=9975232)
[    0.025480] Security Framework initialized
[    0.026261] SELinux:  Disabled at boot.
[    0.028057] AppArmor: AppArmor initialized
[    0.028763] Mount-cache hash table entries: 256
[    0.030207] Initializing cgroup subsys ns
[    0.031024] Initializing cgroup subsys cpuacct
[    0.032007] Initializing cgroup subsys memory
[    0.032812] Initializing cgroup subsys freezer
[    0.033661] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.034464] CPU: L2 cache: 4096K
[    0.036044] ACPI: Core revision 20080926
[    0.036726] ACPI: Checking initramfs for custom DSDT
[    0.336443] Setting APIC routing to flat
[    0.339286] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.380125] CPU0: Intel QEMU Virtual CPU version 0.12.3 stepping 03
[    0.384001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay loop (skipped) preset value.. 4987.61 BogoMIPS (lpj=9975232)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.392897] CPU1: Intel QEMU Virtual CPU version 0.12.3 stepping 03
[    0.396805] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.004000] kvm-clock: cpu 1, msr 0:1025881, secondary cpu clock
[    0.404031] Brought up 2 CPUs
[    0.404033] Total of 2 processors activated (9975.23 BogoMIPS).
[    0.404783] net_namespace: 1400 bytes
[    0.404794] Booting paravirtualized kernel on KVM
[    0.405167] Time: 14:33:53  Date: 12/09/11
[    0.405178] regulator: core version 0.5
[    0.405246] NET: Registered protocol family 16
[    0.405435] ACPI: bus type pci registered
[    0.408106] PCI: Using configuration type 1 for base access
[    0.408131] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.408133] mtrr: your CPUs had inconsistent MTRRdefType settings
[    0.408133] mtrr: probably your BIOS does not setup all CPUs.
[    0.408134] mtrr: corrected configuration.
[    0.418110] ACPI: Interpreter enabled
[    0.418754] ACPI: (supports S0 S3 S4 S5)
[    0.419503] ACPI: Using IOAPIC for interrupt routing
[    0.422033] ACPI: No dock devices found.
[    0.422715] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.425461] pci 0000:00:01.3: quirk: region b000-b03f claimed by PIIX4 ACPI
[    0.426614] pci 0000:00:01.3: quirk: region b100-b10f claimed by PIIX4 SMB
[    0.437160] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10 11)
[    0.438331] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.439429] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10 *11)
[    0.440364] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    0.441596] ACPI: WMI: Mapper loaded
[    0.442589] SCSI subsystem initialized
[    0.444130] usbcore: registered new interface driver usbfs
[    0.445093] usbcore: registered new interface driver hub
[    0.446032] usbcore: registered new device driver usb
[    0.446032] PCI: Using ACPI for IRQ routing
[    0.460034] Bluetooth: Core ver 2.13
[    0.460855] NET: Registered protocol family 31
[    0.460982] Bluetooth: HCI device and connection manager initialized
[    0.462330] Bluetooth: HCI socket layer initialized
[    0.464011] NET: Registered protocol family 8
[    0.464908] NET: Registered protocol family 20
[    0.465854] NetLabel: Initializing
[    0.466562] NetLabel:  domain hash size = 128
[    0.467475] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.468033] NetLabel:  unlabeled traffic allowed by default
[    0.469293] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.470378] hpet0: 3 comparators, 64-bit 100.000000 MHz counter
[    0.476400] AppArmor: AppArmor Filesystem Enabled
[    0.488028] pnp: PnP ACPI init
[    0.488686] ACPI: bus type pnp registered
[    0.490513] pnp: PnP ACPI: found 7 devices
[    0.491368] ACPI: ACPI bus type pnp unregistered
[    0.497306] bus: 00 index 0 io port: [0x00-0xffff]
[    0.498277] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.499503] NET: Registered protocol family 2
[    0.536139] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.537936] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.539747] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.541499] TCP: Hash tables configured (established 16384 bind 16384)
[    0.542965] TCP reno registered
[    0.552159] NET: Registered protocol family 1
[    0.553335] checking if image is initramfs... it is
[    1.001017] Clocksource tsc unstable (delta = -375451329 ns)
[    1.186093] Freeing initrd memory: 8475k freed
[    1.190438] audit: initializing netlink socket (disabled)
[    1.191562] type=2000 audit(1323441234.188:1): initialized
[    1.202305] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.205103] VFS: Disk quotas dquot_6.5.1
[    1.205842] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.207594] fuse init (API version 7.10)
[    1.208374] msgmni has been set to 976
[    1.209503] alg: No test for stdrng (krng)
[    1.210484] io scheduler noop registered
[    1.211168] io scheduler anticipatory registered
[    1.211919] io scheduler deadline registered
[    1.212651] io scheduler cfq registered (default)
[    1.213458] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    1.214443] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    1.215391] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    1.217139] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.218048] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.219278] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.220517] ACPI: Power Button (FF) [PWRF]
[    1.221553] processor ACPI_CPU:00: registered as cooling_device0
[    1.222544] processor ACPI_CPU:01: registered as cooling_device1
[    1.237204] Linux agpgart interface v0.103
[    1.237886] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.239103] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.240498] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.242161] brd: module loaded
[    1.242967] loop: module loaded
[    1.243547] Fixed MDIO Bus: probed
[    1.244104] PPP generic driver version 2.4.2
[    1.245058] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    1.246607] Driver 'sd' needs updating - please use bus_type methods
[    1.247870] Driver 'sr' needs updating - please use bus_type methods
[    1.249693] scsi0 : ata_piix
[    1.250476] scsi1 : ata_piix
[    1.251090] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc000 irq 14
[    1.252419] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc008 irq 15
[    1.565008] ata2.00: ATAPI: QEMU DVD-ROM, 0.12.3, max UDMA/100
[    1.566419] ata2.00: configured for MWDMA2
[    1.567534] isa bounce pool size: 16 pages
[    1.568764] scsi 1:0:0:0: CD-ROM            QEMU     QEMU DVD-ROM     0.12 PQ: 0 ANSI: 5
[    1.572672] sr0: scsi3-mmc drive: 4x/4x xa/form2 tray
[    1.573724] Uniform CD-ROM driver Revision: 3.20
[    1.574810] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.576479] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.577810] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.579034] uhci_hcd: USB Universal Host Controller Interface driver
[    1.580462] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    1.581639] uhci_hcd 0000:00:01.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, high) -> IRQ 11
[    1.583396] uhci_hcd 0000:00:01.2: UHCI Host Controller
[    1.584522] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    1.585827] uhci_hcd 0000:00:01.2: irq 11, io base 0x0000c020
[    1.586897] usb usb1: configuration #1 chosen from 1 choice
[    1.587838] hub 1-0:1.0: USB hub found
[    1.588476] hub 1-0:1.0: 2 ports detected
[    1.589293] usbcore: registered new interface driver libusual
[    1.590249] usbcore: registered new interface driver usbserial
[    1.591212] USB Serial support registered for generic
[    1.592043] usbcore: registered new interface driver usbserial_generic
[    1.593113] usbserial: USB Serial Driver core
[    1.593868] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.595701] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.596522] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.609065] mice: PS/2 mouse device common for all mice
[    1.633186] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.634569] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.635938] device-mapper: uevent: version 1.0.3
[    1.637363] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.639147] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.641251] device-mapper: multipath: version 1.0.5 loaded
[    1.642353] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.644115] cpuidle: using governor ladder
[    1.644956] cpuidle: using governor menu
[    1.646174] TCP cubic registered
[    1.646909] NET: Registered protocol family 10
[    1.648337] lo: Disabled Privacy Extensions
[    1.649509] NET: Registered protocol family 17
[    1.650440] Bluetooth: L2CAP ver 2.11
[    1.651185] Bluetooth: L2CAP socket layer initialized
[    1.652203] Bluetooth: SCO (Voice Link) ver 0.6
[    1.653136] Bluetooth: SCO socket layer initialized
[    1.654286] Bluetooth: RFCOMM socket layer initialized
[    1.655151] Bluetooth: RFCOMM TTY layer initialized
[    1.655951] Bluetooth: RFCOMM ver 1.10
[    1.656791] registered taskstats version 1
[    1.657598]   Magic number: 7:227:586
[    1.658336] rtc_cmos 00:01: setting system clock to 2011-12-09 14:33:54 UTC (1323441234)
[    1.659638] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.660612] EDD information not available.
[    1.661315] Freeing unused kernel memory: 536k freed
[    1.662467] Write protecting the kernel read-only data: 6708k
Loading, please wait...
Couldnt get a file descriptor referring to the console
Begin: Loading essential drivers... ...
[    2.114313] md: linear personality registered for level -1
[    2.121370] md: multipath personality registered for level -4
[    2.128462] md: raid0 personality registered for level 0
[    2.136518] md: raid1 personality registered for level 1
[    2.143449] xor: automatically using best checksumming function: generic_sse
[    2.165014]    generic_sse:  8420.000 MB/sec
[    2.165835] xor: using function: generic_sse (8420.000 MB/sec)
[    2.167877] async_tx: api initialized (async)
[    2.237023] raid6: int64x1   1962 MB/s
[    2.305017] raid6: int64x2   2659 MB/s
[    2.373038] raid6: int64x4   2055 MB/s
[    2.441033] raid6: int64x8   1838 MB/s
[    2.509026] raid6: sse2x1    3334 MB/s
[    2.577011] raid6: sse2x2    3786 MB/s
[    2.645014] raid6: sse2x4    5187 MB/s
[    2.645654] raid6: using algorithm sse2x4 (5187 MB/s)
[    2.646474] md: raid6 personality registered for level 6
[    2.647329] md: raid5 personality registered for level 5
[    2.648201] md: raid4 personality registered for level 4
[    2.666567] md: raid10 personality registered for level 10
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Waiting for root file system... ...
[    2.785676] FDC 0 is a S82078B
[    2.805270] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    2.806502] Copyright (c) 1999-2006 Intel Corporation.
[    2.807762] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    2.808859] e1000 0000:00:03.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, high) -> IRQ 10
[    3.126869] e1000: 0000:00:03.0: e1000_probe: (PCI:33MHz:32-bit) d0:0d:46:34:07:d1
[    3.176253] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.177863] sym53c8xx 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, high) -> IRQ 11
[    3.181728] sym0: <895a> rev 0x0 at pci 0000:00:04.0 irq 11
[    3.190737] sym0: No NVRAM, ID 7, Fast-40, LVD, parity checking
[    3.192010] sym0: SCSI BUS has been reset.
[    3.206958] scsi2 : sym-2.2.3
[    6.213181] scsi 2:0:0:0: Direct-Access     QEMU     QEMU HARDDISK    0.12 PQ: 0 ANSI: 3
[    6.214804] scsi target2:0:0: tagged command queuing enabled, command queue depth 16.
[    6.216337] scsi target2:0:0: Beginning Domain Validation
[    6.218137] scsi target2:0:0: Domain Validation skipping write tests
[    6.219420] scsi target2:0:0: Ending Domain Validation
[    6.226493] sd 2:0:0:0: [sda] 21000192 512-byte hardware sectors: (10.7 GB/10.0 GiB)
[    6.228168] sd 2:0:0:0: [sda] Write Protect is off
[    6.229341] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    6.231601] sd 2:0:0:0: [sda] 21000192 512-byte hardware sectors: (10.7 GB/10.0 GiB)
[    6.233374] sd 2:0:0:0: [sda] Write Protect is off
[    6.234659] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    6.236533]  sda: sda1 sda2 sda3
[    6.237886] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.238870] sd 2:0:0:0: Attached scsi generic sg1 type 0
Done.
Begin: Running /scripts/local-premount ...
Begin: Waiting for resume device... ...
Done.
Done.
[   11.509778] kjournald starting.  Commit interval 5 seconds
[   11.509803] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
 * Setting preliminary keymap...                                         [ OK ] 
 * Starting kernel event manager...                                             [   11.907707] udev: starting version 141
                                                                         [ OK ]
 * Loading hardware drivers...                                                  [   12.034357] piix4_smbus 0000:00:01.3: SMBus Host Controller at 0xb100, revision 0
[   12.129631] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   12.147900] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.209564] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   12.211991] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.217466] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   12.354252] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
                                                                         [ OK ]
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
 * Setting kernel variables (/etc/sysctl.conf)...                        [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...  [ OK ] 
 * Activating swap...                                                    [ OK ] 
 * Checking file systems...                                                     fsck 1.41.4 (27-Jan-2009)
                                                                         [ OK ]
 * Mounting local filesystems...                                                [mntent]: warning: no final newline at the end of /etc/fstab
[   13.417175] ext3: No journal on filesystem on sda2
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

                                                                         [fail]
 * Activating swapfile swap...                                           [ OK ] 
 * Configuring network interfaces...                                     [ OK ] 
 * Setting up console font and keymap...                                 [ OK ] 
 * Starting system log daemon...                                                chown: cannot access `/var/log/mail.warn': No such file or directory
chown: cannot access `/var/log/user.log': No such file or directory
chown: cannot access `/var/log/daemon.log': No such file or directory
chown: cannot access `/var/log/messages': No such file or directory
chown: cannot access `/var/log/auth.log': No such file or directory
chown: cannot access `/var/log/mail.err': No such file or directory
chown: cannot access `/var/log/syslog': No such file or directory
chown: cannot access `/var/log/mail.log': No such file or directory
chown: cannot access `/var/log/kern.log': No such file or directory
chown: cannot access `/var/log/lpr.log': No such file or directory
chown: cannot access `/var/log/mail.info': No such file or directory
                                                                         [ OK ]
 * Starting kernel log daemon...                                         [ OK ] 
 * Starting OpenBSD Secure Shell server sshd                             [ OK ] 
chown: failed to get attributes of `/var/log/dmesg': No such file or directory
chmod: failed to get attributes of `/var/log/dmesg': No such file or directory
AUTHORIZED_KEYS:
************************

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCFxDP3ZvRqiboqYI6S8OrZQmX95Hx5mM9BR6CLg0mBswSfitvqJpRqVSVfPqiJeVHVIi0bK2Xk4jYbnOMIwtsH0DZqSvjw4ANiJw7+BmdCuYUu366qYJUDBQrWPGFWmEHA15eItLVQ0H14lGU1XhCt/8Ab1FmzUZSac2D4tA/mhSSmIsIl2UoP1MS2sBFvIsZksJ0hu9o0uTp+z4/lDFisg/usrnPBoAwZwwKdWQ9CHCa/xMquolaVO7b4xtB5t/WdWQmB50WNE7IauE32xnqXeAw9QL+9kEangiTipmOP9cuwXb2RckB+ZRpJNcCaUD9yz1nxL8Hl7BMvLJZmxGtN admin@eucalyptus
************************
 * Restarting OpenBSD Secure Shell server sshd


```
Can anyone help me thro' this
thanks.

---

### Post by Rusty au Lait on 2011-12-17
check the iptables on CLC (frontend).

---


---
title: "root on software RAID1 weirdness"
date: 2005-06-19
forum: Server Platforms
---

### Post by skylark on 2005-06-19
Hi

I manually migrated my root fs (including /boot) to a raid1 setup. Previously I played with installing directly onto raid1 with some success but never managed to setup LVM on-top of raid this way. I'm having more success with the LVM aspect of things now but every time I reboot my root partition becomes degraded:

Normally I should see this:
$ cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 sdb2[0] sda2[1]
      155999104 blocks [2/2] [UU]

md0 : active raid1 sda1[1] sdb1[0]
      289024 blocks [2/2] [UU]

unused devices: <none>

But when I reboot this I only get something like:
$ cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 sdb2[0] sda2[1]
      155999104 blocks [2/2] [UU]

md0 : active raid1 sdb1[0]
      289024 blocks [1/2] [U_]

unused devices: <none>

My /etc/fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/vg0/swap   none            swap    sw              0       0
/dev/vg0/tmp    /tmp            xfs     defaults        0       2
/dev/vg0/usr    /usr            xfs     defaults        0       2
/dev/vg0/home   /home           xfs     defaults        0       2
/dev/vg0/var    /var            xfs     defaults        0       2

where vg0 is a volume group setup over /dev/md1 and this works flawlessly.

I can't work out why root on RAID1 (my /dev/md0) keeps losing one of the disks (/dev/sda1) every time I reboot. I have to manually add /dev/sda1 back into the array. 

Any ideas?

PS: I did a full surface scan of both hard drives and no errors were found, so I dont think it is hardware related.

---

### Post by alastair on 2005-06-20
Have a look at the syslog/dmesg output on boot and see if you can see any problems being reported.

I tried installing LVM on RAID1 a while ago but had major problems after every reboot (filesystem corruption etc.) and I gave up (and went just RAID1 on every partition.

---

### Post by skylark on 2005-06-21
[QUOTE=alastair]I tried installing LVM on RAID1 a while ago but had major problems after every reboot (filesystem corruption etc.)[/QUOTE]
When I tried to directly install onto LVM on RAID1 I noticed that after installation had finished my RAID1 partitions were being rebuilt (one of the disks was hot added...). Near the start of reconsturction everything seemed okay, then as it went near 50% (24 hours later!) I noticed a whole bunch of applications wouldn't launch, file sizes seemed wrong etc). I think it is a bug in the Ubuntu install and it really wasted alot of my time.

Anyway back to my problem: I can't see any ansewrs in the logs. Here is var/log/dmseg:

```
FT 0x0100000c) @ 0x0000000000000000
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:15 APIC version 16
ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: BIOS IRQ0 pin2 override ignored.
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
ACPI: IRQ9 used by override.
ACPI: IRQ14 used by override.
ACPI: IRQ15 used by override.
Setting APIC routing to flat
Using ACPI (MADT) for SMP configuration information
Checking aperture...
CPU 0: aperture @ 80000000 size 32 MB
Aperture from northbridge cpu 0 too small (32 MB)
No AGP bridge found
Built 1 zonelists
Kernel command line: root=/dev/md0 ro console=tty0 quiet splash
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 131072 bytes)
time.c: Using 1.193182 MHz PIT timer.
time.c: Detected 2010.326 MHz processor.
Console: colour VGA+ 80x25
Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Memory: 1023052k/1048512k available (1585k kernel code, 24784k reserved, 1008k data, 132k init)
Calibrating delay loop... 3981.31 BogoMIPS (lpj=1990656)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 256 (order: 0, 4096 bytes)
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 00
ACPI: Looking for DSDT in initrd... not found!
Using local APIC NMI watchdog using perfctr0
Using local APIC timer interrupts.
Detected 12.564 MHz APIC timer.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
NET: Registered protocol family 16
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:09.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 14 devices
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
PCI-DMA: Disabling IOMMU.
pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
pnp: 00:00: ioport range 0x1400-0x147f has been reserved
pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
pnp: 00:00: ioport range 0x1800-0x187f has been reserved
pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
audit: initializing netlink socket (disabled)
audit(1119324625.205:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Linux agpgart interface v0.100 (c) Dave Jones
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, khubd not stopped
 Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4084KiB [1 disk] into ram disk... |
...<snip>...
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 132k freed
ACPI: Processor [CPU0] (supports 8 throttling states)
NET: Registered protocol family 1
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
md: raid1 personality registered as nr 3
SCSI subsystem initialized
libata version 1.10 loaded.
sata_nv version 0.5
ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
ACPI: PCI interrupt 0000:00:07.0[A] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:07.0 to 64
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xC800 irq 23
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xC808 irq 23
ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3468 86:3c01 87:4003 88:407f
ata1: dev 0 ATA, max UDMA/133, 312579695 sectors: lba48
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
ata1: dev 0 configured for UDMA/133
scsi0 : sata_nv
ata2: no device found (phy stat 00000000)
scsi1 : sata_nv
elevator: using anticipatory as default io scheduler
  Vendor: ATA       Model: ST3160827AS       Rev: 3.42
  Type:   Direct-Access                      ANSI SCSI revision: 05
ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:08.0 to 64
ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xDC00 irq 22
ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xDC08 irq 22
ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3468 86:3c01 87:4003 88:407f
ata3: dev 0 ATA, max UDMA/133, 312579695 sectors: lba48
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
ata3: dev 0 configured for UDMA/133
scsi2 : sata_nv
ata4: no device found (phy stat 00000000)
scsi3 : sata_nv
  Vendor: ATA       Model: ST3160827AS       Rev: 3.42
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 312579695 512-byte hdwr sectors (160041 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 312579695 512-byte hdwr sectors (160041 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
SCSI device sdb: 312579695 512-byte hdwr sectors (160041 MB)
SCSI device sdb: drive cache: write back
SCSI device sdb: 312579695 512-byte hdwr sectors (160041 MB)
SCSI device sdb: drive cache: write back
 /dev/scsi/host2/bus0/target0/lun0: p1 p2
Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
md: md0 stopped.
md: bind<sdb1>
raid1: raid set md0 active with 1 out of 2 mirrors
Stopping tasks: ====|
Freeing memory...  done (497 pages freed)
Restarting tasks... done
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
EXT3 FS on md0, internal journal
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: SONY CD-RW CRX145E, ATAPI CD/DVD-ROM drive
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
Real Time Clock Driver v1.12
ieee1394: Initialized config rom entry `ip1394'
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md1 stopped.
md: bind<sda2>
md: bind<sdb2>
raid1: raid set md1 active with 2 out of 2 mirrors
cdrom: open failed.
SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
SGI XFS Quota Management subsystem
XFS mounting filesystem dm-1
Ending clean XFS mount for filesystem: dm-1
XFS mounting filesystem dm-2
<etc>
```

And here is the relevant part of a recent /etc/var/syslog:
```
11:30:49 Ubu syslogd 1.4.1#16ubuntu6: restart.
11:30:49 Ubu udev[5603]: creating device node '/dev/vcs1'
11:30:49 Ubu udev[5605]: creating device node '/dev/vcsa1'
11:30:49 Ubu udev[5634]: removing device node '/dev/vcs1'
11:30:49 Ubu udev[5648]: removing device node '/dev/vcsa1'
11:30:49 Ubu udev[5656]: creating device node '/dev/vcs1'
11:30:49 Ubu udev[5664]: creating device node '/dev/vcsa1'
11:30:49 Ubu udev[5672]: removing device node '/dev/vcs1'
11:30:49 Ubu udev[5680]: removing device node '/dev/vcsa1'
11:30:49 Ubu udev[5688]: creating device node '/dev/vcs1'
11:30:49 Ubu udev[5696]: creating device node '/dev/vcsa1'
11:30:49 Ubu udev[5704]: removing device node '/dev/vcs1'
11:30:49 Ubu udev[5712]: removing device node '/dev/vcsa1'
11:30:49 Ubu udev[5713]: creating device node '/dev/vcs1'
11:30:49 Ubu udev[5730]: creating device node '/dev/vcsa1'
11:30:49 Ubu kernel: Inspecting /boot/System.map-2.6.10-5-amd64-generic
11:30:49 Ubu kernel: Loaded 28264 symbols from /boot/System.map-2.6.10-5-amd64-generic.
11:30:49 Ubu kernel: Symbols match kernel version 2.6.10.
11:30:49 Ubu kernel: No module symbols loaded - kernel modules not enabled. 
11:30:49 Ubu kernel: FT 0x0100000c) @ 0x0000000000000000
11:30:49 Ubu kernel: ACPI: Local APIC address 0xfee00000
11:30:49 Ubu kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
11:30:49 Ubu kernel: Processor #0 15:15 APIC version 16
11:30:49 Ubu kernel: ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
11:30:49 Ubu kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
11:30:49 Ubu kernel: IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
11:30:49 Ubu kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
11:30:49 Ubu kernel: ACPI: BIOS IRQ0 pin2 override ignored.
11:30:49 Ubu kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
11:30:49 Ubu kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
11:30:49 Ubu kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
11:30:49 Ubu kernel: ACPI: IRQ9 used by override.
11:30:49 Ubu kernel: ACPI: IRQ14 used by override.
11:30:49 Ubu kernel: ACPI: IRQ15 used by override.
11:30:49 Ubu kernel: Setting APIC routing to flat
11:30:49 Ubu kernel: Using ACPI (MADT) for SMP configuration information
11:30:49 Ubu kernel: Checking aperture...
11:30:49 Ubu kernel: CPU 0: aperture @ 80000000 size 32 MB
11:30:49 Ubu kernel: Aperture from northbridge cpu 0 too small (32 MB)
11:30:49 Ubu kernel: No AGP bridge found
11:30:49 Ubu kernel: Built 1 zonelists
11:30:49 Ubu kernel: Kernel command line: root=/dev/md0 ro console=tty0 quiet splash
11:30:49 Ubu kernel: Initializing CPU#0
11:30:49 Ubu kernel: PID hash table entries: 4096 (order: 12, 131072 bytes)
11:30:49 Ubu kernel: time.c: Using 1.193182 MHz PIT timer.
11:30:49 Ubu kernel: time.c: Detected 2010.326 MHz processor.
11:30:49 Ubu kernel: Console: colour VGA+ 80x25
11:30:49 Ubu kernel: Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
11:30:49 Ubu kernel: Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
11:30:49 Ubu kernel: Memory: 1023052k/1048512k available (1585k kernel code, 24784k reserved, 1008k data, 132k nit)
11:30:49 Ubu kernel: Calibrating delay loop... 3981.31 BogoMIPS (lpj=1990656)
11:30:49 Ubu kernel: Security Framework v1.0.0 initialized
11:30:49 Ubu kernel: SELinux:  Disabled at boot.
11:30:49 Ubu kernel: Mount-cache hash table entries: 256 (order: 0, 4096 bytes)
11:30:49 Ubu kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
11:30:49 Ubu kernel: CPU: L2 Cache: 512K (64 bytes/line)
11:30:49 Ubu kernel: CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 00
11:30:49 Ubu kernel: ACPI: Looking for DSDT in initrd... not found!
11:30:49 Ubu kernel: Using local APIC NMI watchdog using perfctr0
11:30:49 Ubu kernel: Using local APIC timer interrupts.
11:30:49 Ubu kernel: Detected 12.564 MHz APIC timer.
11:30:49 Ubu kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
11:30:49 Ubu kernel: NET: Registered protocol family 16
11:30:49 Ubu kernel: PCI: Using configuration type 1
11:30:49 Ubu kernel: mtrr: v2.0 (20020519)
11:30:49 Ubu kernel: ACPI: Subsystem revision 20050211
11:30:49 Ubu kernel: ACPI: Interpreter enabled
11:30:49 Ubu kernel: ACPI: Using IOAPIC for interrupt routing
11:30:49 Ubu kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
11:30:49 Ubu kernel: PCI: Probing PCI hardware (bus 00)
11:30:49 Ubu kernel: PCI: Transparent bridge - 0000:00:09.0
11:30:49 Ubu kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
11:30:49 Ubu kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
11:30:49 Ubu kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
11:30:49 Ubu kernel: pnp: PnP ACPI init
11:30:49 Ubu kernel: pnp: PnP ACPI: found 14 devices
11:30:49 Ubu kernel: usbcore: registered new driver usbfs
11:30:49 Ubu kernel: usbcore: registered new driver hub
11:30:49 Ubu kernel: PCI: Using ACPI for IRQ routing
11:30:49 Ubu kernel: ** PCI interrupts are no longer routed automatically.  If this
11:30:49 Ubu kernel: ** causes a device to stop working, it is probably because the
11:30:49 Ubu kernel: ** driver failed to call pci_enable_device().  As a temporary
11:30:49 Ubu kernel: ** workaround, the "pci=routeirq" argument restores the old
11:30:49 Ubu kernel: ** behavior.  If this argument makes the device work again,
11:30:49 Ubu kernel: ** please email the output of "lspci" to bjorn.helgaas@hp.com
11:30:49 Ubu kernel: ** so I can fix the driver.
11:30:49 Ubu kernel: PCI-DMA: Disabling IOMMU.
11:30:49 Ubu kernel: pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
11:30:49 Ubu kernel: pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
11:30:49 Ubu kernel: pnp: 00:00: ioport range 0x1400-0x147f has been reserved
11:30:49 Ubu kernel: pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
11:30:49 Ubu kernel: pnp: 00:00: ioport range 0x1800-0x187f has been reserved
11:30:49 Ubu kernel: pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
11:30:49 Ubu kernel: IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
11:30:49 Ubu kernel: audit: initializing netlink socket (disabled)
11:30:49 Ubu kernel: audit(1119324625.205:0): initialized
11:30:49 Ubu kernel: VFS: Disk quotas dquot_6.5.1
11:30:49 Ubu kernel: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
11:30:49 Ubu kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
11:30:49 Ubu kernel: devfs: boot_options: 0x0
11:30:49 Ubu kernel: Initializing Cryptographic API
11:30:49 Ubu kernel: Linux agpgart interface v0.100 (c) Dave Jones
11:30:49 Ubu kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
11:30:49 Ubu kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
11:30:49 Ubu kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
11:30:49 Ubu kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
11:30:49 Ubu kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
11:30:49 Ubu kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
11:30:49 Ubu kernel: io scheduler noop registered
11:30:49 Ubu kernel: io scheduler anticipatory registered
11:30:49 Ubu kernel: io scheduler deadline registered
11:30:49 Ubu kernel: io scheduler cfq registered
11:30:49 Ubu kernel: RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
11:30:49 Ubu kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
11:30:49 Ubu kernel: NET: Registered protocol family 2
11:30:49 Ubu kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
11:30:49 Ubu kernel: TCP: Hash tables configured (established 262144 bind 65536)
11:30:49 Ubu kernel: NET: Registered protocol family 8
11:30:49 Ubu kernel: NET: Registered protocol family 20
11:30:49 Ubu kernel: Restarting tasks...<6> Strange, khubd not stopped
11:30:49 Ubu kernel:  Strange, kswapd0 not stopped
11:30:49 Ubu kernel:  Strange, kseriod not stopped
11:30:49 Ubu kernel:  done
11:30:49 Ubu kernel: ACPI wakeup devices: 
11:30:49 Ubu kernel: HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1 
11:30:49 Ubu kernel: ACPI: (supports S0 S1 S4 S5)
11:30:49 Ubu kernel: RAMDISK: cramfs filesystem found at block 0
11:30:49 Ubu kernel: RAMDISK: Loading 4084KiB [1 disk] into ram disk... |<snip>...done.
11:30:49 Ubu kernel: VFS: Mounted root (cramfs filesystem) readonly.
11:30:49 Ubu kernel: Freeing unused kernel memory: 132k freed
11:30:49 Ubu kernel: ACPI: Processor [CPU0] (supports 8 throttling states)
11:30:49 Ubu kernel: NET: Registered protocol family 1
11:30:49 Ubu kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
11:30:49 Ubu kernel: md: raid1 personality registered as nr 3
11:30:49 Ubu kernel: SCSI subsystem initialized
11:30:49 Ubu kernel: libata version 1.10 loaded.
11:30:49 Ubu kernel: sata_nv version 0.5
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
11:30:49 Ubu kernel: ACPI: PCI interrupt 0000:00:07.0[A] -> GSI 23 (level, low) -> IRQ 23
11:30:49 Ubu kernel: PCI: Setting latency timer of device 0000:00:07.0 to 64
11:30:49 Ubu kernel: ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xC800 irq 23
11:30:49 Ubu kernel: ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xC808 irq 23
11:30:49 Ubu kernel: ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3468 86:3c01 87:4003 88:407f
11:30:49 Ubu kernel: ata1: dev 0 ATA, max UDMA/133, 312579695 sectors: lba48
11:30:49 Ubu kernel: nv_sata: Primary device added
11:30:49 Ubu kernel: nv_sata: Primary device removed
11:30:49 Ubu kernel: nv_sata: Secondary device added
11:30:49 Ubu kernel: nv_sata: Secondary device removed
11:30:49 Ubu kernel: ata1: dev 0 configured for UDMA/133
11:30:49 Ubu kernel: scsi0 : sata_nv
11:30:49 Ubu kernel: ata2: no device found (phy stat 00000000)
11:30:49 Ubu kernel: scsi1 : sata_nv
11:30:49 Ubu kernel: elevator: using anticipatory as default io scheduler
11:30:49 Ubu kernel:   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
11:30:49 Ubu kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
11:30:49 Ubu kernel: ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
11:30:49 Ubu kernel: ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 22 (level, low) -> IRQ 22
11:30:49 Ubu kernel: PCI: Setting latency timer of device 0000:00:08.0 to 64
11:30:49 Ubu kernel: ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xDC00 irq 22
11:30:49 Ubu kernel: ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xDC08 irq 22
11:30:49 Ubu kernel: ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3468 86:3c01 87:4003 88:407f
11:30:49 Ubu kernel: ata3: dev 0 ATA, max UDMA/133, 312579695 sectors: lba48
11:30:49 Ubu kernel: nv_sata: Primary device added
11:30:49 Ubu kernel: nv_sata: Primary device removed
11:30:49 Ubu kernel: nv_sata: Secondary device added
11:30:49 Ubu kernel: nv_sata: Secondary device removed
11:30:49 Ubu kernel: ata3: dev 0 configured for UDMA/133
11:30:49 Ubu kernel: scsi2 : sata_nv
11:30:49 Ubu kernel: ata4: no device found (phy stat 00000000)
11:30:49 Ubu kernel: scsi3 : sata_nv
11:30:49 Ubu kernel:   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
11:30:49 Ubu kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
11:30:49 Ubu kernel: SCSI device sda: 312579695 512-byte hdwr sectors (160041 MB)
11:30:49 Ubu kernel: SCSI device sda: drive cache: write back
11:30:49 Ubu kernel: SCSI device sda: 312579695 512-byte hdwr sectors (160041 MB)
11:30:49 Ubu kernel: SCSI device sda: drive cache: write back
11:30:49 Ubu kernel:  /dev/scsi/host0/bus0/target0/lun0: p1 p2
11:30:49 Ubu kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
11:30:49 Ubu kernel: SCSI device sdb: 312579695 512-byte hdwr sectors (160041 MB)
11:30:49 Ubu kernel: SCSI device sdb: drive cache: write back
11:30:49 Ubu kernel: SCSI device sdb: 312579695 512-byte hdwr sectors (160041 MB)
11:30:49 Ubu kernel: SCSI device sdb: drive cache: write back
11:30:49 Ubu kernel:  /dev/scsi/host2/bus0/target0/lun0: p1 p2
11:30:49 Ubu kernel: Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
11:30:49 Ubu kernel: md: md0 stopped.
11:30:49 Ubu kernel: md: bind<sdb1>
11:30:49 Ubu kernel: raid1: raid set md0 active with 1 out of 2 mirrors
11:30:49 Ubu kernel: Stopping tasks: ====|
11:30:49 Ubu kernel: Freeing memory... done (497 pages freed)
11:30:49 Ubu kernel: Restarting tasks... done
11:30:49 Ubu kernel: kjournald starting.  Commit interval 5 seconds
11:30:49 Ubu kernel: EXT3-fs: mounted filesystem with ordered data mode.
11:30:49 Ubu kernel: EXT3 FS on md0, internal journal
11:30:49 Ubu kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
11:30:49 Ubu kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
11:30:49 Ubu kernel: Probing IDE interface ide0...
11:30:49 Ubu kernel: hda: SONY CD-RW CRX145E, ATAPI CD/DVD-ROM drive
11:30:49 Ubu kernel: Probing IDE interface ide1...
11:30:49 Ubu kernel: Probing IDE interface ide2...
11:30:49 Ubu kernel: Probing IDE interface ide3...
11:30:49 Ubu kernel: Probing IDE interface ide4...
11:30:49 Ubu kernel: Probing IDE interface ide5...
11:30:49 Ubu kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
11:30:49 Ubu kernel: hda: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache
11:30:49 Ubu kernel: Uniform CD-ROM driver Revision: 3.20
11:30:49 Ubu kernel: parport: PnPBIOS parport detected.
11:30:49 Ubu kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
11:30:49 Ubu kernel: lp0: using parport0 (interrupt-driven).
11:30:49 Ubu kernel: mice: PS/2 mouse device common for all mice
11:30:49 Ubu kernel: input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
11:30:49 Ubu kernel: Real Time Clock Driver v1.12
11:30:49 Ubu kernel: ieee1394: Initialized config rom entry `ip1394'
11:30:49 Ubu kernel: sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
11:30:49 Ubu kernel: Capability LSM initialized
11:30:49 Ubu kernel: ts: Compaq touchscreen protocol output
11:30:49 Ubu kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
11:30:49 Ubu kernel: md: md1 stopped.
11:30:49 Ubu kernel: md: bind<sda2>
11:30:49 Ubu kernel: md: bind<sdb2>
11:30:49 Ubu kernel: raid1: raid set md1 active with 2 out of 2 mirrors
11:30:49 Ubu kernel: cdrom: open failed.
11:30:49 Ubu kernel: SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
11:30:49 Ubu kernel: SGI XFS Quota Management subsystem
11:30:49 Ubu kernel: XFS mounting filesystem dm-1
11:30:49 Ubu kernel: Ending clean XFS mount for filesystem: dm-1
11:30:49 Ubu kernel: XFS mounting filesystem dm-2
<etc>
```

Can't work it out at all.

---

### Post by alastair on 2005-06-21
You can speed up a rebuild (if needed) by setting the system raid rebuild speed min/max :

/proc/sys/dev/raid/speed_limit_[max|min]

Via file : /etc/sysctl.conf :

dev.raid.speed_limit_min = 20000
dev.raid.speed_limit_max = 40000

Maybe. Tune to taste.

As for your issue ...

It's odd. I assume all the partitions are the same "type" i.e. "fd" (raid auto)?

fdisk -l /dev/sda
fdisk -l /dev/sdb

---

### Post by skylark on 2005-06-21
Thanks for the rebuild tip; although when rebuliding /dev/md0 it only takes a few seconds since it's a small partition:

```
~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          34      273073+  fd  Linux raid autodetect
/dev/sda2              35       19457   156015247+  fd  Linux raid autodetect

~$ sudo fdisk -l /dev/sdb
Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          34      273073+  fd  Linux raid autodetect
/dev/sdb2              35       19457   156015247+  fd  Linux raid autodetect

```

Some info from mdadm, not sure if the missing super block message is the problem or not:
```
~$ sudo mdadm --query /dev/md0
/dev/md0: 266.56MiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.
/dev/md0: No md super block found, not an md component.

~$ sudo mdadm --examine /dev/md0
mdadm: No super block found on /dev/md0 (Expected magic a92b4efc, got 03ff0113)

~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Mon Jun 20 19:43:18 2005
     Raid Level : raid1
     Array Size : 272960 (266.56 MiB 279.51 MB)
    Device Size : 272960 (266.56 MiB 279.51 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jun 22 10:28:39 2005
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5d946d18:22b0ccbc:1caa01cd:2dad6a85
         Events : 0.6607

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
```
If the super block is a problem, how would I go about fixing it? (although /dev/md1 has the same problems with the super block but on a reboot is always fine).

PS: the block sizes differ slightly from my original post since I re-installed from scratch since posting. One thing I've read recently is that I am meant to zero out the superblock before recreating an array. I didn't do this - I assumed mdadm would overwrite any existing data...

---

### Post by skylark on 2005-11-02
After updating to Breezy the problem I had with /dev/md0 becoming degraded on reboot has been resolved (it magically no longer happens).

I did run into a problem with xfs after updating. All my xfs filesystems failed to mount complaining of "error 990". A xfs_repair fixed this and now everything seems okay. Anyone else run into this?

---


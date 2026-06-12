---
title: "Poor IDE performance when upgrade 6.06 to 8.04"
date: 2008-06-01
forum: Server Platforms
---

### Post by vrillusions on 2008-06-01
I upgraded my Ubuntu Server from 6.06 LTS to 8.04 LTS last weekend and it went relatively pain free.  I was on the server last night and noticed my load climbing up.  Last I saw the load was 84 and it took about 8 minutes from when I issued sudo reboot for it to register, and maybe another 10 minutes for it to close everything down and actually restart.

I noticed mdadm was running it's monthly check of a the raid arrays but didn't think much of it so I restarted the command.  Sure enough the load skyrocketed and I had to reboot.  I noticed /proc/mdstat said the verification was going at about 1800KB/sec (yes, KB).

I ran hdparm and it was giving buffered disk reads of 2.75 MB/sec.  UDMA5 is the active mode on the drive.  I am not positive what the transfer rate was with 6.06 but I'd like to say it was around 50MB/sec.  When I run hdparm -i I get a few "Inappropriate ioctl for device" messages which I know I didn't get before.

This is a dell poweredge server running two seagate PATA drives. I have the raid setup as a mirror between the two drives.  This setup ran for months without issue on 6.06 so the monthly raid verification wasn't an issue then.

For now I've just disabled the monthly check in /etc/default/mdadm but that doesn't solve the slow disk I/O.  Was something changed between 6.06 kernel and 8.04 kernel that may have caused this? any boot options I can pass to it?  Unfortunately the server is located in a datacenter about 25 miles away so I can't do a whole lot of changes that may stop the computer from starting up as I don't want to keep driving there, unless there are a bunch of things to try out.

Here's some system info:
```
vr@rikku:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy
vr@rikku:~$ procinfo
Linux 2.6.24-17-server (buildd@palmer) (gcc 4.2.3 ) #1 SMP Thu May 1 15:05:55 UTC 2008 2CPU [rikku]

Memory:      Total        Used        Free      Shared     Buffers
Mem:       1035120      987548       47572           0      170844
Swap:      2056304           0     2056304

Bootup: Sun Jun  1 04:59:52 2008    Load average: 0.31 0.31 0.28 1/181 29685

user  :       0:36:53.73   2.0%  page in :   711635  disk 1:    33448r  299231w
nice  :       1:49:37.16   5.8%  page out:  4199824  disk 2:    33005r  298614w
system:       0:20:07.92   1.1%  page act:   151543
IOwait:       0:16:20.86   0.9%  page dea:    38410
hw irq:       0:22:15.07   1.2%  page flt: 91184449
sw irq:       0:01:27.20   0.1%  swap in :        0
idle  :   1d  3:42:59.19  89.0%  swap out:        1
uptime:      15:33:58.08         context : 27003675

irq  0:       114 timer                 irq 12:         4 i8042
irq  1:         2 i8042                 irq 14:       105 libata
irq  6:         3 floppy [2]            irq 15:   2198102 libata
irq  8:         3 rtc                   irq 16:   2223745 eth0
irq  9:         0 acpi                  irq 18:        15 aic7xxx
irq 11:         0 ohci_hcd:usb1         irq 19:        15 aic7xxx

vr@rikku:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0] sdb1[1]
      14651136 blocks [2/2] [UU]

md1 : active raid1 sda2[0] sdb2[1]
      9767424 blocks [2/2] [UU]

md2 : active raid1 sda3[0] sdb3[1]
      218748992 blocks [2/2] [UU]

unused devices: <none>
vr@rikku:~$ cat /etc/mtab
/dev/md0 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/md2 /home ext3 rw,relatime,usrquota 0 0
/dev/md1 /var ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
vr@rikku:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   310 MB in  2.00 seconds = 154.81 MB/sec
 Timing buffered disk reads:   10 MB in  3.63 seconds =   2.75 MB/sec
vr@rikku:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST3250624A                              , FwRev=3.AAH   , SerialNo=            5ND585NH
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?8?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

vr@rikku:~$ sudo hdparm -v /dev/sda

/dev/sda:
 IO_support    =  0 (default)
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0

vr@rikku:~$ sudo hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   318 MB in  2.01 seconds = 158.35 MB/sec
 Timing buffered disk reads:   16 MB in  3.23 seconds =   4.95 MB/sec
vr@rikku:~$ grep ^kernel /boot/grub/menu.lst | head -1
kernel          /boot/vmlinuz-2.6.24-17-server root=/dev/md0 ro quiet splash
```

It is a PowerEdge 1650 with dual P3 1266MHz processors and 1gb RAM.

Let me know if there's any other information that may be helpful

(edit)
After looking around some more it looks like the output of dmesg may be useful:

```
vr@rikku:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-17-server (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 15:05:55 UTC 2008 (Ubuntu 2.6.24-17.31-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffe0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 000000003ffefc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffefc00 - 000000003ffff000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 262112) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262112
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262112
[    0.000000] On node 0 totalpages: 262112
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32481 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FDC40 checksum 0
[    0.000000] ACPI: RSDP 000FDC40, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FDC54, 0030 (r1 DELL   PE1650          1 MSFT  100000A)
[    0.000000] ACPI: FACP 000FDC84, 0074 (r1 DELL   PE1650          1 MSFT  100000A)
[    0.000000] ACPI: DSDT 3FFE0000, 282A (r1 DELL   PE1650          1 MSFT  100000A)
[    0.000000] ACPI: FACS 3FFEFC00, 0040
[    0.000000] ACPI: APIC 000FDCF8, 006A (r1 DELL   PE1650          1 MSFT  100000A)
[    0.000000] ACPI: SPCR 000FDD62, 0050 (r1 DELL   PE1650          1 MSFT  100000A)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:11 APIC version 17
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:11 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-15
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec01000] gsi_base[16])
[    0.000000] IOAPIC[1]: apic_id 3, version 17, address 0xfec01000, GSI 16-31
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ffff000:bec01000)
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260065
[    0.000000] Kernel command line: root=/dev/md0 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fec01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1263.509 MHz processor.
[   53.439839] Console: colour VGA+ 80x25
[   53.439847] console [tty0] enabled
[   53.440888] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   53.442403] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   53.508876] Memory: 1026516k/1048448k available (2255k kernel code, 21316k reserved, 1032k data, 384k init, 130944k highmem)
[   53.508894] virtual kernel memory layout:
[   53.508896]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   53.508898]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   53.508901]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   53.508903]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   53.508905]       .init : 0xc043c000 - 0xc049c000   ( 384 kB)
[   53.508907]       .data : 0xc0333ef5 - 0xc0435fe4   (1032 kB)
[   53.508909]       .text : 0xc0100000 - 0xc0333ef5   (2255 kB)
[   53.508915] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   53.509013] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   53.658957] Calibrating delay using timer specific routine.. 2528.14 BogoMIPS (lpj=12640719)
[   53.659027] Security Framework initialized
[   53.659050] SELinux:  Disabled at boot.
[   53.659084] AppArmor: AppArmor initialized
[   53.659095] Failure registering capabilities with primary security module.
[   53.659115] Mount-cache hash table entries: 512
[   53.659398] Initializing cgroup subsys ns
[   53.659410] Initializing cgroup subsys cpuacct
[   53.659431] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   53.659451] CPU: L1 I cache: 16K, L1 D cache: 16K
[   53.659456] CPU: L2 cache: 512K
[   53.659461] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   53.659480] Compat vDSO mapped to ffffe000.
[   53.659508] Checking 'hlt' instruction... OK.
[   53.699466] SMP alternatives: switching to UP code
[   53.701821] Early unpacking initramfs... done
[   54.234715] ACPI: Core revision 20070126
[   54.234838] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   54.237154] CPU0: Intel(R) Pentium(R) III CPU family      1266MHz stepping 01
[   54.237194] SMP alternatives: switching to SMP code
[   54.238138] Booting processor 1/0 eip 3000
[   54.248447] Initializing CPU#1
[   54.398523] Calibrating delay using timer specific routine.. 2526.98 BogoMIPS (lpj=12634905)
[   54.398536] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   54.398551] CPU: L1 I cache: 16K, L1 D cache: 16K
[   54.398554] CPU: L2 cache: 512K
[   54.398559] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   54.398966] CPU1: Intel(R) Pentium(R) III CPU family      1266MHz stepping 01
[   54.399001] Total of 2 processors activated (5055.12 BogoMIPS).
[   54.399331] ENABLING IO-APIC IRQs
[   54.399566] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   54.618612] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   54.638648] Brought up 2 CPUs
[   54.638720] CPU0 attaching sched-domain:
[   54.638726]  domain 0: span 03
[   54.638729]   groups: 01 02
[   54.638735] CPU1 attaching sched-domain:
[   54.638738]  domain 0: span 03
[   54.638741]   groups: 02 01
[   54.639172] net_namespace: 64 bytes
[   54.639191] Booting paravirtualized kernel on bare hardware
[   54.640153] Time:  4:59:53  Date: 06/01/08
[   54.640215] NET: Registered protocol family 16
[   54.640628] EISA bus registered
[   54.640638] ACPI: bus type pci registered
[   54.657123] PCI: PCI BIOS revision 2.10 entry at 0xfc6ae, last bus=2
[   54.657128] PCI: Using configuration type 1
[   54.657133] Setting up standard PCI resources
[   54.660130] ACPI: EC: Look up EC in DSDT
[   54.664826] ACPI: Interpreter enabled
[   54.664832] ACPI: (supports S0 S4 S5)
[   54.664852] ACPI: Using IOAPIC for interrupt routing
[   54.673046] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   54.673437] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   54.675115] ACPI: PCI Root Bridge [PCI1] (0000:01)
[   54.675402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   54.676093] ACPI: PCI Root Bridge [PCI2] (0000:02)
[   54.676197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI2._PRT]
[   54.676734] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 11 12 14)
[   54.676923] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 11 12 14)
[   54.677110] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 11 12 14)
[   54.677298] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 9 11 12 14)
[   54.677483] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.677670] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.677858] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.678045] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.678233] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.678442] ACPI: PCI Interrupt Link [LNKJ] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.678630] ACPI: PCI Interrupt Link [LNKK] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.678818] ACPI: PCI Interrupt Link [LNKL] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.679015] ACPI: PCI Interrupt Link [LNKM] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.679204] ACPI: PCI Interrupt Link [LNKN] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.679392] ACPI: PCI Interrupt Link [LNKO] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.679581] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 9 11 12 14) *0, disabled.
[   54.679772] ACPI: PCI Interrupt Link [LUSB] (IRQs 3 4 5 6 7 *11 12 14)
[   54.680005] Linux Plug and Play Support v0.97 (c) Adam Belay
[   54.680066] pnp: PnP ACPI init
[   54.680081] ACPI: bus type pnp registered
[   54.689708] pnp: PnP ACPI: found 11 devices
[   54.689713] ACPI: ACPI bus type pnp unregistered
[   54.689722] PnPBIOS: Disabled by ACPI PNP
[   54.690235] PCI: Using ACPI for IRQ routing
[   54.690242] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   54.728385] NET: Registered protocol family 8
[   54.728389] NET: Registered protocol family 20
[   54.728452] NetLabel: Initializing
[   54.728456] NetLabel:  domain hash size = 128
[   54.728459] NetLabel:  protocols = UNLABELED CIPSOv4
[   54.728483] NetLabel:  unlabeled traffic allowed by default
[   54.728557] AppArmor: AppArmor Filesystem Enabled
[   54.738346] Time: tsc clocksource has been installed.
[   54.758412] system 00:07: ioport range 0x800-0x89f has been reserved
[   54.758418] system 00:07: ioport range 0x8a0-0x8af has been reserved
[   54.758423] system 00:07: ioport range 0x8c0-0x8c3 has been reserved
[   54.758428] system 00:07: ioport range 0xc00-0xcd7 has been reserved
[   54.758433] system 00:07: ioport range 0xf50-0xf58 has been reserved
[   54.758454] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   54.758460] system 00:0a: iomem range 0x100000-0x3fffffff could not be reserved
[   54.758465] system 00:0a: iomem range 0x0-0x0 could not be reserved
[   54.758470] system 00:0a: iomem range 0xf0000-0xfffff could not be reserved
[   54.758475] system 00:0a: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   54.758481] system 00:0a: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   54.758486] system 00:0a: iomem range 0xffe00000-0xffffffff could not be reserved
[   54.789262] NET: Registered protocol family 2
[   54.888396] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   54.888981] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   54.893059] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   54.895337] TCP: Hash tables configured (established 131072 bind 65536)
[   54.895344] TCP reno registered
[   54.918628] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[   55.298033] Switched to high resolution mode on CPU 0
[   55.378161]  it is
[   55.933456] Freeing initrd memory: 7984k freed
[   55.934762] audit: initializing netlink socket (disabled)
[   55.934791] audit(1212296394.300:1): initialized
[   55.935151] highmem bounce pool size: 64 pages
[   55.935160] Total HugeTLB memory allocated, 0
[   55.939251] VFS: Disk quotas dquot_6.5.1
[   55.939432] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   55.939865] io scheduler noop registered
[   55.939871] io scheduler anticipatory registered
[   55.939875] io scheduler deadline registered (default)
[   55.939901] io scheduler cfq registered
[   55.939928] Boot video device is 0000:00:0c.0
[   55.958293] isapnp: Scanning for PnP cards...
[   56.314503] isapnp: No Plug & Play device found
[   56.372125] Real Time Clock Driver v1.12ac
[   56.372296] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   56.372452] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   56.373439] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   56.374939] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   56.375069] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   56.375363] PNP: No PS/2 controller found. Probing ports directly.
[   56.377313] serio: i8042 KBD port at 0x60,0x64 irq 1
[   56.377328] serio: i8042 AUX port at 0x60,0x64 irq 12
[   56.410077] mice: PS/2 mouse device common for all mice
[   56.410346] EISA: Probing bus 0 at eisa.0
[   56.410353] EISA: Cannot allocate resource for mainboard
[   56.410394] EISA: Detected 0 cards.
[   56.410399] cpuidle: using governor ladder
[   56.410403] cpuidle: using governor menu
[   56.410690] NET: Registered protocol family 1
[   56.410748] Using IPI No-Shortcut mode
[   56.410810] registered taskstats version 1
[   56.410981]   Magic number: 12:935:968
[   56.411001]   hash matches device ttyb9
[   56.411147] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   56.412053] Freeing unused kernel memory: 384k freed
[   56.716186] fuse init (API version 7.9)
[   56.797410] device-mapper: uevent: version 1.0.3
[   56.797508] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   56.835353] md: linear personality registered for level -1
[   56.845202] md: multipath personality registered for level -4
[   56.854636] md: raid0 personality registered for level 0
[   56.866148] md: raid1 personality registered for level 1
[   56.875397] xor: automatically using best checksumming function: pIII_sse
[   56.917126]    pIII_sse  :  2905.200 MB/sec
[   56.917130] xor: using function: pIII_sse (2905.200 MB/sec)
[   56.918971] async_tx: api initialized (async)
[   57.087165] raid6: int32x1    392 MB/s
[   57.256936] raid6: int32x2    442 MB/s
[   57.426868] raid6: int32x4    405 MB/s
[   57.596759] raid6: int32x8    342 MB/s
[   57.766689] raid6: mmxx1     1149 MB/s
[   57.936574] raid6: mmxx2     1374 MB/s
[   58.106490] raid6: sse1x1    1016 MB/s
[   58.276405] raid6: sse1x2    1388 MB/s
[   58.276409] raid6: using algorithm sse1x2 (1388 MB/s)
[   58.276415] md: raid6 personality registered for level 6
[   58.276418] md: raid5 personality registered for level 5
[   58.276422] md: raid4 personality registered for level 4
[   58.331717] md: raid10 personality registered for level 10
[   58.996687] SCSI subsystem initialized
[   59.006258] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   59.006266] Copyright (c) 1999-2006 Intel Corporation.
[   59.006374] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 17 (level, low) -> IRQ 16
[   59.273611] e1000: 0000:01:02.0: e1000_probe: (PCI:66MHz:64-bit) 00:06:5b:ec:d4:14
[   59.273784] Floppy drive(s): fd0 is 1.44M
[   59.273914] usbcore: registered new interface driver usbfs
[   59.273971] usbcore: registered new interface driver hub
[   59.287790] FDC 0 is a National Semiconductor PC87306
[   59.291643] usbcore: registered new device driver usb
[   59.335944] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   59.336400] ACPI: PCI Interrupt Link [LUSB] enabled at IRQ 11
[   59.336417] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [LUSB] -> GSI 11 (level, low) -> IRQ 11
[   59.336443] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   59.336891] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[   59.336919] ohci_hcd 0000:00:0f.2: irq 11, io mem 0xfe100000
[   59.377883] libata version 3.00 loaded.
[   59.384737] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   59.384796] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[   59.397968] usb usb1: configuration #1 chosen from 1 choice
[   59.398017] hub 1-0:1.0: USB hub found
[   59.398032] hub 1-0:1.0: 4 ports detected
[   59.643828] e1000: 0000:01:04.0: e1000_probe: (PCI:66MHz:64-bit) 00:06:5b:ec:d4:15
[   59.684052] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[   59.684236] ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   74.887087] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   74.887091]         <Adaptec aic7899 Ultra160 SCSI adapter>
[   74.887094]         aic7899: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   74.887096]
[   74.887365] ACPI: PCI Interrupt 0000:01:06.1[B] -> GSI 19 (level, low) -> IRQ 19
[   90.098567] scsi1 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   90.098571]         <Adaptec aic7899 Ultra160 SCSI adapter>
[   90.098573]         aic7899: Ultra160 Wide Channel B, SCSI Id=7, 32/253 SCBs
[   90.098576]
[   90.113314] scsi2 : pata_serverworks
[   90.113415] scsi3 : pata_serverworks
[   90.113472] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8b0 irq 14
[   90.113477] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8b8 irq 15
[   90.388737] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[   90.388746] ata1: failed to recover some devices, retrying in 5 secs
[   95.855597] ata1.00: ATAPI: SAMSUNG CD-ROM SN-124, N102, max UDMA/33
[   96.055492] ata1.00: configured for UDMA/33
[   96.304895] ata2.00: ATA-7: ST3250624A, 3.AAH, max UDMA/100
[   96.304904] ata2.00: 488397168 sectors, multi 8: LBA48
[   96.354606] ata2.01: ATA-7: ST3250624A, 3.AAH, max UDMA/100
[   96.354611] ata2.01: 488397168 sectors, multi 8: LBA48
[   96.354631] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   96.354638] ata2.01: simplex DMA is claimed by other device, disabling DMA
[   96.421301] ata2.00: configured for PIO4
[   96.487600] ata2.01: configured for PIO4
[   96.488073] scsi 2:0:0:0: CD-ROM            SAMSUNG  CD-ROM SN-124    N102 PQ: 0 ANSI: 5
[   96.488783] scsi 3:0:0:0: Direct-Access     ATA      ST3250624A       3.AA PQ: 0 ANSI: 5
[   96.489253] scsi 3:0:1:0: Direct-Access     ATA      ST3250624A       3.AA PQ: 0 ANSI: 5
[   96.510136] Driver 'sd' needs updating - please use bus_type methods
[   96.510375] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   96.510408] sd 3:0:0:0: [sda] Write Protect is off
[   96.510414] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   96.510453] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   96.510558] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   96.510579] sd 3:0:0:0: [sda] Write Protect is off
[   96.510583] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   96.510618] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   96.510624]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   96.521273] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   96.521282] Uniform CD-ROM driver Revision: 3.20
[   96.521374] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   96.528097]  sda1 sda2 sda3 sda4
[   96.551876] sd 3:0:0:0: [sda] Attached SCSI disk
[   96.551974] sd 3:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   96.551998] sd 3:0:1:0: [sdb] Write Protect is off
[   96.552003] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   96.552040] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   96.552124] sd 3:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   96.552144] sd 3:0:1:0: [sdb] Write Protect is off
[   96.552149] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   96.552184] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   96.552190]  sdb: sdb1 sdb2 sdb3 sdb4
[   96.589629] sd 3:0:1:0: [sdb] Attached SCSI disk
[   96.598854] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   96.598897] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   96.598958] sd 3:0:1:0: Attached scsi generic sg2 type 0
[   97.134141] md: md2 stopped.
[   97.371174] md: md1 stopped.
[   97.404343] md: md0 stopped.
[   97.426484] md: bind<sdb1>
[   97.450509] md: md2 stopped.
[   97.587363] md: bind<sdb3>
[   97.588803] md: bind<sda3>
[   97.608858] raid1: raid set md2 active with 2 out of 2 mirrors
[   97.609047] md: md1 stopped.
[   97.704802] md: bind<sdb2>
[   97.714003] md: bind<sda2>
[   97.736585] raid1: raid set md1 active with 2 out of 2 mirrors
[   97.736774] md: md0 stopped.
[   97.736796] md: unbind<sdb1>
[   97.736807] md: export_rdev(sdb1)
[   97.896035] md: bind<sdb1>
[   97.896912] md: bind<sda1>
[   97.916991] raid1: raid set md0 active with 2 out of 2 mirrors
[   98.088746] kjournald starting.  Commit interval 5 seconds
[   98.088765] EXT3-fs: mounted filesystem with ordered data mode.
[  103.431435] input: PC Speaker as /devices/platform/pcspkr/input/input1
[  103.820886] Linux agpgart interface v0.102
[  103.913910] agpgart: unable to determine aperture size.
[  103.913963] agpgart: agp_backend_initialize() failed.
[  103.913975] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22
[  103.913992] agpgart: unable to determine aperture size.
[  103.914033] agpgart: agp_backend_initialize() failed.
[  103.914041] agpgart-serverworks: probe of 0000:00:00.1 failed with error -22
[  103.914054] agpgart: ServerWorks CNB20HE is unsupported due to lack of documentation.
[  103.914111] agpgart: ServerWorks CNB20HE is unsupported due to lack of documentation.
[  104.001272] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[  104.196729] scb2_flash: warning - can't reserve rom window, continuing
[  104.313877] CFI: Found no SCB2 BIOS Flash device at location zero
[  104.313885] scb2_flash: flash probe failed!
[  104.360938] input: Power Button (FF) as /devices/virtual/input/input2
[  104.480606] ACPI: Power Button (FF) [PWRF]
[  104.510926] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[  105.133019] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  106.781897] NET: Registered protocol family 10
[  106.782597] lo: Disabled Privacy Extensions
[  108.265720] lp: driver loaded but no devices found
[  108.803662] Adding 1028152k swap on /dev/sda4.  Priority:-1 extents:1 across:1028152k
[  108.860758] Adding 1028152k swap on /dev/sdb4.  Priority:-2 extents:1 across:1028152k
[  109.362361] EXT3 FS on md0, internal journal
[  110.460735] kjournald starting.  Commit interval 5 seconds
[  110.493909] EXT3 FS on md2, internal journal
[  110.493918] EXT3-fs: mounted filesystem with ordered data mode.
[  110.533410] kjournald starting.  Commit interval 5 seconds
[  110.535236] EXT3 FS on md1, internal journal
[  110.535242] EXT3-fs: mounted filesystem with ordered data mode.
[  112.038842] ip_tables: (C) 2000-2006 Netfilter Core Team
[  117.345789] eth0: no IPv6 routers present
[  668.157538] tun: Universal TUN/TAP device driver, 1.6
[  668.157556] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  668.159834] tun0: Disabled Privacy Extensions

```

Some noteworthy lines in there are in the 90.x range.  Including disabling dma and configuring for PIO4.  Also says driver "sd" needs updating?

---

### Post by vrillusions on 2008-06-01
Solved my own problem :D

After looking at the dmesg output more closely I did some more searching around and found [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175022).  The [solution](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/175022/comments/2) is to enable the pata_ module you need and blacklist generic_ata in the initramfs file.

```
$ lspci | grep -i ide
00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 93)
$ lsmod | grep -i ^libata
libata                159344  3 pata_serverworks,pata_acpi,ata_generic

```

It lists pata_serverworks as a dependant, and after some more searching that is indeed the module the ide interface uses.  So I add the following to the end of /etc/initramfs-tools/modules (it was blank except for a few commented lines)

```
pata_serverworks
blacklist ata_generic
```

then update the initramfs file:

```
sudo update-initramfs -u
```

reboot and now transfers speeds are MUCH better:

```
$ lsmod | grep -i ^libata
libata                159344  3 pata_acpi,ata_generic,pata_serverworks
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   432 MB in  2.01 seconds = 215.40 MB/sec
 Timing buffered disk reads:  154 MB in  3.19 seconds =  48.20 MB/sec

```

It is still loading that ata_generic module but pata_serverworks is getting loaded first, so it uses that module for the drives.

---

### Post by windependence on 2008-06-01
I have never been a big fan of software RAID. Using a hardware RAID controller takes the load off the CPU since the work is being done on the card. Should one of these software RAID processes run out of control or lock up, it can easily crash your machine. Seeing as how you can buy RAID controllers pretty cheap now for ATA and SATA drives and even cheaper on eBay, I don't think software RAID is worth the trouble.

-Tim

---

### Post by 3d_eye on 2008-06-03
[QUOTE=vrillusions;5095767]
It is a PowerEdge 1650 with dual P3 1266MHz processors and 1gb RAM.

Hi,
Sorry for inquiring about a different Linux distribution... :popcorn:

I have a problem booting CentOS (ClarkConnect Community Ed. 4.2 SP1, to be precise) on an IBM xSeries 305, with WD 500 GB drives attached to the same controller you have in your Dell server:

IDE interface: Broadcom CSB5 IDE Controller

Obviously my problem arises from the fact that the IBM BIOS does not support 48-bit LBA. It reports the WD drives with a size of 137438 MB.
After the BIOS messages are displayed, I get the follwing error:
"NMI issued, check event log
Press Esc key to turn off NMI or other key to reboot"

Question: Does your PowerEdge recognize your 250 GB Seagate drives with the correct size?
Do you know if it is possible to use large drives requiring 48-bit LBA reliably in a machine with a BIOS lacking 48-bit LBA support?

Many thanks in advance, regards

Peter

---


---
title: "Paravirtualized Xen DomU Support for 8.10"
date: 2008-11-11
forum: Virtualisation
---

### Post by elalonde on 2008-11-11
Hello, I have searched the forums but cannot determine whether there are plans to support a paravirtualized Xen DomU for Ubuntu Intrepid. I understand that there are *no* plans to support Dom0, and that Ubuntu already works as DomU in non-paravirtualized form, but I seek to learn whether a paravirtualized DomU is possible now in 8.10 or whether there exist plans to later support this functionality.

---

### Post by dbaxps on 2008-12-28
Create Intrepid Server HVM DomU  at Xen 3.3.0 Hardy Dom0,Xen 3.3.1 OpenSuse 11.1 Dom0,Xen 3.3.1-rc4 CentOS 5.2 Dom0 via profile like:
[root@ServerXen331 vm]# cat  intrepid.hvm 
name = "InrepidHVM"
builder = "hvm"
memory = "1024"
disk = ['phy:/dev/sdb7,hda,w','file:/etc/xen/isos/IntrepidSRV.iso,hdc:cdrom,r']
vif = [ 'bridge=eth0' ]
device_model = "/usr/lib64/xen/bin/qemu-dm"
kernel = "/usr/lib/xen/boot/hvmloader"
vnc=1
boot="cd"
vcpus=1
serial = "pty" # enable serial console
on_reboot   = 'restart'
on_crash    = 'restart'
***********************************************************
Notice profile works like PV drivers have been implemented
***********************************************************
When done , load PV DomU with same image device via pygrub :-
[root@ServerXen331 vm]# cat  intrepid.py
memory = 4096
name = "IntrepidPV"
bootloader="/usr/bin/pygrub"
vif = [ 'bridge = eth0' ]
disk = [ 'phy:/dev/sdb7,xvda,w']
vfb = ['type=vnc,vncunused=1']
I believe there was a "special patch" to Xen 3.3.0 official release
that pygrub can boot recent Linux PV domUs that may contain the new
ext3 256 Byte inodes. fsimage.so also gets involved
Earlier Xen Dom0 requires some additional efforts like :-
[http://www.opensolaris.org/jive/thread.jspa?threadID=83273&tstart=0](http://www.opensolaris.org/jive/thread.jspa?threadID=83273&tstart=0)
Actually , the problem appears to be at Xen Dom0 side. Not much , what
could be done for Intrepid Server Distro.
The link above is a nice manual regarding this issue

---

### Post by dbaxps on 2008-12-28
pyGRUB  version 0.6
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Ubuntu 8.10 (hvc0) , kernel 2.6.27-7-server                            
&#9474; Ubuntu 8.10, kernel 2.6.27-7-server                                    
&#9474; Ubuntu 8.10, kernel 2.6.27-7-server (recovery mode)                    
&#9474; Ubuntu 8.10, memtest86+                                                
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
     Use the ^ and v keys to select which entry is highlighted.
     Press enter to boot the selected OS. 'e' to edit the
     commands before booting, 'a' to modify the kernel arguments
     before booting, or 'c' for a command line.




     Will boot selected entry in  6 seconds


Started domain UbuntuPVS810
                           [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-server (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 07:20:47 UTC 2008 (Ubuntu 2.6.27-7.14-server)
[    0.000000] Command line: root=/dev/xvda1 ro 2 console=hvc0
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] ACPI in unprivileged domain disabled
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  Xen: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  Xen: 00000000000a0000 - 0000000000100000 (reserved)
[    0.000000]  Xen: 0000000000100000 - 000000000241e000 (usable)
[    0.000000]  Xen: 000000000241e000 - 0000000002c21000 (reserved)
[    0.000000]  Xen: 0000000002c21000 - 0000000100000000 (usable)
[    0.000000] last_pfn = 0x100000 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000] last_map_addr: 100000000 end: 100000000
[    0.000000] RAMDISK: 008b7000 - 0241e000
[    0.000000] DMI not present or invalid.
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000100000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000100000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [0000000000008000 -  0000000000027fff] pages 20
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 0100000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0002c21000 - 0002c3c000]   XEN PAGETABLES ==> [0002c21000 - 0002c3c000]
[    0.000000]   #3 [0000200000 - 00008b6f9c]    TEXT DATA BSS ==> [0000200000 - 00008b6f9c]
[    0.000000]   #4 [00008b7000 - 000241e000]          RAMDISK ==> [00008b7000 - 000241e000]
[    0.000000]   #5 [0002c3c000 - 0003423000]          PGTABLE ==> [0002c3c000 - 0003423000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0000241e
[    0.000000]     0: 0x00002c21 -> 0x00100000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] No local APIC present
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000000241e000 - 0000000002c21000
[    0.000000] PCI: Warning: Cannot find a gap in the 32bit address range
[    0.000000] PCI: Unassigned devices with 32bit resource registers may break!
[    0.000000] Allocating PCI resources starting at 100200000 (gap: 100100000:400000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028324
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/xvda1 ro 2 console=hvc0
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Detected 3005.554 MHz processor.
[    0.010000] Console: colour dummy device 80x25
[    0.010000] console [tty0] enabled
[    0.010000] console [hvc0] enabled
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Memory: 4076624k/4194304k available (3110k kernel code, 109092k reserved, 1573k data, 536k init)
[    0.010000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.010000] installing Xen timer for CPU 0
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6011.10 BogoMIPS (lpj=30055540)
[    0.010000] Security Framework initialized
[    0.010000] SELinux:  Disabled at boot.
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 0/0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] SMP alternatives: switching to UP code
[    0.016779] Freeing SMP alternatives: 24k freed
[    0.016831] cpu 0 spinlock event irq 1
[    0.016893] Brought up 1 CPUs
[    0.017149] net_namespace: 1552 bytes
[    0.017155] Booting paravirtualized kernel on Xen
[    0.017158] Xen version: 3.3.1-rc4 (preserve-AD)
[    0.017257] Grant table initialized
[    0.037009] Time: 165:165:165  Date: 165/165/65
[    0.037038] NET: Registered protocol family 16
[    0.037624] PCI: Fatal: No config space access function found
[    0.038287] ACPI: Interpreter disabled.
[    0.040003] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.040048] pnp: PnP ACPI: disabled
[    0.040103] xen_balloon: Initialising balloon driver.
[    0.040464] PCI: System does not support PCI
[    0.040472] PCI: System does not support PCI
[    0.070050] NET: Registered protocol family 8
[    0.070055] NET: Registered protocol family 20
[    0.070090] NetLabel: Initializing
[    0.070094] NetLabel:  domain hash size = 128
[    0.070097] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.070110] NetLabel:  unlabeled traffic allowed by default
[    0.070116] PCI-GART: No AMD northbridge found.
[    0.070440] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.070444]    actual entries 65586
[    0.070512] AppArmor: AppArmor Filesystem Enabled
[    0.070905] NET: Registered protocol family 2
[    0.160149] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.161331] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.164047] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.164506] TCP: Hash tables configured (established 524288 bind 65536)
[    0.164512] TCP reno registered
[    0.190085] NET: Registered protocol family 1
[    0.190170] checking if image is initramfs... it is
[    0.208810] Freeing initrd memory: 28060k freed
[    0.217633] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.218034] audit: initializing netlink socket (disabled)
[    0.218049] type=2000 audit(1230489042.402:1): initialized
[    0.222558] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.224863] VFS: Disk quotas dquot_6.5.1
[    0.224948] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.225045] msgmni has been set to 8246
[    0.225154] io scheduler noop registered
[    0.225161] io scheduler anticipatory registered
[    0.225168] io scheduler deadline registered (default)
[    0.225290] io scheduler cfq registered
[    0.250827] Linux agpgart interface v0.103
[    0.250838] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    0.252619] brd: module loaded
[    0.252678] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.252830] PNP: No PS/2 controller found. Probing ports directly.
[    0.253651] i8042.c: No controller found.
[    0.270675] mice: PS/2 mouse device common for all mice
[    0.270722] rtc_cmos: probe of rtc_cmos failed with error -16
[    0.270798] cpuidle: using governor ladder
[    0.270802] cpuidle: using governor menu
[    0.271042] TCP cubic registered
[    0.271058] IO APIC resources could be not be allocated.
[    0.271218] registered taskstats version 1
[    0.271228] XENBUS: Device with no driver: device/vbd/51712
[    0.271232] XENBUS: Device with no driver: device/vif/0
[    0.271235] XENBUS: Device with no driver: device/console/0
[    0.271246]   Magic number: 1:252:3141
[    0.271316] /build/buildd/linux-2.6.27/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.271322] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.271325] EDD information not available.
[    0.271343] Freeing unused kernel memory: 536k freed
[    0.271482] Write protecting the kernel read-only data: 4344k
Loading, please wait...
Couldnt get a file descriptor referring to the console
Begin: Loading essential drivers... ...
[    0.335554] fuse init (API version 7.9)
[    0.400924] thermal: Unknown symbol acpi_processor_set_thermal_limit
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Waiting for root file system... ...
[    1.132622] blkfront: xvda: barriers enabled
[    1.132922]  xvda: xvda1 xvda2 < xvda5 >
Done.
Begin: Running /scripts/local-premount ...
Begin: Waiting for resume device... ...
Done.
Done.
[    6.361132] kjournald starting.  Commit interval 5 seconds
[    6.361147] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
 * Reading files needed to boot...                                       [ OK ] 
 * Setting preliminary keymap...                                         [ OK ] 
 * Setting the system clock
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.
 * Unable to set System Clock to: Sun Dec 28 18:30:51 UTC 2008
 * Starting basic networking...                                          [ OK ] 
 * Starting kernel event manager...                                             [    9.693455] udevd version 124 started
                                                                         [ OK ]
 * Loading hardware drivers...                                                  [    9.924940] Initialising Xen virtual ethernet driver.
[   10.073958] input: PC Speaker as /devices/platform/pcspkr/input/input1
                                                                         [ OK ]
 * Setting the system clock
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.
 * Unable to set System Clock to: Sun Dec 28 18:30:53 UTC 2008
 * Loading kernel modules...                                                     * Loading manual drivers...                                                                                      [   11.076817] loop: module loaded
[   11.117702] lp: driver loaded but no devices found
                                                                         [ OK ]
 * Setting kernel variables (/etc/sysctl.conf)...                        [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-process-security.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-tcp-timestamps-workaround.c[ OK ]        
 * Setting kernel variables (/etc/sysctl.d/30-tracker.conf)...           [ OK ] 
 * Activating swap...                                                    [ OK ] 
 * Checking root file system...                                                 fsck 1.41.3 (12-Oct-2008)
/dev/xvda1: clean, 122914/960992 files, 768462/3837519 blocks
                                                                         [ OK ]
 * Checking file systems...                                                     fsck 1.41.3 (12-Oct-2008)
                                                                         [ OK ]
 * Mounting local filesystems...                                         [ OK ] 
 * Activating swapfile swap...                                           [ OK ] 
$Mounting securityfs on /sys/kernel/security: done.
Loading AppArmor profiles : done.
 * Skipping firewall: ufw (not enabled)...                               [ OK ] 
 * Configuring network interfaces...                                     [ OK ] 
 * Setting up console font and keymap...                                 [ OK ] 
 * Starting system log daemon...                                         [ OK ] 
 * Doing Wacom setup...                                                         cat: */id: No such file or directory
                                                                         [ OK ]
 * Starting kernel log daemon...                                         [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Starting OpenBSD Secure Shell server sshd                             [ OK ] 
 * Starting Common Unix Printing System: cupsd                           [ OK ] 
 * Starting powernowd...                                                         * CPU frequency scaling not supported...                                                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
[   22.696155] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
 * Starting NetworkManager...                                            [ OK ] 
 * Starting GNOME Display Manager...                                     [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
 * Starting anac(h)ronistic cron anacron                                 [ OK ] 
 * Starting deferred execution scheduler atd                             [ OK ] 
 * Starting periodic command scheduler crond                             [ OK ] 
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
 * Checking battery state...                                             [ OK ] 

Ubuntu 8.10 ServerUbuntu810 hvc0

ServerUbuntu810 login: root
Password: 
Last login: Sun Dec 28 13:26:42 EST 2008 on hvc0
Linux ServerUbuntu810 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
root@ServerUbuntu810:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:3e:1b:8b:d2  
          inet addr:192.168.1.45  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:fe1b:8bd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1965 (1.9 KB)  TX bytes:4953 (4.9 KB)
          Interrupt:9 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ServerUbuntu810:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             15G  2.8G   11G  20% /
tmpfs                 2.1G     0  2.1G   0% /lib/init/rw
varrun                2.1G   96K  2.1G   1% /var/run
varlock               2.1G     0  2.1G   0% /var/lock
udev                  2.1G  2.6M  2.1G   1% /dev
tmpfs                 2.1G     0  2.1G   0% /dev/shm

---

### Post by dbaxps on 2008-12-28
[root@ServerXen331 ~]# xm dmesg
 __  __            _____  _____  _             _  _   
 \ \/ /___ _ __   |___ / |___ / / |   _ __ ___| || |  
  \  // _ \ '_ \    |_ \   |_ \ | |__| '__/ __| || |_ 
  /  \  __/ | | |  ___) | ___) || |__| | | (__|__   _|
 /_/\_\___|_| |_| |____(_)____(_)_|  |_|  \___|  |_|  
                                                      
(XEN) Xen version 3.3.1-rc4 (root@) (gcc version 4.1.2 20071124 (Red Hat 4.1.2-42)) Sun Dec 28 14:34:38 MSK 2008
(XEN) Latest ChangeSet: Fri Dec 19 15:16:13 2008 +0000 18544:2c83b2d7cd20
(XEN) Command line: 
(XEN) Video information:
(XEN)  VGA is text mode 80x25, font 8x16
(XEN)  VBE/DDC methods: none; EDID transfer time: 0 seconds
(XEN)  EDID info not retrieved because no DDC retrieval method detected
(XEN) Disc information:
(XEN)  Found 0 MBR signatures
(XEN)  Found 2 EDD information structures
(XEN) Xen-e820 RAM map:
(XEN)  0000000000000000 - 000000000009ec00 (usable)
(XEN)  000000000009ec00 - 00000000000a0000 (reserved)
(XEN)  00000000000e4000 - 0000000000100000 (reserved)
(XEN)  0000000000100000 - 00000000cff80000 (usable)
(XEN)  00000000cff80000 - 00000000cff8e000 (ACPI data)
(XEN)  00000000cff8e000 - 00000000cffe0000 (ACPI NVS)
(XEN)  00000000cffe0000 - 00000000d0000000 (reserved)
(XEN)  00000000fee00000 - 00000000fee01000 (reserved)
(XEN)  00000000ffe00000 - 0000000100000000 (reserved)
(XEN)  0000000100000000 - 0000000230000000 (usable)
(XEN) System RAM: 8191MB (8387704kB)
(XEN) ACPI: RSDP 000FBB80, 0014 (r0 ACPIAM)
(XEN) ACPI: RSDT CFF80000, 003C (r1 A_M_I_ OEMRSDT  10000730 MSFT       97)
(XEN) ACPI: FACP CFF80200, 0084 (r2 A_M_I_ OEMFACP  10000730 MSFT       97)
(XEN) ACPI: DSDT CFF805C0, 8E13 (r1  A0840 A0840001        1 INTL 20060113)
(XEN) ACPI: FACS CFF8E000, 0040
(XEN) ACPI: APIC CFF80390, 006C (r1 A_M_I_ OEMAPIC  10000730 MSFT       97)
(XEN) ACPI: MCFG CFF80400, 003C (r1 A_M_I_ OEMMCFG  10000730 MSFT       97)
(XEN) ACPI: OEMB CFF8E040, 0081 (r1 A_M_I_ AMI_OEM  10000730 MSFT       97)
(XEN) ACPI: HPET CFF893E0, 0038 (r1 A_M_I_ OEMHPET  10000730 MSFT       97)
(XEN) ACPI: OSFR CFF89420, 00B0 (r1 A_M_I_ OEMOSFR  10000730 MSFT       97)
(XEN) Xen heap: 14MB (14480kB)
(XEN) Domain heap initialised
(XEN) Processor #0 7:7 APIC version 20
(XEN) Processor #1 7:7 APIC version 20
(XEN) IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
(XEN) Enabling APIC mode:  Flat.  Using 1 I/O APICs
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Detected 3005.618 MHz processor.
(XEN) HVM: VMX enabled
(XEN) CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
(XEN) Booting processor 1/1 eip 8c000
(XEN) CPU1: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
(XEN) Total of 2 processors activated.
(XEN) ENABLING IO-APIC IRQs
(XEN)  -> Using new ACK method
(XEN) checking TSC synchronization across 2 CPUs: passed.
(XEN) Platform timer is 14.318MHz HPET
(XEN) Brought up 2 CPUs
(XEN) I/O virtualisation disabled
(XEN) *** LOADING DOMAIN 0 ***
(XEN)  Xen  kernel: 64-bit, lsb, compat32
(XEN)  Dom0 kernel: 64-bit, lsb, paddr 0xffffffff80200000 -> 0xffffffff805d87ec
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN)  Dom0 alloc.:   0000000226000000->0000000228000000 (2022123 pages to be allocated)
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN)  Loaded kernel: ffffffff80200000->ffffffff805d87ec
(XEN)  Init. ramdisk: ffffffff805d9000->ffffffff80d1fa00
(XEN)  Phys-Mach map: ffffffff80d20000->ffffffff81c9d758
(XEN)  Start info:    ffffffff81c9e000->ffffffff81c9e4a4
(XEN)  Page tables:   ffffffff81c9f000->ffffffff81cb2000
(XEN)  Boot stack:    ffffffff81cb2000->ffffffff81cb3000
(XEN)  TOTAL:         ffffffff80000000->ffffffff82000000
(XEN)  ENTRY ADDRESS: ffffffff80200000
(XEN) Dom0 has maximum 2 VCPUs
(XEN) Scrubbing Free RAM: .done.
(XEN) Xen trace buffers: disabled
(XEN) Std. Loglevel: Errors and warnings
(XEN) Guest Loglevel: Nothing (Rate-limited: Errors and warnings)
(XEN) Xen is relinquishing VGA console.
(XEN) *** Serial input -> DOM0 (type 'CTRL-a' three times to switch input to Xen)
(XEN) Freed 104kB init memory.
[root@ServerXen331 ~]# xm list -l UbuntuPVS810
(domain
    (domid 15)
    (on_crash restart)
    (uuid d9a1b362-c834-67ab-4e9d-d4b706699297)
    (bootloader_args )
    (vcpus 1)
    (name UbuntuPVS810)
    (on_poweroff destroy)
    (on_reboot restart)
    (bootloader /usr/bin/pygrub)
    (maxmem 4096)
    (memory 4096)
    (shadow_memory 0)
    (features )
    (on_xend_start ignore)
    (on_xend_stop ignore)
    (start_time 1230489041.67)
    (cpu_time 5.977945576)
    (online_vcpus 1)
    (image
        (linux
            (kernel )
            (notes
                (HV_START_LOW 18446603336221196288)
                (FEATURES '!writable_page_tables|pae_pgdir_above_4gb')
                (VIRT_BASE 18446744071562067968)
                (GUEST_VERSION 2.6)
                (PADDR_OFFSET 0)
                (GUEST_OS linux)
                (HYPERCALL_PAGE 18446744071564201984)
                (LOADER generic)
                (SUSPEND_CANCEL 1)
                (PAE_MODE yes)
                (ENTRY 18446744071569531392)
                (XEN_VERSION xen-3.0)
            )
        )
    )
    (status 2)
    (state -b----)
    (store_mfn 2216783)
    (console_mfn 2216782)
    (device
        (vif
            (bridge eth0)
            (mac 00:16:3e:1b:8b:d2)
            (script /etc/xen/scripts/vif-bridge)
            (uuid d33a8637-2937-049a-fd80-96251b572e1e)
            (backend 0)
        )
    )
    (device
        (vbd
            (protocol x86_64-abi)
            (uuid 8547bdfa-1368-25f3-96b4-6bcdfada031b)
            (dev xvda:disk)
            (uname phy:/dev/sdb7)
            (mode w)
            (backend 0)
            (bootable 1)
            (VDI )
        )
    )
    (device
        (console
            (protocol vt100)
            (location 2)
            (uuid 638eaa48-391c-45e6-0805-b4bb0410a3fc)
        )
    )
)

---


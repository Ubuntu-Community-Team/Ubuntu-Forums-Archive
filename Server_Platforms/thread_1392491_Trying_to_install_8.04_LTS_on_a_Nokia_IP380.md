---
title: "Trying to install 8.04 LTS on a Nokia IP380"
date: 2010-01-28
forum: Server Platforms
---

### Post by pierref on 2010-01-28
I will describe how I failed to install the Linux Turnkey WordPress appliance on a Nokia IP380 host, hoping that anybody could help me to get the job done. That appliance is running upon the Ubuntu 8.04 LTS system.
This describes a linear process, but in order to get that far, I had to try a lot of things that didn't work and didn't mention; the discovery of this linear process is the result of many iterations.
I failed near to the end, nut I hope that someone reading this can help me to get until the end. Please mail me at pf at openoffice dot org if you discover the ultimate trick.
**Used hardware**
[LIST]
[*]A Nokia IP 380 firewall running the native OS called IPSO
[*]A laptop running Ubuntu Karmic, having USB ports and a serial COM port
[*]An USB 2.0 to SATA/IDE converter, plugged into an USB port of my laptop
[*]A serial cable (null-modem)
[/LIST]
**Followed procedure**
I booted into IPSO and wrote down the MAC addresses of the eth[1-4] NICs:
[LIST]
[*]eth1: 00:a0:8e:78:c1:b4
[*]eth2: 00:a0:8e:78:c1:b5
[*]eth3: 00:a0:8e:78:c1:b6
[*]eth4: 00:a0:8e:78:c1:b7
[/LIST]
I installed the Linux Turnkey WordPress appliance into a virtual machine of VirtualBox, using a virtual hard disk of 2GB, named lamp.vdi. Because I didn't know how to change the default layout of the keybooard, I found it usefull to enter a root password that doesn't contain any letter of the following set: &#8220;a, q, z, w, m&#8221; whose position differ on the keyboards of several countries. I avoided also numbers and punctuation for the same reason. When the appliance will be running, it will still be possible to change these passwords into something stronger.
I converted the virtual disk into a raw disk image with the command (making sure that the target file lamp.img didn't exist yet, otherwise I had to remove it first):
```
VBoxManage clonehd --format RAW ~/.VirtualBox/HardDisks/lamp.vdi ~/Desktop/lamp.img
```
I plugged the hard disk of the IP380 into the USB port of my laptop with a very handy device called &#8220;USB 2.0 to SATA/IDE converter&#8221;. Depending on the presence of a CD-ROM disk, the disk showed up as /dev/sdb or /dev/sdc.
Obviously, the disk with the IPSO system was not able to be mounted, since Ubuntu doesn't support the IPSO file systems, as far as I know.
Copy the raw disk image on it with the command
```
sudo dd if=~/Desktop/lamp.img of=/dev/sdc
```
Attention: be absolutely sure you write onto the correct device, otherwise you will loose ALL the data on the device used as target with the option &#8220;of=<device>&#8221;!
I mounted the disk I just wrote. The easiest way is to plug out and plug in the USB adapter. Now the system could detect the newly written ext3 file system. I saw a file system appearing on /media/f8e48704-be17-465a-a295-5bed6d1b91d4. That string with hexadecimal numbers and hyphens f8e48704-be17-465a-a295-5bed6d1b91d4 is the UUID of the externally mounted disk. For making the references to this disk shorter, I gave the label exthd to that file system, which is located in the first partition of the disk drive:
```
sudo e2label /dev/sdc1 exthd
```
After this command, I unmounted and remounted the external disk drive. Starting from now, I can access that host disk through the path /media/exthd.
First, the GRUB loader needs to be adapted for loading from the serial console. I went to the root directory of the file system:
```
cd /media/exthd
```
I edited the file boot/grub/menu.lst by adding next two lines before any other command:
```
serial --unit=0 --speed=9600 --word=8 --parity=no --stop=1
terminal --timeout=10--dumb serial
```
I added an option to the kernel command line:
```
console=ttyS0,9600n8
```
Another useful option on the kernel line for avoiding a warning is
```
acpi=off
```
Finally, I also disabled the usb modules by adding to the options
```
nousb
```
so that the kernel line finally looked like:
```
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID= f8e48704-be17-465a-a295-5bed6d1b91d4 ro quiet console=ttyS0,9600n8 acpi=off nousb
```
where, remember, f8e48704-be17-465a-a295-5bed6d1b91d4 is the UUID specific to my disk drive. It will be something different on other systems.
I copied the boot/initrd.img-2.6.24-24-generic onto the Desktop directory my laptop for modifying it. That file is the image of a RAM filesystem compressed with gzip.
I had to extract the content of that image issuing:
```
cd ~/Desktop
mkdir initrd.dir
cd initrd.dir
gunzip < ../initrd.img-2.6.24-24-generic | cpio -i --make-directories
```
Now I am able to edit that part of the system.
First, I had to create the file etc/modprobe.conf where I put the following lines:
```
alias eth0 eepro100 
alias eth1 eepro100 
alias eth2 eepro100 
alias eth3 eepro100 
blacklist e100 	# we will use eepro100 instead
install eth0 /sbin/modprobe eepro100 
install eth1 /sbin/modprobe eepro100 
install eth2 /sbin/modprobe eepro100 
install eth3 /sbin/modprobe eepro100 
```
Next I had to modify one line out from the file etc/modprobe.d/blacklist, that one excluding the driver we just need, i.e. eepro100. So I found the line
```
blacklist eepro100
```
and commented it out by putting a # in front of it
```
#blacklist eepro100
```
The RAM file system doesn't contain the eepro100.ko module, so I had to copy it into the image
```
sudo cp /media/exthd/lib/modules/2.6.24-24-generic/kernel/drivers/net/eepro100.ko ~/Desktop/initrd.dir/lib/modules/2.6.24-24-generic/kernel/drivers/net

```Since the kernel option nousb doesn't seem to have worked, I decided to remove manually all the usb drivers with the command
```
rm -r lib/modules/2.6.24-24-generic/kernel/drivers/usb
```
Now I had to write the changes in initrd.dir back to the boot/initrd.img-2.6.24-24-generic file with the commands
```
cd ~/Desktop/initrd.dir
find . | cpio --create --format='newc' | gzip -c > ../initrd.img-2.6.24-24-generic
sudo cp ../initrd.img-2.6.24-24-generic /media/exthd/boot/initrd.img-2.6.24-24-generic
```
Since the system is booting up in two phases, first using the a subset of drivers from the RAM file system, and then the complete set of drivers from the whole file system, the same job has to be done for the second phase of the booting process.
Remove manually all the usb drivers
```
sudo rm -r /media/exthd/lib/modules/2.6.24-24-generic/kernel/drivers/usb/

```
Copy the file /etc/modprobe.conf
```
sudo cp ~/Desktop/initrd.dir/etc/modprobe.conf /media/exthd/etc/
```
Prevent eepro100 to be blacklisted in /etc/modprobe.d/blacklist by putting a &#8220;#&#8221; in front of the line containing &#8220;eepro100&#8221;, so it looks like:
```
#blacklist eepro100
```
I unmounted the external hard drive, plugged the USB/SATA adapter off, and put the disk drive into the IP380 host.
I connected the serial cable from the console serial port of the IP380 to my COM port, and started some utility like minicom or gtkterm.
When GRUB loads, you can enter into the GRUB menu by pressing ESC, allowing you to choose an entry.
I booted the Nokia IP380 first in recovery mode, this gives me the possibility to enter a root shell for checking everything is working fine. The asked password is the password given when installing the appliance into VirtualBox.
At that point, I get stuck. The eepro100 drivers load, but as I expected, the MAC addresses were set to ff:ff:ff:ff:ff:ff.
When I set the correct MAC addresses with the commands
```
ifconfig eth0 hw ether 00:a0:8e:78:c1:b4
ifconfig eth1 hw ether 00:a0:8e:78:c1:b5
ifconfig eth2 hw ether 00:a0:8e:78:c1:b6
ifconfig eth3 hw ether 00:a0:8e:78:c1:b7

```I am not able to get the network working, neither by asking a dynamic IP address from the DHCP server, nor by defining it static and adding the route manually with the following commands:
```
ifconfig eth0 hw ether 00:a0:8e:78:c1:b4 192.168.101.9 netmask 255.255.255.0 up
route add default gw 192.168.101.254 
```
The command &#8220;mii-tools eth0&#8221; returns &#8220;No MII transceiver present!&#8221;. Any clue?
Here is a complete log of the output of the booting sequence:
```
General Software Pentium III Embedded BIOS (tm) Version 4.3

Copyright (C) 2000 General Software, Inc.

Nokia NIC Trooper BIOS Version 1.1





00000640K Low Memory Passed

00000000K Ext Memory Passed

+-----------------------------------------------------------------------------+
|          System BIOS Configuration, (C) 2000 General Software, Inc.         |
+---------------------------------------+-------------------------------------+
| System CPU           : Pentium III    | Low Memory           : 637KB        |
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-24-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Sat Aug 22 01:06:14 UTC 2009 (Ubuntu 2.6.24-24.60-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65536
[    0.000000]   HighMem     65536 ->    65536
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65536
[    0.000000] DMI not present or invalid.
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 65024
[    0.000000] Kernel command line: root=UUID=f8e48704-be17-465a-a295-5bed6d1b91d4 ro single console=ttyS0,9600n8 acpi=off nousb
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 866.495 MHz processor.
[   27.750980] Console: colour dummy device 80x25
[   27.751014] console [ttyS0] enabled
[   29.841961] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.925498] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   30.028872] Memory: 248188k/262144k available (2181k kernel code, 13448k reserved, 1006k data, 368k init, 0k highmem)
[   30.155782] virtual kernel memory layout:
[   30.155785]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   30.155788]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.155792]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   30.155795]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[   30.155798]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   30.155801]       .data : 0xc0321578 - 0xc041cdc4   (1006 kB)
[   30.155804]       .text : 0xc0100000 - 0xc0321578   (2181 kB)
[   30.684555] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.781452] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   30.953016] Calibrating delay using timer specific routine.. 1734.18 BogoMIPS (lpj=3468365)
[   31.053057] Security Framework initialized
[   31.102071] SELinux:  Disabled at boot.
[   31.148013] AppArmor: AppArmor initialized
[   31.197038] Failure registering capabilities with primary security module.
[   31.279236] Mount-cache hash table entries: 512
[   31.333705] Initializing cgroup subsys ns
[   31.381685] Initializing cgroup subsys cpuacct
[   31.434815] CPU: L1 I cache: 16K, L1 D cache: 16K
[   31.491197] CPU: L2 cache: 256K
[   31.528710] CPU serial number disabled.
[   31.574555] Compat vDSO mapped to ffffe000.
[   31.624642] Checking 'hlt' instruction... OK.
[   31.690408] SMP alternatives: switching to UP code
[   31.750696] Freeing SMP alternatives: 11k freed
[   31.805177] Early unpacking initramfs... done
[   32.577137] CPU0: Intel Pentium III (Coppermine) stepping 0a
[   32.645147] SMP motherboard not detected.
[   32.693046] Local APIC not detected. Using dummy APIC emulation.
[   32.764956] Brought up 1 CPUs
[   32.801041] net_namespace: 64 bytes
[   32.842798] Booting paravirtualized kernel on bare hardware
[   32.910839] Time: 14:48:56  Date: 01/27/10
[   32.959948] NET: Registered protocol family 16
[   33.013616] EISA bus registered
[   33.051413] PCI: PCI BIOS revision 2.10 entry at 0xe7c3e, last bus=4
[   33.127380] PCI: Using configuration type 1
[   33.177452] Setting up standard PCI resources
[   33.231566] ACPI: Interpreter disabled.
[   33.277433] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.345225] pnp: PnP ACPI: disabled
[   33.386923] PnPBIOS: Scanning system for PnP BIOS support...
[   33.454771] PnPBIOS: PnP BIOS support was not detected.
[   33.517843] PCI: Probing PCI hardware
[   33.561706] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   33.561710] * this clock source is slow. If you are sure your timer does not have
[   33.561714] * this bug, please use "acpi_pm_good" to disable the workaround
[   33.820873] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   33.820877] * this clock source is slow. If you are sure your timer does not have
[   33.820881] * this bug, please use "acpi_pm_good" to disable the workaround
[   34.081168] PCI: Discovered peer bus 02
[   34.127764] PCI: Discovered peer bus 03
[   34.174044] PCI: Discovered peer bus 04
[   34.246787] NET: Registered protocol family 8
[   34.298907] NET: Registered protocol family 20
[   34.352172] AppArmor: AppArmor Filesystem Enabled
[   34.408423] Time: tsc clocksource has been installed.
[   34.469889] PCI: Bus 1, cardbus bridge: 0000:00:09.0
[   34.529282]   IO window: 00001000-000010ff
[   34.578321]   IO window: 00001400-000014ff
[   34.627257]   PREFETCH window: 20000000-23ffffff
[   34.682430]   MEM window: 24000000-27ffffff
[   34.732410] PCI: Bus 5, cardbus bridge: 0000:00:09.1
[   34.791739]   IO window: 00001800-000018ff
[   34.840683]   IO window: 00001c00-00001cff
[   34.889621]   PREFETCH window: 28000000-2bffffff
[   34.944800]   MEM window: 2c000000-2fffffff
[   34.994788] PCI: Enabling device 0000:00:09.0 (0000 -> 0003)
[   35.062528] PCI: No IRQ known for interrupt pin A of device 0000:00:09.0. Please try using pci=biosirq.
[   35.174863] PCI: Enabling device 0000:00:09.1 (0000 -> 0003)
[   35.242596] PCI: No IRQ known for interrupt pin B of device 0000:00:09.1. Please try using pci=biosirq.
[   35.354961] NET: Registered protocol family 2
[   35.446150] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   35.528883] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   35.613369] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   35.690581] TCP: Hash tables configured (established 8192 bind 8192)
[   35.766594] TCP reno registered
[   35.814063] checking if image is initramfs... it is
[   37.232325] Freeing initrd memory: 7050k freed
[   37.286846] audit: initializing netlink socket (disabled)
[   37.351455] audit(1264603734.993:1): initialized
[   37.411956] VFS: Disk quotas dquot_6.5.1
[   37.459495] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.538113] io scheduler noop registered
[   37.584985] io scheduler anticipatory registered
[   37.640256] io scheduler deadline registered
[   37.691298] io scheduler cfq registered (default)
[   37.747627] PCI: Firmware left 0000:02:03.0 e100 interrupts enabled, disabling
[   37.834029] PCI: Firmware left 0000:02:04.0 e100 interrupts enabled, disabling
[   37.920375] PCI: Firmware left 0000:02:05.0 e100 interrupts enabled, disabling
[   38.006716] PCI: Firmware left 0000:02:06.0 e100 interrupts enabled, disabling
[   38.093617] isapnp: Scanning for PnP cards...
[   38.479888] Clocksource tsc unstable (delta = 856010033 ns)
[   38.547835] Time: pit clocksource has been installed.
[   38.625650] isapnp: No Plug & Play device found
[   38.769758] Real Time Clock Driver v1.12ac
[   38.818988] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.911845] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.984211] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.058533] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.149338] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   39.242317] PNP: No PS/2 controller found. Probing ports directly.
[   39.318479] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.377913] serio: i8042 AUX port at 0x60,0x64 irq 12
[   39.451406] mice: PS/2 mouse device common for all mice
[   39.514183] EISA: Probing bus 0 at eisa.0
[   39.562208] Cannot allocate resource for EISA slot 1
[   39.621662] EISA: Detected 0 cards.
[   39.663392] cpuidle: using governor ladder
[   39.712433] cpuidle: using governor menu
[   39.759691] NET: Registered protocol family 1
[   39.811860] Using IPI No-Shortcut mode
[   39.856740] registered taskstats version 1
[   39.905959]   Magic number: 10:270:840
[   39.950945]   hash matches device ptyu6
[   39.996888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   40.068736] EDD information not available.
[   40.118341] Freeing unused kernel memory: 368k freed
[   40.177880] Write protecting the kernel read-only data: 802k
Loading, please wait...
Begin: Loading essential drivers... ...
[   40.689013] thermal: Unknown symbol acpi_processor_set_thermal_limit
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Waiting for root file system... ...
[   41.516201] SCSI subsystem initialized
[   41.600496] eepro100.c:v1.09j-t 9/29/99 Donald Becker
[   41.600503] eepro100.c: $Revision: 1.36 $ 2000/11/17 Modified by Andrey V. Savochkin <saw@saw.sw.com.sg> and others
[   41.830545] eth0: Invalid EEPROM checksum 0xff00, check settings before activating this device!
[   41.934643] eth0: OEM i82557/i82558 10/100 Ethernet, ff:ff:ff:ff:ff:ff, IRQ 11.
[   42.022109]   Board assembly ffffff-255, Physical connectors present: RJ45 BNC AUI MII
[   42.115207]   Primary interface chip unknown-15 PHY #31.
[   42.180976]     Secondary interface chip i82555.
[   42.236598]   General self-test: passed.
[   42.236601]   Serial sub-system self-test: passed.
[   42.236604]   Internal registers self-test: passed.
[   42.236607]   ROM checksum self-test: passed (0xdbd8681d).
[   42.493230] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   42.711351] tulip0:  EEPROM default media type 100baseTx.
[   42.775945] tulip0:  Index #0 - Media MII (#11) described by a 21142 MII PHY (3) block.
[   42.871744] tulip0:  Index #1 - Media 10baseT (#0) described by a 21142 Serial PHY (2) block.
[   42.983625] tulip0: ***WARNING***: No MII transceiver found!
[   43.097016] eth1: Invalid EEPROM checksum 0xff00, check settings before activating this device!
[   43.201140] eth1: OEM i82557/i82558 10/100 Ethernet, ff:ff:ff:ff:ff:ff, IRQ 11.
[   43.288611]   Board assembly ffffff-255, Physical connectors present: RJ45 BNC AUI MII
[   43.381711]   Primary interface chip unknown-15 PHY #31.
[   43.447483]     Secondary interface chip i82555.
[   43.503393]   General self-test: passed.
[   43.503396]   Serial sub-system self-test: passed.
[   43.503399]   Internal registers self-test: passed.
[   43.503402]   ROM checksum self-test: passed (0xdbd8681d).
[   43.764562] eth2: Digital DS21142/43 Tulip rev 65 at Port 0xdc00, EEPROM not present, 00:4c:69:6e:75:79, IRQ 10.
[   43.917136] tulip1:  EEPROM default media type 100baseTx.
[   43.981770] tulip1:  Index #0 - Media MII (#11) described by a 21142 MII PHY (3) block.
[   44.077567] tulip1:  Index #1 - Media 10baseT (#0) described by a 21142 Serial PHY (2) block.
[   44.189440] tulip1: ***WARNING***: No MII transceiver found!
[   44.303494] eth3: Invalid EEPROM checksum 0xff00, check settings before activating this device!
[   44.407583] eth3: OEM i82557/i82558 10/100 Ethernet, ff:ff:ff:ff:ff:ff, IRQ 11.
[   44.495057]   Board assembly ffffff-255, Physical connectors present: RJ45 BNC AUI MII
[   44.588359]   Primary interface chip unknown-15 PHY #31.
[   44.654129]     Secondary interface chip i82555.
[   44.710144]   General self-test: passed.
[   44.710147]   Serial sub-system self-test: passed.
[   44.710150]   Internal registers self-test: passed.
[   44.710153]   ROM checksum self-test: passed (0xdbd8681d).
[   44.972947] eth4: Digital DS21142/43 Tulip rev 65 at Port 0xd800, EEPROM not present, 00:4c:69:6e:75:7a, IRQ 10.
[   45.116916] tulip2:  EEPROM default media type 100baseTx.
[   45.181455] tulip2:  Index #0 - Media MII (#11) described by a 21142 MII PHY (3) block.
[   45.277256] tulip2:  Index #1 - Media 10baseT (#0) described by a 21142 Serial PHY (2) block.
[   45.389115] tulip2: ***WARNING***: No MII transceiver found!
[   45.502323] eth5: Invalid EEPROM checksum 0xff00, check settings before activating this device!
[   45.606438] eth5: OEM i82557/i82558 10/100 Ethernet, ff:ff:ff:ff:ff:ff, IRQ 11.
[   45.693909]   Board assembly ffffff-255, Physical connectors present: RJ45 BNC AUI MII
[   45.787007]   Primary interface chip unknown-15 PHY #31.
[   45.852776]     Secondary interface chip i82555.
[   45.908788]   General self-test: passed.
[   45.908791]   Serial sub-system self-test: passed.
[   45.908794]   Internal registers self-test: passed.
[   45.908797]   ROM checksum self-test: passed (0xdbd8681d).
[   46.172476] eth6: Digital DS21142/43 Tulip rev 65 at Port 0xcc00, EEPROM not present, 00:4c:69:6e:75:7b, IRQ 10.
[   46.325585] tulip3:  EEPROM default media type 100baseTx.
[   46.390180] tulip3:  Index #0 - Media MII (#11) described by a 21142 MII PHY (3) block.
[   46.485983] tulip3:  Index #1 - Media 10baseT (#0) described by a 21142 Serial PHY (2) block.
[   46.597859] tulip3: ***WARNING***: No MII transceiver found!
[   46.669791] scsi0 : pata_serverworks
[   46.714489] scsi1 : pata_serverworks
[   46.757397] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xf800 irq 14
[   46.839701] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xf808 irq 15
[   46.932931] eth7: Digital DS21142/43 Tulip rev 65 at Port 0xc800, EEPROM not present, 00:4c:69:6e:75:7c, IRQ 10.
[   47.206640] ata1.00: ATA-6: FUJITSU MHT2040AS, 006D, max UDMA/100
[   47.279527] ata1.00: 78140160 sectors, multi 16: LBA 
[   47.371194] ata1.00: configured for MWDMA2
[   47.585139] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2040A 006D PQ: 0 ANSI: 5
[   48.348915] Driver 'sd' needs updating - please use bus_type methods
[   48.426673] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   48.510084] sd 0:0:0:0: [sda] Write Protect is off
[   48.569075] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.678015] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   48.761351] sd 0:0:0:0: [sda] Write Protect is off
[   48.818728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.926927]  sda: sda1 sda2 < sda5 >
[   49.023511] sd 0:0:0:0: [sda] Attached SCSI disk
[   49.092044] sd 0:0:0:0: Attached scsi generic sg0 type 0
Done.
Begin: Running /scripts/local-premount ...
Done.
[   49.526034] kjournald starting.  Commit interval 5 seconds
[   49.591702] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
[ OK ]ting preliminary keymap...        
[ OK ]ting up resolvconf...        
 * Setting the system clock
[ OK ]rting basic networking...        
[ OK ]rting kernel event manager...        
 * Loading hardware drivers...        [   55.641024] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   55.792647] Yenta: CardBus bridge found at 0000:00:09.0 [0000:0000]
[   55.867639] Yenta: Enabling burst memory read transactions
[   55.933276] Yenta: Using CSCINT to route CSC interrupts to PCI
[   56.003098] Yenta: Routing CardBus interrupts to PCI
[   56.062533] Yenta TI: socket 0000:00:09.0, mfunc 0x00001000, devctl 0x66
[   56.142740] Yenta TI: socket 0000:00:09.0 no PCI interrupts. Fish. Please report.
[   56.232309] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   56.232313] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   56.413801] Linux agpgart interface v0.102
[   56.576345] Yenta: ISA IRQ mask 0x0000, PCI irq 0
[   56.632648] Socket status: 30000006
[   56.685885] agpgart: unable to determine aperture size.
[   56.748414] agpgart: agp_backend_initialize() failed.
[   56.808887] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22
[   56.893264] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[   56.965033] agpgart: unable to determine aperture size.
[   57.027603] agpgart: agp_backend_initialize() failed.
[   57.088076] agpgart-serverworks: probe of 0000:00:00.1 failed with error -22
[   57.172460] Yenta: CardBus bridge found at 0000:00:09.1 [0000:0000]
[   57.247465] Yenta: Using CSCINT to route CSC interrupts to PCI
[   57.317259] Yenta: Routing CardBus interrupts to PCI
[   57.376694] Yenta TI: socket 0000:00:09.1, mfunc 0x00001000, devctl 0x66
[   57.456913] Yenta TI: socket 0000:00:09.1 no PCI interrupts. Fish. Please report.
[   57.546472] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   57.546476] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   57.855515] Yenta: ISA IRQ mask 0x0000, PCI irq 0
[   57.911798] Socket status: 30000006
udhcpc[2455]: udhcpc (v0.9.9-pre) started
udhcpc[2464]: udhcpc (v0.9.9-pre) started
[   58.450720] NET: Registered protocol family 17
udhcpc[2455]: Sending discover...
udhcpc[2464]: Sending discover...
[ OK ]
 * Setting the system clockudhcpc[2455]: Sending discover...
udhcpc[2464]: Sending discover...
[ OK ]ding kernel modules...         * Loading manual drivers...        
[ OK ]ting kernel variables...        
[ OK ]ivating swap...        
 * Checking root file system...        fsck 1.40.8 (13-Mar-2008)
exthd: clean, 32308/121920 files, 149129/485958 blocks
[ OK ]
 * Checking file systems...        fsck 1.40.8 (13-Mar-2008)
[ OK ]
[ OK ]nting local filesystems...        
[ OK ]ivating swapfile swap...        
[ OK ]cking minimum space in /tmp...        
[ OK ]figuring network interfaces...        
 * Setting up console font and keymap...        udhcpc[2455]: Sending discover.
..
udhcpc[2464]: Sending discover...
[ OK ]
Give root password for maintenance
(or type Control-D to continue): udhcpc[2455]: No lease, failing.
udhcpc[2464]: No lease, failing.

```

At this point, I have a root shell:
```
root@wordpress:~# ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@wordpress:~# ifconfig eth0 192.168.101.9 up
SIOCSIFFLAGS: Invalid argument
SIOCSIFFLAGS: Invalid argument
rooot@wordpress:~# ifconfig eth0 hw ether 00:a0:8e:78:c1:b4 192.168.101.9 netmask 255.255.255.0 up                                                       
root@wordpress:~# ifconfig eth0                 
eth0      Link encap:Ethernet  HWaddr 00:a0:8e:78:c1:b4  
          inet addr:192.168.101.9  Bcast:192.168.101.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

```
I can't ping to numerical addresses on the same local network:
```
root@wordpress:~# ping 192.168.101.134                                  
PING 192.168.101.134 (192.168.101.134) 56(84) bytes of data.
From 192.168.101.9 icmp_seq=2 Destination Host Unreachable
From 192.168.101.9 icmp_seq=3 Destination Host Unreachable
From 192.168.101.9 icmp_seq=4 Destination Host Unreachable

--- 192.168.101.134 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4999ms, pipe 3
root@wordpress:~# route -n                                            
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
root@wordpress:~# route add default gw 192.168.101.254 
root@wordpress:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.101.254 0.0.0.0         UG    0      0        0 eth0
root@wordpress:~# ping 192.168.101.134
PING 192.168.101.134 (192.168.101.134) 56(84) bytes of data.
From 192.168.101.9 icmp_seq=1 Destination Host Unreachable
From 192.168.101.9 icmp_seq=2 Destination Host Unreachable
From 192.168.101.9 icmp_seq=3 Destination Host Unreachable

--- 192.168.101.134 ping statistics ---

5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4017ms, pipe 3
```
even after setting a correct route. The only thing that I can do is to ping to the machine itself, obviously:
```
root@wordpress:~# ping 192.168.101.9  

PING 192.168.101.9 (192.168.101.9) 56(84) bytes of data.
64 bytes from 192.168.101.9: icmp_seq=1 ttl=64 time=0.088 ms
64 bytes from 192.168.101.9: icmp_seq=2 ttl=64 time=0.038 ms
64 bytes from 192.168.101.9: icmp_seq=3 ttl=64 time=0.032 ms

--- 192.168.101.9 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.032/0.052/0.088/0.026 ms
root@wordpress:~# ping 192.168.101.254
PING 192.168.101.254 (192.168.101.254) 56(84) bytes of data.
From 192.168.101.9 icmp_seq=1 Destination Host Unreachable
From 192.168.101.9 icmp_seq=2 Destination Host Unreachable
From 192.168.101.9 icmp_seq=3 Destination Host Unreachab
--- 192.168.101.254 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3008ms, pipe 3                                                                
root@wordpress:~# halt

```If someone can get further, he is welcome, but I stop here.

---

### Post by pierref on 2010-01-30
I found several success stories about trying to do this. 

Perhaps the most relevant is this one: 

[LIST]
[http://forum.pfsense.org/index.php?action=printpage;topic=4595.0]("http://forum.pfsense.org/index.php?action=printpage;topic=4595.0")
[/LIST]

It is located on a pfsense forum, but it speaks also about installing Ubuntu 6.06.1 server on a Nokia IP330.

Installing FreeBSD seems also to be rather easy, but I didn't try yet. :p> 

---

### Post by pierref on 2010-06-26
> **nadeem1414 said:**
> how can i install the whole movies in one step in my [Nokia C1-02]("http://www.mobile-phone.pk/nokia_c1_02-2355/") ? and also guide me for further detailed of its selling way?

@nadeem1414: The Nokia C1-02 is a mobile phone. It has nothing to do with the IP380 router in this thread.

Anyway, the solution is to connect your computer to your mobile through Bluetooth or USB, to copy the file of the movie into the directory Videos of the card (normally on the D: device) and open this file from the video player.

---

### Post by dboxfutzi on 2012-11-17
Hi there,

I got three old Nokia IP350 with IPOS installed on them.
I like the idea of installing an Open- Source-linux-project- Firewall on it like IPCop or m0n0wall.
I got stuck on the same problems with the ethernet-ports.
Like you can see the System recognizes the 4x Intel 82551ER NIC Chips but says that the EEprom Checksum is incorrect, MAC adress is missing etc see the Code:

```

[   43.097016] eth1: Invalid EEPROM checksum 0xff00, check settings before activating this device! 
[   43.201140] eth1: OEM i82557/i82558 10/100 Ethernet, ff:ff:ff:ff:ff:ff, IRQ 11. 
[   43.288611]   Board assembly ffffff-255, Physical connectors present: RJ45 BNC AUI MII

[   44.303494] eth3: Invalid EEPROM checksum 0xff00, check settings before activating this device! 
[   44.407583] eth3: OEM i82557/i82558 10/100 Ethernet, ff:ff:ff:ff:ff:ff, IRQ 11. 
[   44.495057]   Board assembly ffffff-255, Physical connectors present: RJ45 BNC AUI MII

[   45.502323] eth5: Invalid EEPROM checksum 0xff00, check settings before activating this device! 
[   45.606438] eth5: OEM i82557/i82558 10/100 Ethernet, ff:ff:ff:ff:ff:ff, IRQ 11. 
[   45.693909]   Board assembly ffffff-255, Physical connectors present: RJ45 BNC AUI MII

```And I think the EEprom's are missing on IP350 / IP380!
See yourselve on the Mainboard right behind the NIC chips and the quartz you can see unsoldered SOIC- pads. The are marked as U28, U29, U30 and U39.

On the smaller models like IP110 / IP120 / IP130 you can fint the EEprom onboard but not properly programmed. 
So you have to programm them first with an Intel- Tool named EEupdate.exe or ERupdate.exe in DOS.
After that the Linux'll accept the NICs.

I found a Post about that:
[HTML]http://forum.m0n0.ch/index.php?PHPSESSID=mhufkbbeh0914n878e3a5v8sj0&/topic,1471.0.html[/HTML]

I think about ordering the missing EEproms (93LC46B) and solder them to the board.
In the technical documentation of the NIC's I found everything about the IC.
[HTML]http://www.intel.com/content/dam/doc/datasheet/82551er-fast-ethernet-pci-datasheet.pdf[/HTML]
The NIC'll automatically recognize the empty EEprom!
Then I should be able to program them like a IP110 etc.

Hope it'll work!

:guitar:

Greetings from germany :)

---

### Post by pierref on 2012-11-17
> **dboxfutzi said:**
> 
I think about ordering the missing EEproms (93LC46B) and solder them to the board.
In the technical documentation of the NIC's I found everything about the IC.
[HTML]http://www.intel.com/content/dam/doc/datasheet/82551er-fast-ethernet-pci-datasheet.pdf[/HTML]
The NIC'll automatically recognize the empty EEprom!
Then I should be able to program them like a IP110 etc.

Greetings from germany :)

I wish you good luck. I don't see myself tweaking at hardware level. Anyway: please, keep us informed. 

My solution was to install pfSense, see this forum: [http://forum.pfsense.org/index.php?topic=41618.0]("http://forum.pfsense.org/index.php?topic=41618.0")

---

### Post by dboxfutzi on 2012-11-28
Hi there,

i got the ICs and soldered them in.
After programming them by using the tool ERupdate the NICs now have their MACs stored.
Now I've problems installing any other System than IPSO...
All the Systems crashes at boot -> PFsense, IPCop, m0n0wall

need help!

Greetings

---

### Post by pierref on 2012-11-29
> **dboxfutzi said:**
> Hi there,

i got the ICs and soldered them in.
After programming them by using the tool ERupdate the NICs now have their MACs stored.
Now I've problems installing any other System than IPSO...
All the Systems crashes at boot -> PFsense, IPCop, m0n0wall

need help!

Greetings

Congratulations for reprogramming the NICs.

Probably you will be able to install Ubuntu Linux or Debian Linux. If this works, once installed you could try to run PFsense, IPCop, m0n0wall or whatever inside a virtual machine.

---

### Post by drwarner on 2012-11-30
People have reported successful installs of pfSense on Nokia IP380 hardware; it involved disabling USB support.

The IP350/380 will crash at USB detection if a normal FreeBSD kernel is booted, as seen in the dmesg output in [this thread ]("http://forum.m0n0.ch/index.php?topic=5826.0")on the m0n0wall forums.

Perhaps try installing a custom kernel without USB support?

I'd love to hear the result.
I've got an IP350, but I haven't replaced the drive in it yet... Once I have an opportunity to dig out my null-modem serial cable and tinker, I'll come back and report in.

-DW

---


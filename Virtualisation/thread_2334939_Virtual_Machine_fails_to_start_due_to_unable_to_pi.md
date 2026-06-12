---
title: "Virtual Machine fails to start due to unable to pin certain vCPUs"
date: 2016-08-24
forum: Virtualisation
---

### Post by whbbhw1024 on 2016-08-24
[COLOR=#00ff00]1&#12289;Issue:[/COLOR]
The virtual machine deployment always failed with the below error by KVM hypervisor.
The problem is with particular set of vPCUs NOT all vCPUs pin sets have the problem.
Someone meet this issue or can give me some advises?
[COLOR=#00ff00]
2&#12289;Background:[/COLOR]
 =========== 
 We have installed Ubuntu 14.04.4 LTS Kernel version 3.13.0-87-generic on the board as HostOS. 
 We use QEMU emulator version 2.2.0 (Debian 1:2.2+dfsg-5expubuntu9.7~cloud5) as the hypervisor. 
 We did not see any hardware related alarms from BSP. 
[COLOR=#00ff00]
3&#12289;Error information:[/COLOR]

{code} 
root@compute-0-10:/var/log/libvirt/qemu# cat instance-0000001b.log 
 2016-07-12 14:43:32.328+0000: starting up 
 LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name instance-0000001b -S -machine pc-i440fx-utopic,accel=kvm,usb=off -cpu host -m 1024 -realtime mlock=off -smp 4,sockets=2,cores=1,threads=2 -object memory-backend-file,prealloc=yes,mem-path=/mnt/huge_qemu_1G/libvirt/qemu,share=on,size=1024M,id=ram-node0,host-nodes=0,policy=bind -numa node,nodeid=0,cpus=0-3,memdev=ram-node0 -uuid 3d180b9c-1c9b-4895-a154-c47eefc0e6db -smbios type=1,manufacturer=OpenStack Foundation,product=OpenStack Nova,version=2015.1.0,serial=38383032-3736-3530-3032-433030303139,uuid=3d180b9c-1c9b-4895-a154-c47eefc0e6db -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/instance-0000001b.monitor,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=utc,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -boot strict=on -device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 -drive file=/var/lib/nova/instances/3d180b9c-1c9b-4895-a154-c47eefc0e6db/disk,if=none,id=drive-virtio-disk0,format=qcow2,cache=directsync -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x4,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -drive file=/var/lib/nova/instances/3d180b9c-1c9b-4895-a154-c47eefc0e6db/disk.config,if=none,id=drive-ide0-1-1,readonly=on,format=raw,cache=directsync -device ide-cd,bus=ide.1,unit=1,drive=drive-ide0-1-1,id=ide0-1-1 -chardev socket,id=charnet0,path=/run/openvswitch/vhostuser-6c4c4140-bfc -netdev type=vhost-user,id=hostnet0,chardev=charnet0 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=fa:16:3e:5a:af:49,bus=pci.0,addr=0x3 -chardev file,id=charserial0,path=/var/lib/nova/instances/3d180b9c-1c9b-4895-a154-c47eefc0e6db/console.log -device isa-serial,chardev=charserial0,id=serial0 -chardev pty,id=charserial1 -device isa-serial,chardev=charserial1,id=serial1 -device usb-tablet,id=input0 -vnc 192.168.2.32:3 -k en-us -device cirrus-vga,id=video0,bus=pci.0,addr=0x2 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x5 -msg timestamp=on 
 Domain id=8 is tainted: high-privileges 
 Domain id=8 is tainted: host-cpu 
 char device redirected to /dev/pts/14 (label charserial1) 
 2016-07-12T14:43:33.299826Z qemu-system-x86_64: -netdev type=vhost-user,id=hostnet0,chardev=charnet0: chardev "charnet0" went up 

 [COLOR=#ff0000]KVM internal error. Suberror: 3 
 extra data[0]: 800000fd 
 extra data[1]: 31 [/COLOR]
 RAX=ffffffff8100cb80 RBX=ffffffff81ce6e20 RCX=0100000000000000 RDX=0000000000000000 
 RSI=0000000000000000 RDI=0000000000000000 RBP=0000000000000000 RSP=ffffffff81c03ef0 
 R8 =0000000000000000 R9 =0000000000000000 R10=0000000000000000 R11=0000000000000000 
 R12=ffffffff81c00000 R13=0000000000000000 R14=00000000ffffffed R15=ffffffff81e83000 
 RIP=ffffffff81043a62 RFL=00000246 [---Z-P-] CPL=0 II=0 A20=1 SMM=0 HLT=0 
 ES =0000 0000000000000000 ffffffff 00c00000 
 CS =0010 0000000000000000 ffffffff 00a09b00 DPL=0 CS64 [-RA] 
 SS =0018 0000000000000000 ffffffff 00c09300 DPL=0 DS   [-WA] 
 DS =0000 0000000000000000 ffffffff 00c00000 
 FS =0000 0000000000000000 ffffffff 00c00000 


[COLOR=#00ff00]4&#12289;Other info:[/COLOR]
root@compute-0-10:~# lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                20
On-line CPU(s) list:   0-19
Thread(s) per core:    2
Core(s) per socket:    10
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 62
Stepping:              4
CPU MHz:               2401.000
BogoMIPS:              4799.76
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              25600K
NUMA node0 CPU(s):     0-19


root@compute-0-10:~# lspci
00:00.0 Host bridge: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 DMI2 (rev 04)
00:01.0 PCI bridge: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 1a (rev 04)
00:02.0 PCI bridge: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 2a (rev 04)
00:03.0 PCI bridge: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 3a (rev 04)
00:03.2 PCI bridge: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port 3c (rev 04)
00:05.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 VTd/Memory Map/Misc (rev 04)
00:05.2 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 IIO RAS (rev 04)
00:05.4 PIC: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 IOAPIC (rev 04)
00:1c.0 PCI bridge: Intel Corporation DH89xxCC PCI Express Root Port #1 (rev 08)
00:1c.1 PCI bridge: Intel Corporation DH89xxCC PCI Express Root Port #2 (rev 08)
00:1d.0 USB controller: Intel Corporation DH89xxCC USB2 Enhanced Host Controller #1 (rev 08)
00:1f.0 ISA bridge: Intel Corporation DH89xxCC LPC Controller (rev 08)
00:1f.2 SATA controller: Intel Corporation DH89xxCC 4 Port SATA AHCI Controller (rev 08)
00:1f.3 SMBus: Intel Corporation DH89xxCC SMBus Controller (rev 08)
00:1f.7 System peripheral: Intel Corporation DH89xxCC Watchdog Timer (rev 08)
01:00.0 Ethernet controller: Intel Corporation 82599 10 Gigabit Dual Port Backplane Connection (rev 01)
01:00.1 Ethernet controller: Intel Corporation 82599 10 Gigabit Dual Port Backplane Connection (rev 01)
02:00.0 Co-processor: Intel Corporation DH89XXCC Series QAT (rev 21)
02:00.1 Ethernet controller: Intel Corporation DH8900CC Series Gigabit Network Connection (rev 21)
02:00.2 Ethernet controller: Intel Corporation DH8900CC Series Gigabit Network Connection (rev 21)
02:00.3 Ethernet controller: Intel Corporation DH8900CC Series Gigabit Network Connection (rev 21)
02:00.4 Ethernet controller: Intel Corporation DH8900CC Series Gigabit Network Connection (rev 21)
03:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS2308 PCI-Express Fusion-MPT SAS-2 (rev 05)
04:00.0 Ethernet controller: Intel Corporation 82599 10 Gigabit Dual Port Backplane Connection (rev 01)
04:00.1 Ethernet controller: Intel Corporation 82599 10 Gigabit Dual Port Backplane Connection (rev 01)
06:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
ff:08.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Link 0 (rev 04)
ff:09.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Link 1 (rev 04)
ff:0a.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 0 (rev 04)
ff:0a.1 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 1 (rev 04)
ff:0a.2 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 2 (rev 04)
ff:0a.3 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Power Control Unit 3 (rev 04)
ff:0b.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 UBOX Registers (rev 04)
ff:0b.3 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 UBOX Registers (rev 04)
ff:0c.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0c.1 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0c.2 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0c.3 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0c.4 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0d.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0d.1 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0d.2 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0d.3 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0d.4 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Unicast Registers (rev 04)
ff:0e.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Home Agent 0 (rev 04)
ff:0e.1 Performance counters: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Home Agent 0 (rev 04)
ff:0f.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Target Address/Thermal Registers (rev 04)
ff:0f.1 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 RAS Registers (rev 04)
ff:0f.2 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
ff:0f.3 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
ff:0f.4 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
ff:0f.5 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 0 Channel Target Address Decoder Registers (rev 04)
ff:10.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 0 (rev 04)
ff:10.1 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 1 (rev 04)
ff:10.2 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 0 (rev 04)
ff:10.3 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 1 (rev 04)
ff:10.4 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 2 (rev 04)
ff:10.5 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 Thermal Control 3 (rev 04)
ff:10.6 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 2 (rev 04)
ff:10.7 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Integrated Memory Controller 1 Channel 0-3 ERROR Registers 3 (rev 04)
ff:13.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 R2PCIe (rev 04)
ff:13.1 Performance counters: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 R2PCIe (rev 04)
ff:13.4 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Ring Registers (rev 04)
ff:13.5 Performance counters: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 QPI Ring Performance Ring Monitoring (rev 04)
ff:16.0 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 System Address Decoder (rev 04)
ff:16.1 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Broadcast Registers (rev 04)
ff:16.2 System peripheral: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 Broadcast Registers (rev 04)

---


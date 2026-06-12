---
title: "GPU Passthrough getting &quot;Unable to determine the device handle for GPU....&quot; error"
date: 2016-12-08
forum: Virtualisation
---

### Post by kvasko on 2016-12-08
I am trying to do PCI Passthrough of a GTX 1080 and a GTX 980. I am successfully able to pass one of the units to the guest VM and it shows up with lspci (inside the guest).

Guest VM
[HTML]$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.2 USB controller: Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II] (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:02.0 VGA compatible controller: Cirrus Logic GD 5446
00:03.0 Ethernet controller: Red Hat, Inc Virtio network device
00:04.0 SCSI storage controller: Red Hat, Inc Virtio block device
00:05.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 980] (rev a1)
00:06.0 Unclassified device [00ff]: Red Hat, Inc Virtio memory balloon[/HTML]


I install the NVIDIA drivers (375.20) by doing the following:

[HTML]sudo apt-get update
sudo apt-get install linux-image-generic
sudo shutdown -r now
sudo apt-get install build-essential linux-source linux-headers-`uname -r` linux-image-extra-virtual
sudo ./NVIDIA-Linux-x86_64-375.20.run[/HTML]

this works and installs the drivers successfully. 

However when I run "nvidia-smi" and get the following error.

$nvidia-smi
Unable to determine the device handle for GPU 0000:05:00.0: Unknown Error


I found this thread [https://ubuntuforums.org/showthread.php?t=2333719&page=2](https://ubuntuforums.org/showthread.php?t=2333719&page=2) but he was getting the following error on the host and was apparently fixed by adding "video=efifb:off" to his grub on the host. However, I'm not getting this error on my host. 

[HTML][34060.617993] vfio-pci 0000:4e:00.0: BAR 3: can't reserve [mem 0x60000000-0x61ffffff 64bit pref][/HTML]


debugging information on host.

[HTML]$lspci -tv
....
 |           +-1f.0  Intel Corporation Xeon E7 v3/Xeon E5 v3/Core i7 VCU
 |           \-1f.2  Intel Corporation Xeon E7 v3/Xeon E5 v3/Core i7 VCU
 +-[0000:80]-+-02.0-[81]--+-00.0  NVIDIA Corporation Device 1b80
 |           |            \-00.1  NVIDIA Corporation Device 10f0
 |           +-03.0-[82]--+-00.0  NVIDIA Corporation GM204 [GeForce GTX 980]
 |           |            \-00.1  NVIDIA Corporation GM204 High Definition Audio Controller
 |           +-05.0  Intel Corporation Xeon E7 v3/Xeon E5 v3/Core i7 Address Map, VTd_Misc, System Management
 |           +-05.1  Intel Corporation Xeon E7 v3/Xeon E5 v3/Core i7 Hot Plug
 |           +-05.2  Intel Corporation Xeon E7 v3/Xeon E5 v3/Core i7 RAS, Control Status and Global Errors
....[/HTML]

[HTML]$lspci -vnnn 

81:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b80] (rev a1) (prog-if 00 [VGA controller])
81:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10f0] (rev a1)
82:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM204 [GeForce GTX 980] [10de:13c0] (rev a1) (prog-if 00 [VGA controller])
82:00.1 Audio device [0403]: NVIDIA Corporation GM204 High Definition Audio Controller [10de:0fbb] (rev a1)[/HTML]


[HTML]$lspci -vnnn -d 10de:

81:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b80] (rev a1) (prog-if 00 [VGA controller])
 Subsystem: Device [196e:119e]
 Physical Slot: 2
 Flags: fast devsel, IRQ 34
 Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
 Memory at e0000000 (64-bit, prefetchable) [size=256M]
 Memory at f0000000 (64-bit, prefetchable) [size=32M]
 I/O ports at f000 [size=128]
 Expansion ROM at fb000000 [disabled] [size=512K]
 Capabilities: [60] Power Management version 3
 Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
 Capabilities: [78] Express Legacy Endpoint, MSI 00
 Capabilities: [100] Virtual Channel
 Capabilities: [250] Latency Tolerance Reporting
 Capabilities: [128] Power Budgeting <?>
 Capabilities: [420] Advanced Error Reporting
 Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
 Capabilities: [900] #19
 Kernel driver in use: vfio-pci
81:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10f0] (rev a1)
 Subsystem: Device [196e:119e]
 Physical Slot: 2
 Flags: bus master, fast devsel, latency 0, IRQ 7
 Memory at fb080000 (32-bit, non-prefetchable) [size=16K]
 Capabilities: [60] Power Management version 3
 Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
 Capabilities: [78] Express Endpoint, MSI 00
 Capabilities: [100] Advanced Error Reporting
 Kernel driver in use: pci-stub
82:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM204 [GeForce GTX 980] [10de:13c0] (rev a1) (prog-if 00 [VGA controller])
 Subsystem: Device [196e:1116]
 Physical Slot: 4
 Flags: bus master, fast devsel, latency 0, IRQ 36
 Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
 Memory at c0000000 (64-bit, prefetchable) [size=256M]
 Memory at d0000000 (64-bit, prefetchable) [size=32M]
 I/O ports at e000 [size=128]
 Expansion ROM at f9000000 [disabled] [size=512K]
 Capabilities: [60] Power Management version 3
 Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
 Capabilities: [78] Express Legacy Endpoint, MSI 00
 Capabilities: [100] Virtual Channel
 Capabilities: [250] Latency Tolerance Reporting
 Capabilities: [258] L1 PM Substates
 Capabilities: [128] Power Budgeting <?>
 Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
 Capabilities: [900] #19
 Kernel driver in use: vfio-pci
82:00.1 Audio device [0403]: NVIDIA Corporation GM204 High Definition Audio Controller [10de:0fbb] (rev a1)
 Subsystem: Device [196e:1116]
 Physical Slot: 4
 Flags: bus master, fast devsel, latency 0, IRQ 7
 Memory at f9080000 (32-bit, non-prefetchable) [size=16K]
 Capabilities: [60] Power Management version 3
 Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
 Capabilities: [78] Express Endpoint, MSI 00
 Kernel driver in use: pci-stub[/HTML]


**guest VM **
[HTML]
$ nvidia-smi
Unable to determine the device handle for GPU 0000:00:05.0: Unknown Error[/HTML]

[HTML]$ dmesg
[   32.914603] nvidia 0000:00:05.0: irq 45 for MSI/MSI-X
[   32.920601] NVRM: RmInitAdapter failed! (0x23:0x56:451)
[   32.920612] NVRM: rm_init_adapter failed for device bearing minor number 0[/HTML]

[HTML]
$lspci -vnnn
00:05.0 VGA compatible controller [0300]: NVIDIA Corporation GM204 [GeForce GTX 980] [10de:13c0] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Device [196e:1116]
        Physical Slot: 5
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f2000000 (64-bit, prefetchable) [size=32M]
        I/O ports at c000 [size=128]
        Expansion ROM at fe000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Legacy Endpoint, MSI 00
        Kernel driver in use: nvidia[/HTML]

Some more debugging information.

On the guest VM.

[HTML]$ cat /proc/driver/nvidia/gpus/0000\:00\:05.0/information
Model:           GeForce GTX 980
IRQ:             11
GPU UUID:        GPU-????????-????-????-????-????????????
Video BIOS:      ??.??.??.??.??
Bus Type:        PCIe
DMA Size:        36 bits
DMA Mask:        0xfffffffff
Bus Location:    0000:00:05.0
Device Minor:    0[/HTML]



No idea where to debug from here. Any help would be appreciated.

---


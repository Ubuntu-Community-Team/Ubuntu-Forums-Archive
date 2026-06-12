---
title: "vfio_region_write failed: Device or resource busy"
date: 2017-10-13
forum: Virtualisation
---

### Post by mckay42 on 2017-10-13
Hi,

I have a problem getting gpu passthrough working. My hardware: CPU: Xeon E5 2695 v2, GPU to pass R9 390, host GPU GTX 550Ti, mainboard: ASUS Z9PA-D8.

vfio-pci seems to work:
```

03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii PRO [Radeon R9 290] [1002:67b1] (rev 80) (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited / Sapphire Technology Hawaii PRO [Radeon R9 290] [174b:e324]
    Flags: fast devsel, IRQ 27
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at e000 [size=256]
    Memory at f0800000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [200] #15
    Capabilities: [270] #19
    Capabilities: [2b0] Address Translation Service (ATS)
    Capabilities: [2c0] #13
    Capabilities: [2d0] #1b
    Kernel driver in use: vfio-pci
    Kernel modules: radeon, amdgpu


03:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio [1002:aac8]
    Subsystem: PC Partner Limited / Sapphire Technology Hawaii HDMI Audio [174b:aac8]
    Flags: fast devsel, IRQ 65
    Memory at f0860000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: vfio-pci
    Kernel modules: snd_hda_intel

```

also the iommu groups looks good:
```

#find /sys/kernel/iommu_groups/ -type l | grep 19
/sys/kernel/iommu_groups/19/devices/0000:03:00.1
/sys/kernel/iommu_groups/19/devices/0000:03:00.0

```

I also made a non shadowed copy of the rom because the R9 390 is my primary GPU.

but when I start the vm I get: 
```
qemu-system-x86_64: -device vfio-pci,host=03:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on,romfile=/usr/share/qemu/vbios.bin: VFIO 0000:03:00.0 BAR 0 mmap unsupported. Performance may be slow
```
and after bootloader when it tries to load windows I continuous getting:
```

...
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11da4, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11dab, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11daa, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11da9, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11da8, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11daf, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11dae, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11dad, 0x0,1) failed: Device or resource busy
qemu-system-x86_64: vfio_region_write(0000:03:00.0:region0+0x11dac, 0x0,1) failed: Device or resource busy
... and so on

```

I hope someone can give me a hint ;)


some additional info:

[LIST]
[*]Host: Ubuntu 16.04
[*]Guest: tested Win7 (x64) and Win10 (x64)
[*]Bios: tested with OVMF and Seabios
[/LIST]

qemu args: 
```

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=03:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on,romfile='/usr/share/qemu/vbios.bin' \
-device vfio-pci,host=03:00.1,bus=root.1,addr=00.1 \
-hda /dev/sdb \

```

---


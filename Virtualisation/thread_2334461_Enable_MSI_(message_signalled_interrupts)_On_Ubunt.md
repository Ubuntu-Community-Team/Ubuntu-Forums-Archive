---
title: "Enable MSI (message signalled interrupts) On Ubuntu 14.04 guest VM"
date: 2016-08-19
forum: Virtualisation
---

### Post by calerogers on 2016-08-19
Hi all,

I am trying to do some troubleshooting where virsh commands hang. After some googling some people had success by enabling MSI on their passthrough devices. I am attempting to do this though it doesn't seem to be working. According to the pre-check commands MSI is there and should be able to be enabled.

Here it says Enable- so that means it is currently disabled, but it has the capability of it since it is there:
```

lspci -v -s 0000:00:05.0
00:05.0 VGA compatible controller: NVIDIA Corporation Device 1b80 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8591
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at a2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    Memory at a0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    Expansion ROM at a3280000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: nvidia

```

And I can see it here as a param for the nvidia kernel module:
```


modinfo nvidia
filename:       /lib/modules/3.13.0-93-generic/kernel/drivers/video/nvidia.ko
alias:          char-major-195-*
version:        367.35
supported:      external
license:        NVIDIA
srcversion:     1053697037498B3A9EC97E0
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.13.0-93-generic SMP mod_unload modversions 
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_CheckPCIConfigSpace:int
parm:           NVreg_EnablePCIeGen3:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_TCEBypassMode:int
parm:           NVreg_MemoryPoolSize:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_AssignGpus:charp

```

Currently I have attempted to enable it by adding options nvidia NVreg_EnableMSI=1 to both /etc/modules and /etc/modprobe.d/nvidia.conf (file I had to create). I have also tried running:
```

sudo modprobe nvidia NVreg_enableMSI=1

```
and
```

echo 1 | sudo tee /sys/bus/pci/devices/$mydevice/msi_bus

```

However, after each method (and subsequent reboot) running the lspci -v -s command it says Enable-.

Any tips or help would be appreciated.

Thanks

---

### Post by KillerKelvUK on 2016-08-19
Hi again :-)

Are those commands and output from the guest or the host?

---

### Post by calerogers on 2016-08-19
Hi there :)

They are from the guest. Sorry if that wasn't clear.

---

### Post by KillerKelvUK on 2016-08-19
What was the contents of the file you placed under /etc/modprobe.d/? And did you run an 'update-initramfs -u' after creating it?

Please can you also post back the output of 'cat /proc/interrupts' from the host _once the guest has completed booting_?

---


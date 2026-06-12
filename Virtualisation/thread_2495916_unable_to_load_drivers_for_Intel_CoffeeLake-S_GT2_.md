---
title: "unable to load drivers for Intel CoffeeLake-S GT2 [UHD Graphics 630] [8086:3e92]"
date: 2024-03-07
forum: Virtualisation
---

### Post by fahadshery on 2024-03-07
I am using proxmox and I can confirm that the iGPU is in it's own IOMMU group "alone".
I have an ubuntu minimal cloud image:
```
cat /etc/os-release && uname -r

PRETTY_NAME="Ubuntu 22.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.4 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
5.15.0-1051-kvm
```

I can see the iGPU within the Ubuntu VM:
```
GPU_List=$(sudo lspci | awk '/VGA|Display|3D/ {print $1}');for GPU_ID in ${GPU_List[@]};do sudo lspci -s $GPU_ID -vnn; done

01:00.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company CometLake-S GT2 [UHD Graphics 630] [103c:8591]
        Physical Slot: 0
        Flags: fast devsel, IRQ 10
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5000 [size=64]
        Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: [40] Vendor Specific Information: Len=0c <?>
        Capabilities: [70] Express Endpoint, MSI 00
        Capabilities: [ac] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2

```

but there are no drivers loaded within the VM?? 
I have been trying to follow [this post]("https://ubuntuforums.org/showthread.php?t=2491146") but I can't see any drivers being loaded at all.

here is some more info:

```
inxi -G &&  sudo dmesg | grep -i i915Graphics:
  Device-1: Intel CoffeeLake-S GT2 [UHD Graphics 630] driver: N/A
  Display: server: No display server data found. Headless machine? tty: 178x51
  Message: GL data unavailable in console. Try -G --display
``` 

```
sudo lspci -nnv | grep -i -e 'Intel' | grep -A 11 -e 'VGA' | grep -i -e 'VGA\|Kernel driver\|Kernel modules'
01:00.0 VGA compatible controller [0300]: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630] [8086:3e92] (prog-if 00 [VGA controller])
```

Any pointers/help would be highly appreciated by this first timer :)

---

### Post by deadflowr on 2024-03-07
*Thread moved to **Virtualization***

---

### Post by MAFoElffen on 2024-03-10
You probably recognize me from the thread you linked to above...

On both your host and Vm Guest, please post this
```

sudo lspci -vnnn | grep -A3 -E 'VGA|Display|3D'

```
I'm looking for vfio as driver for the host on the Intel iGPU...

That would be changed to that module as the driver for the host iGPU, after you blacklist the i915 driver and tell it to load the vfio module for it's Device ID instead. That is the next step after turning on IOMMU and separating out the IOMMU Groups, right? Then that will show up for the VM Guests... But with normal drivers, can only be used by one VM Guest at a time.

Another, more advanced way is to remove/load modules in the "hooks" scripts for the VM Guest.

---


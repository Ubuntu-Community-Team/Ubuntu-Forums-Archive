---
title: "Host Card on GPU passthrough seems to hang"
date: 2020-04-04
forum: Virtualisation
---

### Post by irwebb on 2020-04-04
This is my first post, hopefully not my last.  I'm having a problem getting GPU/PCI passthrough working correctly on my system.  The main problem is I go through the set up and configuration changes and the Guest card seems to be reserved as expected (no video signal) and the Host card seems to hang.  The monitor seems to want to work, it acknowledges a signal (won't go to sleep) but nothing is displayed.

I've used Linux/BSD for years in my job, but I haven't tried to set up a system at home in nearly 20 years.  I always seem to gravitate to the Windows image on dual-boot systems (mostly for gaming) and end up wanting the space for that.  So those never last.  I want to get into practicing coding/scripting more and I hate doing that on Windows so when someone suggested running a VM host at home it seemed like a great solution.  I especially liked the idea of running it on an Ubuntu host.  So I'd really like to get this figured out.  If not, I'm probably going to go to a Windows system and just run VirtualBox on it.  Honestly, I'd rather not do that considering some of the expense I went to to build this system.  Any help is appreciated.  Right now the guest card is disconnected so the host card can work, so that limits some of the information I can give you.

The System:

CPU:     AMD Ryzen 7 3700
MB:       MSI MPG X570 Gaming Edge WiFi
NVMe:  Samsung SSD 970 EVO 1TB
Guest:   XFX Radeon RX580
Host:     XFX Radeon RX550
RAM:    32GB

Host System:
Linux version 5.3.0-45-generic (buildd@lcy01-amd64-027) (gcc version 7.5.0 (Ubuntu 7.5.0-3ubuntu1~18.04)) #37~18.04.1-Ubuntu SMP Fri Mar 27 15:58:10 UTC 2020

I read through a few different tutorials. And followed 3 different ones with varying results.  Here are the various files that have been added/edited.

cat /etc/modprobe.d/vfio_pci.conf
options vfio_pci ids=1002:67df,1002:aaf0

cat /etc/modprobe.d/amd64gpu.conf
softdep amdgpu pre: vfio vfio_pci

cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
vfio
vfio_iommu_type1
vfio_pci ids=1002:67df,1002:aaf0

cat /etc/initramfs-tools/modules
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
softdep amdgpu pre: vfio vfio_pci


vfio
vfio_iommu_type1
vfio_virqfd
vfio_pci ids=1002:67df,1002:aaf0
amdgpu

cat /etc/default/grub
***Edited output****
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on iommu=pt"

---


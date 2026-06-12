---
title: "PCI Passthrough to Paravirtualized Ubuntu 12.04 Guest on XenServer 6.1"
date: 2013-12-24
forum: Virtualisation
---

### Post by jpthompson23 on 2013-12-24
Hi, I'm trying to pass a CUDA GPU through to a paravirtualized Ubuntu 12.04 DomU guest on XenServer 6.1.
I already got this working when the guest is HVM, but I would like to use PV to test VM-to-VM data transfer bandwidth in PV mode.
I think the problem might be with the kernel I'm using in the PV guest.

I can do `lspci` and I get:
```
00:00.0 3D controller: NVIDIA Corporation GK104GL [Tesla K10] (rev a1)
```

But when I do `sudo nvidia-smi` I get:
```
[ 1282.314459] nvidia 0000:00:00.0: device not available (can't reserve [mem 0xd0000000-0xd0ffffff])
[ 1282.314543] pci 0000:00:00.0: device not available (can't reserve [mem 0xd0000000-0xd0ffffff])
FATAL: Error inserting nvidia_319 (/lib/modules/3.8.0-34-generic/updates/dkms/nvidia_319.ko): No such device
NVIDIA: failed to load the NVIDIA kernel module.
NVIDIA-SMI has failed because it couldn't communicate with NVIDIA driver. Make sure that latest NVIDIA driver is installed and running.

```

Here's what I get when I do `grep XEN /boot/config-3.8.0-34-generic`
```
CONFIG_XEN=y
CONFIG_XEN_DOM0=y
CONFIG_XEN_PRIVILEGED_GUEST=y
CONFIG_XEN_PVHVM=y
CONFIG_XEN_MAX_DOMAIN_MEMORY=500
CONFIG_XEN_SAVE_RESTORE=y
# CONFIG_XEN_DEBUG_FS is not set
CONFIG_PCI_XEN=y
CONFIG_XEN_PCIDEV_FRONTEND=m
CONFIG_XEN_BLKDEV_FRONTEND=y
CONFIG_XEN_BLKDEV_BACKEND=m
CONFIG_NETXEN_NIC=m
CONFIG_XEN_NETDEV_FRONTEND=y
CONFIG_XEN_NETDEV_BACKEND=m
CONFIG_INPUT_XEN_KBDDEV_FRONTEND=m
CONFIG_HVC_XEN=y
CONFIG_HVC_XEN_FRONTEND=y
CONFIG_XEN_WDT=m
CONFIG_XEN_FBDEV_FRONTEND=m
CONFIG_XEN_BALLOON=y
CONFIG_XEN_SELFBALLOONING=y
CONFIG_XEN_BALLOON_MEMORY_HOTPLUG=y
CONFIG_XEN_SCRUB_PAGES=y
CONFIG_XEN_DEV_EVTCHN=m
CONFIG_XEN_BACKEND=y
CONFIG_XENFS=m
CONFIG_XEN_COMPAT_XENFS=y
CONFIG_XEN_SYS_HYPERVISOR=y
CONFIG_XEN_XENBUS_FRONTEND=y
CONFIG_XEN_GNTDEV=m
CONFIG_XEN_GRANT_DEV_ALLOC=m
CONFIG_SWIOTLB_XEN=y
CONFIG_XEN_TMEM=y
CONFIG_XEN_PCIDEV_BACKEND=m
CONFIG_XEN_PRIVCMD=m
CONFIG_XEN_ACPI_PROCESSOR=y
CONFIG_XEN_MCE_LOG=y
CONFIG_XEN_HAVE_PVMMU=y

```

Is the problem that my config says `CONFIG_XEN_PCIDEV_FRONTEND=m` instead of `CONFIG_XEN_PCIDEV_FRONTEND=y`?
What does "m" mean, module?  Do I not have the correct module installed?

---


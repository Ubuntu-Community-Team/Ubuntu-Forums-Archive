---
title: "Ubuntu only boots when iommu=soft"
date: 2019-03-24
forum: Virtualisation
---

### Post by mglolenstine on 2019-03-24
Ok, so I've been battling with this problem for few weeks now. I'm trying to set up a KVM, but I'm unable to passthrough a gpu, as my IOMMU doesn't work on any other option than `soft`.

I'm currently rocking:

- fx-8320E

- GA-970A-DS3P

- RX-480 4GB

and I've been having a problem with the IOMMU boot.

So, if I try to boot with anything other than the `soft` mode on `iommu` in grub, I get stuck on booting, no matter what the `amd_iommu` setting is set to. `iommu=off` works fine, but no usb devices are recognised.

Also, I've checked the BIOS and I have enabled SVM and IOMMU for my cpu, and both CPU and the MB support AMD-Vi

If I run `dmesg | grep iommu -i` I get this output:

    ```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-16-generic root=UUID=087205d6-21bf-4c57-87d6-3621a0f04b6c ro iommu=soft
    [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-16-generic root=UUID=087205d6-21bf-4c57-87d6-3621a0f04b6c ro iommu=soft
    [    5.003506] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
    [    5.003507] AMD IOMMUv2 functionality not available on this system
```

I'm assuming that it's saying that functionality is not available because I'm not running the motherboard iommu, but the software one.

So, I'd like to know if there's anything else I can try or check to fix this "problem" and maybe get a Windows VM running with GPU passthrough.

Thanks in advance.

When running `virt-host-validate` I receive this output:

      ```
QEMU: Checking for hardware virtualization                                 : PASS
      QEMU: Checking if device /dev/kvm exists                                   : PASS
      QEMU: Checking if device /dev/kvm is accessible                            : PASS
      QEMU: Checking if device /dev/vhost-net exists                             : PASS
      QEMU: Checking if device /dev/net/tun exists                               : PASS
      QEMU: Checking for cgroup 'memory' controller support                      : PASS
      QEMU: Checking for cgroup 'memory' controller mount-point                  : PASS
      QEMU: Checking for cgroup 'cpu' controller support                         : PASS
      QEMU: Checking for cgroup 'cpu' controller mount-point                     : PASS
      QEMU: Checking for cgroup 'cpuacct' controller support                     : PASS
      QEMU: Checking for cgroup 'cpuacct' controller mount-point                 : PASS
      QEMU: Checking for cgroup 'cpuset' controller support                      : PASS
      QEMU: Checking for cgroup 'cpuset' controller mount-point                  : PASS
      QEMU: Checking for cgroup 'devices' controller support                     : PASS
      QEMU: Checking for cgroup 'devices' controller mount-point                 : PASS
      QEMU: Checking for cgroup 'blkio' controller support                       : PASS
      QEMU: Checking for cgroup 'blkio' controller mount-point                   : PASS
      QEMU: Checking for device assignment IOMMU support                         : PASS
      QEMU: Checking if IOMMU is enabled by kernel                               : WARN (IOMMU appears to be disabled in kernel. Add iommu=pt iommu=1 to kernel cmdline arguments)
       LXC: Checking for Linux >= 2.6.26                                         : PASS
       LXC: Checking for namespace ipc                                           : PASS
       LXC: Checking for namespace mnt                                           : PASS
       LXC: Checking for namespace pid                                           : PASS
       LXC: Checking for namespace uts                                           : PASS
       LXC: Checking for namespace net                                           : PASS
       LXC: Checking for namespace user                                          : PASS
       LXC: Checking for cgroup 'memory' controller support                      : PASS
       LXC: Checking for cgroup 'memory' controller mount-point                  : PASS
       LXC: Checking for cgroup 'cpu' controller support                         : PASS
       LXC: Checking for cgroup 'cpu' controller mount-point                     : PASS
       LXC: Checking for cgroup 'cpuacct' controller support                     : PASS
       LXC: Checking for cgroup 'cpuacct' controller mount-point                 : PASS
       LXC: Checking for cgroup 'cpuset' controller support                      : PASS
       LXC: Checking for cgroup 'cpuset' controller mount-point                  : PASS
       LXC: Checking for cgroup 'devices' controller support                     : PASS
       LXC: Checking for cgroup 'devices' controller mount-point                 : PASS
       LXC: Checking for cgroup 'blkio' controller support                       : PASS
       LXC: Checking for cgroup 'blkio' controller mount-point                   : PASS
       LXC: Checking if device /sys/fs/fuse/connections exists                   : PASS
```

and the problem is that the `iommu=pt iommu=1` don't work for me, as they don't seem to boot.

---


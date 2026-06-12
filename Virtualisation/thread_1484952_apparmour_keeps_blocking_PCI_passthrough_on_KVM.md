---
title: "apparmour keeps blocking PCI passthrough on KVM"
date: 2010-05-16
forum: Virtualisation
---

### Post by RoboJ1M on 2010-05-16
Hi,

I believe this is in relation to [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/545795](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/545795)

It's going to get fixed (hopefully) but in the mean time i can't pass through PCI cards to my guests.

I'm running 10.04 server x64 on both host and guest.

In /etc/libvirt/qemu/abstractions/libvirt-qemu I've added:

 ```
 /sys/bus/usb/devices/ r,
  /sys/bus/usb/devices/** r,
  /sys/devices/**/usb[0-9]*/** r,
  /sys/bus/pci/devices/ r,
  /sys/bus/pci/devices/** r,
  /sys/devices/pci/** r,

  /dev/shm/ r,
  /dev/shm/pulse-shm* r,
  /dev/shm/pulse-shm* rwk,
  /dev/snd/* rw,
  /dev/bus/usb/** rw,
  /dev/** rwk,
```

In virt-aa-helper I added

```
/sys/devices/** r,
```

I'm still getting this in the start up log and syslog:

```
device: 03:06.0: driver="pci-assign" host="03:06.0"
device: 03:06.1: driver="pci-assign" host="03:06.1"
device: 03:06.2: driver="pci-assign" host="03:06.2"
get_real_device: /sys/bus/pci/devices/0000:03:06.0/config: Permission denied
pci-assign: Error: Couldn't get real device (03:06.0)!
Error initializing device pci-assign

```
```
May 10 23:14:25 hal kernel: [ 179.037233] type=1503 audit(1273529665.107:22): operation="open" pid=1601 parent=1 profile="libvirt-28b82cfd-52c0-b743-475e-77dde3933f44" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/pci0000:00/0000:00:14.4/0000:03:06.0/vendor"
```

I don't know what template file is used to create *libvirt-28b82cfd-52c0-b743-475e-77dde3933f44*

Can anybody help me please?

Thanks,

James.

---

### Post by RoboJ1M on 2010-05-18
Serious? Nobody?
Nobody knows how apparmour works?

---

### Post by daudag on 2010-06-18
Hi,

have you found a solution?

Kind Regards
Hans

---

### Post by RoboJ1M on 2010-08-14
Yes, I did.

I hadn't added the correct permissions to one or both of the apparmour files.

Here are the contents of my working files.

usr.lib.libvirt.virt-aa-helper
```
# Last Modified: Mon Jul  06 17:22:37 2009
#include <tunables/global>

/usr/lib/libvirt/virt-aa-helper {
  #include <abstractions/base>

  # needed for searching directories
  capability dac_override,
  capability dac_read_search,

  # needed for when disk is on a network filesystem
  network inet,

  deny @{PROC}/[0-9]*/mounts r,
  @{PROC}/filesystems r,

  /usr/lib/libvirt/virt-aa-helper mr,
  /sbin/apparmor_parser Ux,

  /etc/apparmor.d/libvirt/* r,
  /etc/apparmor.d/libvirt/libvirt-[0-9a-f]*-[0-9a-f]*-[0-9a-f]*-[0-9a-f]*-[0-9a-f]* rw,

  /sys/bus/usb/devices/ r,
  /sys/bus/usb/devices/** r,
  /sys/devices/** r,

  /var/lib/libvirt/images/ rw,
  /var/lib/libvirt/images/** rw,
}

```

/etc/apparmor.d/abstractions/libvirt-qemu 
```

  #/sys/bus/usb/devices/ r,
  #/sys/devices/*/*/usb[0-9]*/** r,
  #/sys/devices/*/*/*/usb[0-9]*/** r,

  /sys/bus/usb/devices/ r,
  /sys/bus/usb/devices/** r,
  /sys/devices/**/usb[0-9]*/** r,
  /sys/bus/pci/devices/ r,
  /sys/bus/pci/devices/** r,
  /sys/devices/pci*/** rw,

  # WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /dev/shm/ r,
  /dev/shm/pulse-shm* r,
  /dev/shm/pulse-shm* rwk,
  /dev/snd/* rw,
  /dev/bus/usb/** rw,
  /dev/** rwk,
  capability ipc_lock,
  # 'kill' is not required for sound and is a security risk. Do not enable
  # unless you absolutely need it.
  deny capability kill,


```

Basically I just didn't quite match up the match pattern for PCI devices to the paths in /dev/*etc/etc/etc*

I warn you though, after all that I found that you can't use libvirt to do PCI device virtualization without an IOMMU on your motherboard.

AMD call it an IOMMU or AMD-Vi
Intel call it VTd.

It's is NOT the same at the VT in your CPU, that it for CPU virtualization only.

The only boards with them on are Intel ones and AMD 890FX boards.

See our thread here for more info on what AMD boards to choose:

[http://forums.tweaktown.com/gigabyte/39801-ga-890fxa-ud5-iommu-bios-switch.html]("http://forums.tweaktown.com/gigabyte/39801-ga-890fxa-ud5-iommu-bios-switch.html")

I got a confirmation from Gigabyte that IOMMU support is in the F4 release of the BIOS for their 890FX board with the model number ending in "UD5" (I forget the rest, but it's not hard to find)

Good luck, I'm saving for an 890FX boards and IOMMU goodness.

Regards,

J1M.

---

### Post by nutznboltz on 2011-03-03
> **RoboJ1M said:**
> The only boards with them on are Intel ones and AMD 890FX boards.

In Documentation/x86/x86_64/boot_options.txt the following statements exist which cast doubt on your "890FX board only" statement.
> ```
IOMMU (input/output memory management unit)

 Currently four x86-64 PCI-DMA mapping implementations exist:

   1. <arch/x86_64/kernel/pci-nommu.c>: use no hardware/software IOMMU at all
      (e.g. because you have < 3 GB memory).
      Kernel boot message: "PCI-DMA: Disabling IOMMU"

   2. <arch/x86_64/kernel/pci-gart.c>: AMD GART based hardware IOMMU.
      Kernel boot message: "PCI-DMA: using GART IOMMU"

   3. <arch/x86_64/kernel/pci-swiotlb.c> : Software IOMMU implementation. Used
      e.g. if there is no hardware IOMMU in the system and it is need because
      you have >3GB memory or told the kernel to us it (iommu=soft))
      Kernel boot message: "PCI-DMA: Using software bounce buffering
      for IO (SWIOTLB)"

   4. <arch/x86_64/pci-calgary.c> : IBM Calgary hardware IOMMU. Used in IBM
      pSeries and xSeries servers. This hardware IOMMU supports DMA address
      mapping with memory protection, etc.
      Kernel boot message: "PCI-DMA: Using Calgary IOMMU"
```

Wikipedia supports the notition that the xSeries is AMD Opteron based
[http://en.wikipedia.org/wiki/IBM_System_x#IBM_eServer_xSeries](http://en.wikipedia.org/wiki/IBM_System_x#IBM_eServer_xSeries)
> Previously IBM servers based on AMD Opteron CPUs did not share the xSeries brand. Instead they fell directly under the eServer umbrella, however, AMD Opteron-based servers now fall under the System x brand.
Where "xSeries" in boot_options.txt is now re-branded as "System X", therefore the mysterious xSeries is likely an AMD Opteron with a non 890FX IOMMU.

Also *The Price of Safety: Evaluating IOMMU Performance* 
[http://www.kernel.org/doc/ols/2007/ols2007v1-pages-9-20.pdf](http://www.kernel.org/doc/ols/2007/ols2007v1-pages-9-20.pdf)
Search for "Calgary" and you will see "System X" "X86-64".

---


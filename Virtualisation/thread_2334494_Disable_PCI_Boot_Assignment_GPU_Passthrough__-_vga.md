---
title: "Disable PCI Boot Assignment GPU Passthrough  - vgaarb: setting as boot device"
date: 2016-08-19
forum: Virtualisation
---

### Post by bluedragon1460 on 2016-08-19
I'm wondering how you disable VGA Arbitration from setting the last PCI slot as a boot device. It seems which ever card is assigned as a boot device is passing through GPU, but when I run nvidia-smi is says "No devices found". I've removed cards in a decremental fashion, and there is always an issue with the last one in the vgaarb assignment, but all the other cards work fine. Any ideas?

Using Ubuntu 16.04 Server Edition


```
[    8.397853] vgaarb: device added: PCI:0000:4b:00.0,decodes=io+mem,owns=none,locks=none
[    8.397858] vgaarb: device added: PCI:0000:4c:00.0,decodes=io+mem,owns=none,locks=none
[    8.397862] vgaarb: device added: PCI:0000:4d:00.0,decodes=io+mem,owns=none,locks=none
[    8.397867] vgaarb: setting as boot device: PCI:0000:4e:00.0
[    8.397869] vgaarb: device added: PCI:0000:4e:00.0,decodes=io+mem,owns=io+mem,locks=none
[    8.397872] vgaarb: loaded
[    8.397873] vgaarb: bridge control possible 0000:4e:00.0
[    8.397875] vgaarb: bridge control possible 0000:4d:00.0
[    8.397877] vgaarb: bridge control possible 0000:4c:00.0
[    8.397879] vgaarb: bridge control possible 0000:4b:00.0
[   12.040509] snd_hda_intel 0000:4b:00.1: Handle vga_switcheroo audio client
[   12.040627] snd_hda_intel 0000:4c:00.1: Handle vga_switcheroo audio client
[   12.041524] snd_hda_intel 0000:4d:00.1: Handle vga_switcheroo audio client
[   12.042228] snd_hda_intel 0000:4e:00.1: Handle vga_switcheroo audio client
[  101.386334] vgaarb: device changed decodes: PCI:0000:4b:00.0,olddecodes=io+mem,decodes=io+mem:owns=none
[  101.399582] vgaarb: device changed decodes: PCI:0000:4c:00.0,olddecodes=io+mem,decodes=io+mem:owns=none
[  101.415605] vgaarb: device changed decodes: PCI:0000:4d:00.0,olddecodes=io+mem,decodes=io+mem:owns=none
[  340.997192] vgaarb: device changed decodes: PCI:0000:4b:00.0,olddecodes=io+mem,decodes=io+mem:owns=none
[  341.026068] snd_hda_intel 0000:4b:00.1: Handle vga_switcheroo audio client

```

---

### Post by KillerKelvUK on 2016-08-20
Hey bluedragon1460, Cale mentioned he had a friend he was troubleshooting with and from you post I'm guessing you're his friend?

I've been having a read of this [http://git.qemu.org/?p=qemu.git;a=blob;f=docs/igd-assign.txt](http://git.qemu.org/?p=qemu.git;a=blob;f=docs/igd-assign.txt) whilst it isn't comparable owing to it being about iGD assignment there is a section that I think might be useful if you haven't already taken similar/same steps it notes.  I'll quote the section specifically below for the avoidance of confusions...

> 
  43 For either mode, depending on the host kernel, the i915 driver in the host
  44 may generate faults and errors upon re-binding to an IGD device after it
  45 has been assigned to a VM.  It's therefore generally recommended to prevent
  46 such driver binding unless the host driver is known to work well for this.
  47 There are numerous ways to do this, i915 can be blacklisted on the host,
  48 the driver_override option can be used to ensure that only vfio-pci can bind
  49 to the device on the host[2], virsh nodedev-detach can be used to bind the
  50 device to vfio drivers and then managed='no' set in the VM xml to prevent
  51 re-binding to i915, etc.  Also note that IGD is also typically the primary
  52 graphics in the host and special options may be required beyond simply
  53 blacklisting i915 or using pci-stub/vfio-pci to take ownership of IGD as a
  54 PCI class device.  Lower level drivers exist that may still claim the device.
  55 It may therefore be necessary to use kernel boot options video=vesafb:off or
  56 video=efifb:off (depending on host BIOS/UEFI) or these can be combined to
  57 a catch-all, video=vesafb:off,efifb:off.  Error messages such as:
  58 
  59     Failed to mmap 0000:00:02.0 BAR <>. Performance may be slow
  60 
  61 are a good indicator that such a problem exists.  The host files /proc/iomem
  62 and /proc/ioports are often useful for identifying drivers consuming ranges
  63 of the device to cause such conflicts.


On the host have you blacklisted the nvidia and nouveau modules as well as disabling the framebuffer for vesa and efi via grub?

---


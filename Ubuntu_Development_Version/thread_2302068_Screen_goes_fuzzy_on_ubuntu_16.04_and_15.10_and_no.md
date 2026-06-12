---
title: "Screen goes fuzzy on ubuntu 16.04 and 15.10 and not on other versions?"
date: 2015-11-07
forum: Ubuntu Development Version
---

### Post by sam-c on 2015-11-07
Screen goes fuzzy on ubuntu 16.04 and 15.10 and not on other versions?
Same Desktop benq Led and only since 15.04 after a while like installing or updating screen beomes unclear?

---

### Post by sam-c on 2015-11-11
How do I check the screen adapters etc?:o

---

### Post by cariboo on 2015-11-12
> **sam-c said:**
> How do I check the screen adapters etc?:o

System Settings->Software & Updates->Additional Drivers

To check what graphics adapter:

```
sudo lshw -C display
```

Should result in something like this:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display               
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:90 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)
```

---

### Post by jerrylamos on 2015-11-12
Display with Ubuntu 15.04 on has been giving me fits.  My display adapter is
 description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation

After 11 months of hassle a workaround was posted on Launchpad:
```

#sudo nano /usr/share/X11/xorg.conf.d/20-intel.conf
#Add the following lines
Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
Option "AccelMethod" "uxa"
EndSection
#reboot

```
Default AccelMethod is called "sna" which code is screwed up on this Lenovo M58p.

I'm guessing this might be worth a try for you......no promises.

For more, see 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255)

---

### Post by QDR06VV9 on 2015-11-12
I think VinDSL posted this a couple of years ago, I think it was during the saucy dev cycle.
But I can't find the link. Worked Nice on Acer 5560 and Lenovo B-570

Kind Regards

---

### Post by sam-c on 2015-11-18
*-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:ffa80000-ffafffff ioport:ec00(size=8) memory:d0000000-dfffffff memory:ffa40000-ffa7fff

This is what Uncle Sam got:lolflag:

---

### Post by QDR06VV9 on 2015-11-19
> **sam-c said:**
> *-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:ffa80000-ffafffff ioport:ec00(size=8) memory:d0000000-dfffffff memory:ffa40000-ffa7fff

This is what Uncle Sam got:lolflag:
Have You yet tried the workaround that jerrylamos provided above?

---


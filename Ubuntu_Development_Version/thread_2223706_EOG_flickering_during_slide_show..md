---
title: "EOG flickering during slide show."
date: 2014-05-12
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-05-12
When running s slide show using eog, I get a lot of flickering, When running a slide show, in gnome-shell in vbox using the same pictures things run as they should. Has any one else seen this.

I'm wondering if it may be the drivers, as Utopic doesn't have drivers for my Nvidia GeForce GTX 750 yet. I'm using the nvidia 337.19 driver from xorg-edgers ppa.

---

### Post by ventrical on 2014-05-14
[s] EOG?

What variants of ubuntu do you mean ? Just gnome-shell or Unity too?. [/s]

Works great here on Gallium 0.4 on NVA8.

 I'll switch to nVidia install and see, later :)

---

### Post by ventrical on 2014-05-14
Slide show works fine here on:

Unity

```


04:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 GS] (rev a1)
ventrical@ventrical-Asus-Overclock:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic

```

using 

nvidia-current 

304.117

---

### Post by cariboo on 2014-05-14
Although the problems seems to be resolved after a couple of days of updates, I'd just like to post my graphic cards details, for others with newer hardware:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display               
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:89 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fe000000-fe07ffff

```

---


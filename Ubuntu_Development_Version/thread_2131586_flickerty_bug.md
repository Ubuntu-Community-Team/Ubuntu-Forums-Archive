---
title: "flickerty bug"
date: 2013-04-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-04-02
I need some advice on how to file a persistent bug that causes my Dell Dimension 3100 to become 'flickery' during bootup and while in Unity (therefore it is not a Unity bug?)

  This has only happened with the **raring** i386  cycle. I tried to run the Beta lastnight  but not only did I get the flickerty bug, the PC froze solid while testing 'live usb' (usage only-non-persistent)

  The hard install on bare metal has been acting the same way since the tool chain update .. so this is systemic with this cycle. I am just not sure if it is the video drivers for Itel or something else.

```

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

```

 *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dff80000-dfffffff ioport:ecd8(size=8) memory:c0000000-cfffffff memory:dff40000-dff7ffff

```

---

### Post by dino99 on 2013-04-02
file a "persistant bug" :confused:   sudo purge april joke  :P

---

### Post by ventrical on 2013-04-03
> **dino99 said:**
> file a "persistant bug" :confused:   sudo purge april joke  :P

umm .. nevermind :)

  I have been busy during the whole beta testing event .. just got time now to drop in..

---


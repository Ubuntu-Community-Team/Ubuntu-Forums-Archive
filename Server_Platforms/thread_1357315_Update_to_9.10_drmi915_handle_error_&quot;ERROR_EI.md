---
title: "Update to 9.10: drm:i915_handle_error &quot;*ERROR* EIR stuck: 0x00000010, masking&quot;"
date: 2009-12-17
forum: Server Platforms
---

### Post by j_a_n on 2009-12-17
Hello everybody,

i've updated a 9.04-server system to 9.10. I'm a bit confused about the new kernel. The system is now using a "**2.6.31-16-generic-pae**" kernel. Before the upgrade (in 9.04) a "**2.6.28-16-server**" kernel was installed. Isn't there a special server version for the new 2.6.31 kernel?

Now (with 9.10), the server starts with a frame buffer (which was not the case under 9.04). I read about new intel graphic support that is now enabled by default in the kernel.
lshw shows:
```
[...]
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff(prefetchable) memory:ffa80000-ffafffff
[...]
```With the enabled frame buffer dmesg shows the following errors:
```
[...]
[   10.632440] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[   10.632454] render error detected, EIR: 0x00000010
[   10.646228] [drm] DAC-5: set mode 1280x1024 11
[   10.695980] Console: switching to colour frame buffer device 160x64
[...]
```After adding "**i915.modeset=0**" in /boot/grub/menu.lst the server boots now without the frame buffer and no error messages appears in the dmesg output.

In result I've two questions:

[LIST]
[*]Is there a special server kernel version for 9.10?
[*]What are the reasons for the dmesg errors?
[/LIST]

---

### Post by iishiii on 2010-01-19
how to add this

---


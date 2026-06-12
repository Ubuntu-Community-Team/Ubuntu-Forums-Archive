---
title: "possible missing firmware loop"
date: 2016-12-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-12-01
every time I update/upgrade zesty I get -

```

Processing triggers for initramfs-tools (0.125ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-28-generic
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915


```

I know there was something posted here in the forums about it.

and it runs Haswell desktop just fine.

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 12.0.3 Direct Rendering: Yes

```

---

### Post by bearlake on 2016-12-01
> **ventrical said:**
> every time I update/upgrade zesty I get -

```

Processing triggers for initramfs-tools (0.125ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-28-generic
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915


```

I know there was something posted here in the forums about it.

and it runs Haswell desktop just fine.

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 12.0.3 Direct Rendering: Yes

```

Seen the same thing here as well.

---

### Post by Yellow Pasque on 2016-12-05
Does it prevent the update from completing or does it just give annoying warnings?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626740)

---

### Post by ventrical on 2016-12-05
> **Temüjin said:**
> Does it prevent the update from completing or does it just give annoying warnings?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626740)

Ahhh yes.. just the warnings .. but the updates complete just fine  and video works just fine. Thanks for the reference about the bug being closed.

Regards..

---


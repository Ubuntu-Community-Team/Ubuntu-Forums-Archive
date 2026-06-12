---
title: "modprobe hangs"
date: 2009-01-04
forum: Server Platforms
---

### Post by rbcurtis on 2009-01-04
Modprobe is hanging on several devices in my Compaq / HP Proliant ML570 G2.  In 'ps' the device only shows up as a PCI ID string.  The modprobe instances hang and haven't gone away after days of runtine.

A) Is there an easy way to map these pci strings to a human readable device name so that I can debug?

B) Can I blacklist or prevent modprobe from trying to load these devices (by PCI ID string instead of by alias)?

'PS' output:
```

root      2673  0.0  0.0   1788   624 ?        D<   12:20   0:00 /sbin/modprobe -Q pci:v00001166d00000201sv00001166sd00000201bc06sc01i00
root      2695  0.1  0.0   1776   612 ?        S<   12:20   0:17 /sbin/modprobe -Q pci:v00000E11d0000A0F7sv00000E11sd0000A2FEbc08sc04i00
root      2983  0.0  0.0   1828   668 ?        D<   12:20   0:00 /sbin/modprobe -Q acpi:PNP0400:

```

---


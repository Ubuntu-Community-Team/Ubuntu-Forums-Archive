---
title: "SMP Problem with kernels 2.6.24 -&gt; 26.27  -&gt; NMI error"
date: 2008-10-24
forum: Server Platforms
---

### Post by tempelt on 2008-10-24
hi,
We have several RX200 S4 Fujitsu Siemens servers which run Ubuntu Hardy.

They are all brand-new dual-quad SMP systems.

When the Hardy kernel starts it detects the CPUs and thows NMI Errors with the following dmesg output:

```
[   10.722140] pcieport-driver 0000:01:00.0: setting latency timer to 64
[   10.723925] pcieport-driver 0000:02:00.0: setting latency timer to 64
[   10.724612] pcieport-driver 0000:02:00.0: found MSI capability
[   10.726536] pcieport-driver 0000:02:01.0: setting latency timer to 64
[   10.727222] pcieport-driver 0000:02:01.0: found MSI capability
[   10.729107] isapnp: Scanning for PnP cards...

[   10.960000] Uhhuh. NMI received for unknown reason a1 on CPU 0.
[   10.960000] You have some hardware problem, likely on the PCI bus.
[   10.960000] Dazed and confused, but trying to continue
```

i will append the full dmesg output and some more infos after the weekend.

The problem seems to occur on different CPUs (even nonexisting ones -like cpu 24...)

I have already tried all the acpi/apic kernel parameters from: [http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

but that did not help.


The FSC hotline told me: "Hardy kernels (>2.6.20) are science fiction ;) and not supported! -change the distribution."

But we have to use ubuntu on these machines.


Does anyone know a solution for this?
Is this a critical error - we currently have to "ignore" them.

Any help is very much appreciated!
Stephan

---


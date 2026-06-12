---
title: "Where to look to confirm SATA link speed?"
date: 2012-04-26
forum: Server Platforms
---

### Post by MakOwner on 2012-04-26
Where can I look to confirm that I have a consistent link speed to all drives through SATA port multipliers?

I see my enclosure drive lights blink as the system comes up as the link to the drives are initiated.  I see a lot of "hard restting link" in the dmesg logs.  Is there a place in the /proc filesystem that will tell me the link speed of each controller/device?

---

### Post by darkod on 2012-04-26
If I am not mistaken it's somewhere at the top of dmesg when the interfaces are brought up.

I think you could filter with something like:
cat dmesg | grep sata

---

### Post by MakOwner on 2012-04-26
> **darkod said:**
> If I am not mistaken it's somewhere at the top of dmesg when the interfaces are brought up.

I think you could filter with something like:
cat dmesg | grep sata

And I see a lot of resets. It's not at all clear what the final configuration is.

example:
```

$ dmesg | grep SATA
[    0.558861] ata3: SATA max UDMA/133 cmd 0xac98 ctl 0xac90 bmdma 0xac60 irq 20
[    0.558932] ata4: SATA max UDMA/133 cmd 0xac80 ctl 0xac78 bmdma 0xac68 irq 20
[    0.943593] ata5: SATA max UDMA/100 host m128@0xfe9ffc00 port 0xfe9f0000 irq 16
[    0.943682] ata6: SATA max UDMA/100 host m128@0xfe9ffc00 port 0xfe9f2000 irq 16
[    0.943771] ata7: SATA max UDMA/100 host m128@0xfe9ffc00 port 0xfe9f4000 irq 16
[    0.943859] ata8: SATA max UDMA/100 host m128@0xfe9ffc00 port 0xfe9f6000 irq 16
[    3.160021] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    3.550219] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    3.920218] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.290221] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.660218] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.030217] ata5.04: SATA link down (SStatus 0 SControl 320)
[    5.400218] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   12.570019] ata5.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   12.940218] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   13.310218] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   13.680217] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   14.050222] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   14.420219] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   21.800019] ata5.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   22.170218] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   22.540219] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   22.910217] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   23.280217] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   23.650216] ata5.04: SATA link down (SStatus 0 SControl 320)
[   24.020220] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   31.370019] ata5.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   31.740218] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   32.110218] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.480217] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.850216] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   33.220217] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   40.660019] ata5.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   41.030218] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   41.400216] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   41.770218] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   42.140217] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   42.510221] ata5.04: SATA link down (SStatus 0 SControl 320)
[   42.880216] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   45.372522] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   45.760218] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   46.130218] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   46.500200] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   46.870218] ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   47.240219] ata6.04: SATA link down (SStatus 0 SControl 320)
[   47.610218] ata6.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   54.780019] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   55.150217] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   55.520221] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   55.890219] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   56.260217] ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   56.630218] ata6.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   64.010025] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   64.380218] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   64.750217] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   65.120220] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   65.490219] ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   65.860218] ata6.04: SATA link down (SStatus 0 SControl 320)
[   66.230218] ata6.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   73.580019] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   73.950217] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   74.320218] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   74.690217] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   75.060219] ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   75.430221] ata6.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   82.860019] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   83.230218] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   83.600218] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   83.970218] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   84.340218] ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   84.710217] ata6.04: SATA link down (SStatus 0 SControl 320)
[   85.080219] ata6.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   87.570018] ata7: SATA link down (SStatus 0 SControl 0)
[   89.700016] ata8: SATA link down (SStatus 0 SControl 0)


```

---


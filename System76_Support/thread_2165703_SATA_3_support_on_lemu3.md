---
title: "SATA 3 support on lemu3"
date: 2013-08-05
forum: System76 Support
---

### Post by rtrejo1 on 2013-08-05
I currently own a lemu3 laptop that shipped with a SATA 2 HDD.  I'm considering purchasing a SATA 3 SSD.  If I were to swap out the HDD for desired SSD, would the SSD operate at SATA 3 speeds or would it fall back to SATA 2 speeds?  It seems my hardware supports SATA 3 based on the output of lspci and dmesg commands.

Output of lspci | grep -i sata:
```
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
```

Output of dmesg | grep -i sata:
```
[    2.261197] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    2.269837] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 40
[    2.269840] ata3: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06200 irq 40
[    2.588834] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.588866] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[15861.641243] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[15864.046641] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

```

---

### Post by golfdiesel on 2013-08-06
From the first line of dmesg you can see that the controller reports to be able to handle 6 Gbps speeds so a 6 Gbps drive should operate on that speed.

---


---
title: "Cryptic message in dmesg (2:2:1: cannot get freq at ep 0x82)"
date: 2012-09-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-01
```
[45378.422111] 2:2:1: cannot get freq at ep 0x82
```

My uptime is about 14 hours, it's not boot related. I can't associate that to anything. There's nothing strange going on in the OS. dmesg shows no related message immediately above or below that.

Google shoes me some instances of similar messages in posts and bug reports about USB devices problems, alsa and sound chipsets, and other stuff. It's not really conclusive for me. 
 
Can anyone give me a tip?

:confused:

Regards,
Effenberg

---

### Post by cariboo on 2012-09-01
Could it have something to do with ACPI? the only place I get that address is in this line:

> [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)

---


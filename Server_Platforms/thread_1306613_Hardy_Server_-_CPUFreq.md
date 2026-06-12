---
title: "Hardy Server - CPUFreq"
date: 2009-10-30
forum: Server Platforms
---

### Post by superFerra on 2009-10-30
Hello,
i own an HP XW8200 that i use as home server. It's a 2x 3.GHz XEON and it's quite a power consuming solution.
It's running a Hardy Server 8.04 64bit
I'm tring install cpufrequtils and use cpuscaling to reduce power consumption when idle.
i've updated my board bios and dmesg say:
```

...
[   23.515807] ACPI: Processor [CPU0] (supports 8 throttling states)
[   23.515859] ACPI: Processor [CPU1] (supports 8 throttling states)
[   23.515931] ACPI: Processor [CPU2] (supports 8 throttling states)
[   23.515982] ACPI: Processor [CPU3] (supports 8 throttling states)
...

```

but if i issue 

```

sudo modprobe acpi-cpufreq.ko
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-25-server/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

```

Can someone point me to a solution?
TIA

---

### Post by superFerra on 2009-11-07
OK, i managed to recompile the kernel with correct p4_clockmod module. Works ok but power consumptions are still high...

Are there any other power manager that i should try?

---


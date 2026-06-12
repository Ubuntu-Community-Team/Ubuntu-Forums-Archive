---
title: "Hyperthreading with 8 physical cores, only 8 cpus shown in procinfo?"
date: 2010-11-11
forum: Server Platforms
---

### Post by peppernicus on 2010-11-11
Hi All:

Running Maverick x64 server here.  I have a number of Sun FIRE 4170 servers each with 2 Xeon X5460 quad-core CPUs inside. HT is on in the bios.  When checking /proc/cpuinfo, I note that /proc/cpuinfo only shows 8 total processors instead of the 16 I'd expect.  Other 4- or 2-way HT hosts have additional entries in cpuinfo for the HT threads (double the # of physical cores) but they don't here.

Is this normal?  I've checked dmesg and NR_CPUS is indeed set to 64 in the -server kernel.

Here's a 4-core i7 w/ HT on:

[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs

And here's the Xeon:

[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs

Any ideas?

Thanks,
-tom

---

### Post by CharlesA on 2010-11-11
See what ***htop*** says.

---

### Post by peppernicus on 2010-11-11
Hi Charles:

Looks like htop is showing the correct number of physical CPUs, yes, but I'm still wondering how I can determine if ubuntu's actually using HT on all 8 cores.

Other OSes show a total of 16 logical CPUs present.  I'm just wondering if for some reason ubuntu would not show the HT threads in /proc/cpuinfo on an 8-core box vs. showing them for <= 4 cores.

---

### Post by CharlesA on 2010-11-11
It should be enabled by default, since it works with the i7.

According to the [spec sheet]("http://ark.intel.com/Product.aspx?id=33087"), that CPU doesn't support hyperthreading.

---

### Post by psusi on 2010-11-11
The stock kernel is configured to support a maximum of 8 cpus.

---


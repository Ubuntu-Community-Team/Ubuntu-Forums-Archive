---
title: "power management and cpu clock"
date: 2012-08-16
forum: System76 Support
---

### Post by runny6play on 2012-08-16
Im running a gazp6 with an i7 and am having the  unfortunate problem that on battery it will not up clock past 1.1 MHz. the only three things I can thing of causing this is apci, some BIOS power management, or a part of intell microcode. I just wanted to know if this was something specific to system76 systems and if the BIOS is the cause. I can't find anything acpi related to it.

---

### Post by Carborundum on 2012-08-16
How are you reading the CPU clock?

---

### Post by runny6play on 2012-08-17
i7z
cpufreq-aperf
and cat /proc/cpuinfo |grep MHz
while the They all show slightly different results. They all show a cap of 1.2 GHz while on battery
I should also probably let you know im running arch-Linux.
rmmoding the ac module seems to work. But I beleave thats a very round about way of doing it as its just hiding the fact that its unplugged from the system.
(the reason I posted in this section rather than other OS is that it is specifically about system76 and asking weather there was something built into the BIOS triggering it.)

---


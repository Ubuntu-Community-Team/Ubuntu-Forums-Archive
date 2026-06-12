---
title: "hp-pavilion-13-a200-x360-convertible-pc won't boot 19.10 livecd (kernel)"
date: 2019-10-13
forum: Ubuntu Development Version
---

### Post by ilgaz on 2019-10-13
Hi,

As I already live problems with my wireless on Ubuntu stable LTS, I thought it would be a nice idea to test current beta.

uname -a output follows (on current stable)
Linux ilgaz-HP-Pavilion-13-x360-PC 4.15.0-65-generic #74-Ubuntu SMP Tue Sep 17 17:06:04 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

My GRUB commandline:

GRUB_CMDLINE_LINUX_DEFAULT="verbose pci=biosirq acpi=off"

(acpi=off definitely needed to boot or it freezes. pci=biosirq is for bcm43142 device which fails to get IRQ normally, dmesg suggested it)

Issue is:

Something happened in 5.x kernel which fails to boot even with acpi=off , distribution hardly matters however Fedora 30 current boots with no issues.

When I attempt to boot via "dd" written (no trickery of any kind) USB3 key:

1) It shows a blank screen with frozen (still) cursor
2) Powers down external USB disk
3) Becomes totally unresponsive, caps lock key led doesn't function anymore and CPU seems to do nothing as the fan stops.

How would one report a bug like that? No logs, nothing to capture? Is there any parameter to try? Or pass a kernel parameter to produce a log file?

Have a nice day

---

### Post by ilgaz on 2019-10-13
I solved this and possibly all other kernel 5.x kernels by

acpi_osi= pci=biosirq and removing acpi=off argument.

IMHO this should be still reported to Linux kernel team. Kernel 4.x boots only with acpi=off and 5.x freezes, needing that removed and adding acpi_osi=

---


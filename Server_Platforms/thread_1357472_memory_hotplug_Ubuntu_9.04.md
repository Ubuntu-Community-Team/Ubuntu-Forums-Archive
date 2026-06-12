---
title: "memory hotplug Ubuntu 9.04"
date: 2009-12-17
forum: Server Platforms
---

### Post by iaon on 2009-12-17
Hello!

Do Anybody knows way to increase memory size on the fly?


I found following manuals 
[http://adaptivethinking.wordpress.com/2009/07/27/vsphere-esx4-hot-add-memory-for-linux-guests/](http://adaptivethinking.wordpress.com/2009/07/27/vsphere-esx4-hot-add-memory-for-linux-guests/)
/usr/src/linux-source-2.6.28/Documentation/memory-hotplug.txt
But it need to manipulate with /sys/devices/system/memory. It is absent on my systems

ls /sys/devices/system/
clocksource  cpu  i8237  i8259    ioapic    irqrouter  lapic  timekeeping

Additional  information:

Kernel isn't customised. System runs into VMWare ESX4

uname -a
Linux  2.6.28-17-server #58-Ubuntu SMP Tue Dec 1 22:13:36 UTC 2009 x86_64 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

:/boot$ grep hotplug -i config-2.6.28-17-server
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ARCH_ENABLE_MEMORY_HOTPLUG=y
CONFIG_HOTPLUG=y
CONFIG_HOTPLUG_CPU=y
CONFIG_HOTPLUG_PCI=y
CONFIG_HOTPLUG_PCI_ACPI=m
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_HOTPLUG_PCI_CPCI=y
CONFIG_HOTPLUG_PCI_CPCI_GENERIC=m
CONFIG_HOTPLUG_PCI_CPCI_ZT5550=m
CONFIG_HOTPLUG_PCI_FAKE=m
CONFIG_HOTPLUG_PCI_PCIE=y
CONFIG_HOTPLUG_PCI_SHPC=m

---

### Post by Vegan on 2009-12-17
Never ever attempt to install or replace memory in a machine while it is operating, you will destroy the machine.

ALWAYS turn the machine off to change hardware.

---

### Post by Xianath on 2009-12-17
Frankly, I believe the answer is "no".

If your question is how to increase the VM memory allocation, I don't think you can do it on the fly but the VMware forums would be a better stop for that.

If you need to increase the physical memory of the ESX host, I honestly haven't heard of a PC that is able to do it. Sun Sparc, IBM Power, and most big iron are all capable of doing it, but as for the PC, perhaps only some high-end server board? Then again, your OS (in this case the ESX supervisor) must support such an operation. Again, a question for the VMware forums.

If you have an extra box with more RAM, you could migrate your VM provided you have vSphere. That's way too many assumptions :)

Regards,
Peter

---

### Post by Vegan on 2009-12-17
I know of several high-end machines that claimed hot-plug, ended up as expensive boat anchors.

I cannot stress enough, shut it down before any hardware changes except for external disks that are designed that way.

The amount of downtime is not significant for any server. Even this forum was down due to a database error that kept it down for many hours.

While minimizing downtime is attracting, there comes a time when downtime is necessary.

---

### Post by iaon on 2009-12-22
[Xianath]("http://ubuntuforums.org/member.php?u=22181") My question was how to increase the VM memory allocation.

Answer to myself:

Ubuntu kernel does not support memory hotplug by default. This feature isn't compatible with SUSPEND feature. Do anybody knows reason to use suspend for server? :)

So we need to rebuild kernel.

I removed following options from kernel config
```
CONFIG_ACPI_SLEEP=y
CONFIG_ARCH_HIBERNATION_HEADER=y
CONFIG_HIBERNATION=y
CONFIG_PM_STD_PARTITION=""
CONFIG_PM_TEST_SUSPEND=y
CONFIG_PM_TRACE_RTC=y
CONFIG_PM_TRACE=y
CONFIG_SUSPEND_FREEZER=y
CONFIG_SUSPEND=y
```and added following

```
CONFIG_ACPI_HOTPLUG_MEMORY=y
CONFIG_ACPI_NUMA=y
CONFIG_ARCH_MEMORY_PROBE=y
CONFIG_HAVE_ARCH_EARLY_PFN_TO_NID=y
CONFIG_K8_NUMA=y
CONFIG_MEMORY_HOTPLUG_SPARSE=y
CONFIG_MEMORY_HOTPLUG=y
CONFIG_MIGRATION=y
CONFIG_NEED_MULTIPLE_NODES=y
CONFIG_NODES_SHIFT=6
CONFIG_NODES_SPAN_OTHER_NODES=y
CONFIG_NUMA=y
CONFIG_X86_64_ACPI_NUMA=y

```
it works! :)

---


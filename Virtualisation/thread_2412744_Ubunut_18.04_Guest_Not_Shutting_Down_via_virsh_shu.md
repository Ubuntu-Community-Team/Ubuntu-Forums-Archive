---
title: "Ubunut 18.04 Guest Not Shutting Down via virsh shutdown"
date: 2019-02-16
forum: Virtualisation
---

### Post by brownatron on 2019-02-16
Hi there,

Having a bit of an odd problem here with an Ubunutu 18.04 (desktop) guest.
I am completely unable to shutdown the guest via a virsh shutdown command.
The command itself reports no error but the VM just doesn't do anything. :(
All my other guests shutdown fine (both Linux and Windows).
The host is running Debian 9.

I have confirmed I have acpid installed and running (included some output at the bottom of this post)
I've also tried forcing acpi shutdown in grub to no avail.

Does anyone have any suggestions?

Thanks
Steve

```
ms01admin@BS-MS01:~$ sudo dmesg | grep -i acpi
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-45-generic root=UUID=ce11e92e-5ce1-40bf-a900-80242b387dde ro quiet splash acpi=force vt.handoff=1
[    0.000000] BIOS-e820: [mem 0x000000007fef0000-0x000000007fef7fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007fef8000-0x000000007fefbfff] ACPI NVS
[    0.000000] efi:  SMBIOS=0x7ecfc000  ACPI=0x7fef7000  ACPI 2.0=0x7fef7014  MEMATTR=0x7ee19018
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000007FEF7014 000024 (v02 BOCHS )
[    0.000000] ACPI: XSDT 0x000000007FEF60E8 00003C (v01 BOCHS  BXPCFACP 00000001      01000013)
[    0.000000] ACPI: FACP 0x000000007FEF2000 000074 (v01 BOCHS  BXPCFACP 00000001 BXPC 00000001)
[    0.000000] ACPI: DSDT 0x000000007FEF3000 0024A2 (v01 BOCHS  BXPCDSDT 00000001 BXPC 00000001)
[    0.000000] ACPI: FACS 0x000000007FEFA000 000040
[    0.000000] ACPI: APIC 0x000000007FEF1000 0000B0 (v01 BOCHS  BXPCAPIC 00000001 BXPC 00000001)
[    0.000000] ACPI: MCFG 0x000000007FEF0000 00003C (v01 BOCHS  BXPCMCFG 00000001 BXPC 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x608
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ5 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-45-generic root=UUID=ce11e92e-5ce1-40bf-a900-80242b387dde ro quiet splash acpi=force vt.handoff=1
[    0.000000] ACPI: Core revision 20170831
[    0.000000] ACPI: 1 ACPI AML tables successfully acquired and loaded
[    0.676321] PM: Registering ACPI NVS region [mem 0x7fef8000-0x7fefbfff] (16384 bytes)
[    0.677021] ACPI: bus type PCI registered
[    0.677021] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.680121] ACPI: Added _OSI(Module Device)
[    0.680122] ACPI: Added _OSI(Processor Device)
[    0.680123] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.680123] ACPI: Added _OSI(Processor Aggregator Device)
[    0.680124] ACPI: Added _OSI(Linux-Dell-Video)
[    0.680125] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.680126] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.682738] ACPI: Interpreter enabled
[    0.682745] ACPI: (supports S0 S5)
[    0.682746] ACPI: Using IOAPIC for interrupt routing
[    0.682769] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.682887] ACPI: Enabled 2 GPEs in block 00 to 3F
[    0.685700] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.685704] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.685826] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.848732] pci 0000:00:1f.0: quirk: [io  0x0600-0x067f] claimed by ICH6 ACPI/GPIO/TCO
[    1.372443] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10 11)
[    1.372541] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    1.372630] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10 *11)
[    1.372743] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    1.372843] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 *10 11)
[    1.372972] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 *10 11)
[    1.373150] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 10 *11)
[    1.373287] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10 *11)
[    1.373324] ACPI: PCI Interrupt Link [GSIA] (IRQs *16)
[    1.373333] ACPI: PCI Interrupt Link [GSIB] (IRQs *17)
[    1.373341] ACPI: PCI Interrupt Link [GSIC] (IRQs *18)
[    1.373349] ACPI: PCI Interrupt Link [GSID] (IRQs *19)
[    1.373356] ACPI: PCI Interrupt Link [GSIE] (IRQs *20)
[    1.373364] ACPI: PCI Interrupt Link [GSIF] (IRQs *21)
[    1.373372] ACPI: PCI Interrupt Link [GSIG] (IRQs *22)
[    1.373380] ACPI: PCI Interrupt Link [GSIH] (IRQs *23)
[    1.376112] ACPI: bus type USB registered
[    1.380469] PCI: Using ACPI for IRQ routing
[    1.448003] pnp: PnP ACPI init
[    1.448003] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.448003] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.448003] pnp 00:02: Plug and Play ACPI device, IDs PNP0f13 (active)
[    1.448003] pnp: PnP ACPI: found 3 devices
[    1.453198] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    1.460075] clocksource: Switched to clocksource acpi_pm
[    1.699970] ACPI: PCI Interrupt Link [GSIF] enabled at IRQ 21
[    2.344424] ACPI: Power Button [PWRF]
[    2.521662] ACPI: PCI Interrupt Link [GSIA] enabled at IRQ 16
[    4.484533] acpi PNP0A08:00: _OSC: platform does not support [SHPCHotplug]
[    4.484590] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [SHPCHotplug]
[    4.973047] ACPI: PCI Interrupt Link [GSIG] enabled at IRQ 22
[    4.973596] ACPI: PCI Interrupt Link [GSIE] enabled at IRQ 20

```
[CENTER][U][B]
EDIT - Solved

[/B][/U][/CENTER]
Needed to create an event handler for the power button:
```
sudo nano /etc/acpi/events/powerbtn

```



```
event=button/power
action=/sbin/poweroff

```

```
sudo service acpid restart


```

---


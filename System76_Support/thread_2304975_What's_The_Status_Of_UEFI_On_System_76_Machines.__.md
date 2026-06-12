---
title: "What's The Status Of UEFI On System 76 Machines.  Ordered Wild Dog Pro, UEFI On It?"
date: 2015-12-01
forum: System76 Support
---

### Post by MechaMechanism on 2015-12-01
What's The Status Of UEFI On System 76 Machines.  Ordered Wild Dog Pro, UEFI On It?  I'm Hoping System 76 has switched to UEFI by now.

Why does System 76 not use Coreboot or the version Libreboot?

---

### Post by hawkmage on 2015-12-10
Here is the output from dmidecode -t 0 on my Leopard Extreme (leox5) that I bought at the end of 2014 that shows the BIOS supports UEFI:
```
# dmidecode 2.12
SMBIOS 2.8 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1702
    Release Date: 04/10/2015
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 16384 kB
    Characteristics:
        PCI is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 5.6
```

---

### Post by MechaMechanism on 2015-12-10
Same here.

```
nate@frontier:~$ sudo dmidecode -t 0
[sudo] password for nate: 
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: F2
    Release Date: 10/19/2015
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 16384 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 5.6
```

---


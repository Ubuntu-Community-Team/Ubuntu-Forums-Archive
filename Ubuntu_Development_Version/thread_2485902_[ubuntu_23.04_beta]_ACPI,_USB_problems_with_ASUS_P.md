---
title: "[ubuntu 23.04 beta] ACPI, USB problems with ASUS PRIME B650-PLUS and Ryzen 9 9700X"
date: 2023-04-13
forum: Ubuntu Development Version
---

### Post by eserinione on 2023-04-13
Hello,
I'm experiencing very slow (more than 30-40s) boot / shutdown times in Ubuntu 23.04 beta. According to the logs there are problems related to USB 3 controllers, bluetooth and probably more importantly with ACPI. I understand this may be a "hardware too new" issue, but still i felt like to share seeing that this is a beta version. As stated in the post title my system is:

AMD Ryzen 9 9700X
Motherboard ASUS PRIME B650-PLUS
Integrated AMD GPU

I checked with the motherboard manufacturer if there are new BIOS drivers for the motherboard but the BIOS update is a beta version but i don't feel too comfortable trying flashing a beta bios version and see what happens :)

Some dmidecode output:

```

Base Board Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Product Name: PRIME B650-PLUS
    Version: Rev 1.xx
    Asset Tag: Default string
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0


Handle 0x0004, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled


Handle 0x0045, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Realtek ALC897 Audio
    Type: Sound
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:0c:00.6


Handle 0x0046, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: Realtek RTL8125BG LAN
    Type: Ethernet
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:07:00.0

```

```

Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 0823
    Release Date: 11/21/2022
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 32 MB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 8.23

```

```

Handle 0x000F, DMI type 4, 48 bytes
Processor Information
    Socket Designation: AM5
    Type: Central Processor
    Family: Zen
    Manufacturer: Advanced Micro Devices, Inc.
    Signature: Family 25, Model 97, Stepping 2
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        HTT (Multi-threading)
    Version: AMD Ryzen 9 7900X 12-Core Processor            
    Voltage: 1.3 V
    External Clock: 100 MHz
    Max Speed: 5700 MHz
    Current Speed: 4700 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x000C
    L2 Cache Handle: 0x000D
    L3 Cache Handle: 0x000E
    Serial Number: Unknown
    Asset Tag: Unknown
    Part Number: Unknown
    Core Count: 12
    Core Enabled: 12
    Thread Count: 24
    Characteristics:
        64-bit capable
        Multi-Core
        Hardware Thread
        Execute Protection
        Enhanced Virtualization
        Power/Performance Control

```

This is an export of the relevant logs:

```

09:20:54 kernel: xhci_hcd 0000:0d:00.0: HC died; cleaning up
09:20:54 kernel: xhci_hcd 0000:0d:00.0: HC died; cleaning up
09:20:54 kernel: xhci_hcd 0000:0d:00.0: xHCI host controller not responding, assume dead
09:20:37 systemd: Failed to start app-gnome-spice\x2dvdagent-2304.scope - Application launched by gnome-session-binary.
09:20:37 systemd: Failed to start app-gnome-spice\x2dvdagent-2304.scope - Application launched by gnome-session-binary.
09:20:35 systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dsecrets-2023.scope - Application launched by gnome-session-binary.
09:20:35 gdm-session-wor: gkr-pam: unable to locate daemon control file
09:20:28 (uetoothd): src/plugin.c:plugin_init() Failed to init bap plugin
09:20:28 (uetoothd): src/plugin.c:plugin_init() Failed to init bap plugin
09:20:28 (uetoothd): src/plugin.c:plugin_init() Failed to init mcp plugin
09:20:28 (uetoothd): src/plugin.c:plugin_init() Failed to init vcp plugin
09:20:27 kernel: uvcvideo 4-1:1.1: Failed to set UVC probe control : -32 (exp. 26).
09:20:26 systemd-udevd: event5: Failed to call EVIOCSKEYCODE with scan code 0x7c, and key code 190: Invalid argument
09:20:26 systemd-udevd: event5: Failed to call EVIOCSKEYCODE with scan code 0x7c, and key code 190: Invalid argument
09:20:26 systemd-udevd: event_source: Failed to get device name: No such file or directory
09:20:26 kernel: hub 6-0:1.0: config failed, hub doesn't have any ports! (err -19)
09:20:26 kernel: ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20221020/psobject-220)
09:20:26 kernel: ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20221020/psobject-220)
09:20:26 kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.GPP7.UP00.DP40.UP00.DP68], AE_NOT_FOUND (20221020/dswload2-162)

```

Other than that, 23.04 beta is running flawlessy and i really love it, thanks :)

---

### Post by IanW on 2023-04-14
I understand that DDR5 motherboards do an extended set of "memory training" excercises on boot.
Could that be part of your problem?

---

### Post by eserinione on 2023-04-14
Thanks i dind't knew about that so i went and disabled the feature in the bios but i still get almost 53 seconds of boot time, 50 of which are spent before the motheboard manufacturer logo shows up.

---

### Post by rcosu on 2023-06-11
Just curious, but is this still an issue for you?  I ask, because I was looking at a new motherboard with that chipset so curious if the issue has cleared up.

---

### Post by dhotrum52 on 2023-08-04
I have an ASUS EX-H510M-v3 and a very quick boot and shut-down about 15 seconds. 
I use Ubuntu 23.04 which I think was a mistake but in Ubuntu you cannot go backwards unless you format then install new.
My motherboard has it's own problems and I am looking for an answer. If I cannot find a similar I will start a new thread
Dave

---

### Post by dhotrum52 on 2023-08-04
My ASUS has problems with installing other than MSW and especially dual boot. I would say find something else

---


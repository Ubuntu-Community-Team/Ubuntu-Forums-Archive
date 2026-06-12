---
title: "Serval professional chipsets"
date: 2012-02-20
forum: System76 Support
---

### Post by kayosiii on 2012-02-20
Can somebody who has the serval professional laptop run me lspci and dump the output here.

---

### Post by isantop on 2012-02-20
The Serval uses an Intel Series 6 Chipset. I've attached some various system information:

lspci:
```
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 0e31 (rev a1)
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
```

lsusb:
```
Bus 002 Device 004: ID 5986:0343 Acer, Inc 
Bus 002 Device 003: ID 147e:1001 Upek 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod:
```
Module                  Size  Used by
xhci_hcd               58578  0 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
nvidia              10221046  44 
snd_hda_codec_nvhdmi    15451  4 
snd_hda_codec_realtek   299844  1 
joydev                 11395  0 
snd_hda_intel          26019  2 
snd_seq_midi            5932  0 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_rawmidi            22207  1 snd_seq_midi
snd_hwdep               6660  1 snd_hda_codec
snd_seq_midi_event      7291  1 snd_seq_midi
psmouse                62080  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              23850  2 snd_seq,snd_pcm
lp                     10201  0 
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
parport                37032  3 parport_pc,ppdev,lp
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
serio_raw               4910  0 
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
dm_raid45              75026  0 
xor                     4709  1 dm_raid45
sdhci_pci               7765  0 
ahci                   22210  2 
libahci                26052  1 ahci
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
jme                    33058  0 
firewire_ohci          24615  0 
video                  22176  0 
mii                     5261  1 jme
output                  2527  1 video
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
intel_agp              32462  0 
```

dmidecode:
```
# dmidecode 2.9
SMBIOS 2.6 present.
79 structures occupying 3316 bytes.
Table at 0x000EAEE0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 4.6.4
    Release Date: 01/18/2011
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 4.6

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: System76, Inc.                            
    Product Name: Serval Professional
    Version: serp7                    
    Serial Number: Not Applicable                    
    Asset Tag: Not Applicable                    
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Not Applicable                    
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: System76, Inc.                           
    Type: Notebook
    Lock: Not Present
    Version: serp7                    
    Serial Number: Not Applicable                    
    Asset Tag: Not Applicable                    
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 42 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: <OUT OF SPEC>
    Manufacturer: Intel            
    ID: A7 06 02 00 FF FB EB BF
    Version: Intel(R) Core(TM) i7-2820QM CPU @ 2.30GHz      
    Voltage: 0.0 V
    External Clock: 100 MHz
    Max Speed: 3800 MHz
    Current Speed: 2300 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Core Count: 4
    Core Enabled: 1
    Thread Count: 2
    Characteristics:
        64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 128 KB
    Maximum Size: 128 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 1024 KB
    Maximum Size: 1024 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 8192 KB
    Maximum Size: 8192 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 16-way Set-associative

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A1
    Internal Connector Type: None
    External Reference Designator: TV Out
    External Connector Type: Mini Centronics Type-14
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2A
    Internal Connector Type: None
    External Reference Designator: COM A
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2B
    Internal Connector Type: None
    External Reference Designator: Video
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9A1 - TPM HDR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9C1 - PCIE DOCKING CONN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2B3 - CPU FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6C2 - EXT HDMI
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3C1 - GMCH FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1D1 - ITP
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E2 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E4 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E3 - LPC HOT DOCKING
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E1 - SCAN MATRIX
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9G1 - LPC SIDE BAND
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J8F1 - UNIFIED
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6F1 - LVDS
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2F1 - LAI FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2G1 - GFX VID
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1G6 - AC JACK
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0020, DMI type 9, 17 bytes
System Slot Information
    Designation: J6B2
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Long
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0021, DMI type 9, 17 bytes
System Slot Information
    Designation: J6B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0022, DMI type 9, 17 bytes
System Slot Information
    Designation: J6D1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0023, DMI type 9, 17 bytes
System Slot Information
    Designation: J7B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0024, DMI type 9, 17 bytes
System Slot Information
    Designation: J8B4
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0025, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:    To Be Filled By O.E.M.

Handle 0x0026, DMI type 11, 5 bytes
OEM Strings
    String 1: 1558

Handle 0x0027, DMI type 12, 5 bytes
System Configuration Options
    Option 1: To Be Filled By O.E.M.

Handle 0x0029, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: Unknown
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x002C, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: Unknown
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x002F, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: Unknown
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0032, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: Unknown
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0035, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: Unknown
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0038, DMI type 22, 26 bytes
Portable Battery
    Location: Location of the battery
    Manufacturer: Battery Manufacturer
    Manufacture Date: 01/01/2007
    Serial Number: Serial Number
    Name: Battery Name
    Chemistry: Nickel Cadmium
    Design Capacity: Unknown
    Design Voltage: Unknown
    SBDS Version: SBDS Version Number
    Maximum Error: Unknown
    OEM-specific Information: 0x12345678

Handle 0x003B, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x003C, DMI type 34, 11 bytes
Management Device
    Description: LM78-1
    Type: LM78
    Address: 0x00000000
    Address Type: I/O Port

Handle 0x003D, DMI type 26, 22 bytes
Voltage Probe
    Description: LM78A
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x003E, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x003F, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x003C
    Component Handle: 0x003C
    Threshold Handle: 0x003D

Handle 0x0040, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78A
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0041, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0042, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x003C
    Component Handle: 0x003F
    Threshold Handle: 0x0040

Handle 0x0043, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x0040
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating

Handle 0x0044, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0045, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x003C
    Component Handle: 0x0042
    Threshold Handle: 0x0043

Handle 0x0046, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x0040
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating

Handle 0x0047, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0048, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x003C
    Component Handle: 0x0045
    Threshold Handle: 0x0046

Handle 0x0049, DMI type 29, 22 bytes
Electrical Current Probe
    Description: ABC
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x004A, DMI type 36, 16 bytes
Management Device Threshold Data

Handle 0x004B, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x003C
    Component Handle: 0x0048
    Threshold Handle: 0x0046

Handle 0x004C, DMI type 39, 22 bytes
System Power Supply
    Power Unit Group: 1
    Location: To Be Filled By O.E.M.
    Name: To Be Filled By O.E.M.
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Model Part Number: To Be Filled By O.E.M.
    Revision: To Be Filled By O.E.M.
    Max Power Capacity: Unknown
    Status: Not Present
    Type: <OUT OF SPEC>
    Input Voltage Range Switching: <OUT OF SPEC>
    Plugged: Yes
    Hot Replaceable: No
    Input Voltage Probe Handle: 0x003D
    Cooling Device Handle: 0x0043
    Input Current Probe Handle: 0x0049

Handle 0x004D, DMI type 41, 11 bytes
Unknown Type
    Header and Data:
        29 0B 4D 00 01 83 01 00 00 00 10
    Strings:
         Onboard IGD

Handle 0x004E, DMI type 41, 11 bytes
Unknown Type
    Header and Data:
        29 0B 4E 00 01 85 01 00 00 00 C8
    Strings:
         Onboard LAN

Handle 0x004F, DMI type 41, 11 bytes
Unknown Type
    Header and Data:
        29 0B 4F 00 01 81 01 00 00 03 E2
    Strings:
         Onboard 1394

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: System76, Inc.                          
    Product Name: Serval Professional
    Version: serp7                    
    Serial Number: Not Applicable                    
    UUID: 0090F5B3-05E9-0000-0000-000000000000
    Wake-up Type: Power Switch
    SKU Number: Not Applicable                    
    Family: Not Applicable                    

Handle 0x0028, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: 0x0029
    Number Of Devices: 4

Handle 0x002A, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: 0x002C
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK 0
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: 0000
    Serial Number: 02310501
    Asset Tag: 0123456789
    Part Number: 76.A300G.C120C    

Handle 0x002B, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x002A
    Memory Array Mapped Address Handle: 0x0033
    Partition Row Position: Unknown
    Interleave Position: 1
    Interleaved Data Depth: 1

Handle 0x002D, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK 1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 0123456789
    Part Number: [Empty]

Handle 0x002E, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: 0x002F
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK 2
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: 0000
    Serial Number: 02310501
    Asset Tag: 0123456789
    Part Number: 76.A300G.C120C    

Handle 0x0030, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x002E
    Memory Array Mapped Address Handle: 0x0033
    Partition Row Position: Unknown
    Interleave Position: 2
    Interleaved Data Depth: 1

Handle 0x0031, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK 3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 0123456789
    Part Number: [Empty]

Handle 0x0033, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Physical Array Handle: 0x0028
    Partition Width: 0

Handle 0x0050, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        eng
    Currently Installed Language: eng

Handle 0x0037, DMI type 22, 26 bytes
Portable Battery
    Location: Location of the battery
    Manufacturer: Battery Manufacturer
    Manufacture Date: 01/01/2007
    Serial Number: Serial Number
    Name: BATT 1
    Chemistry: Nickel Cadmium
    Design Capacity: 232 mWh
    Design Voltage: 5000 mV
    SBDS Version: 01.12.912
    Maximum Error: Unknown
    OEM-specific Information: 0x12345678

Handle 0x0051, DMI type 131, 64 bytes
OEM-specific Type
    Header and Data:
        83 40 51 00 35 00 00 00 00 00 00 00 00 00 00 00
        F8 00 49 1C FF FF FF FF 01 20 00 00 00 00 07 00
        75 04 01 00 00 00 00 00 C8 00 FF FF 00 00 00 00
        00 00 00 00 D2 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x0052, DMI type 127, 4 bytes
End Of Table
```

Please note that some of the information in the dmi table are specific to the machine we collected it from. Your information may differ slightly.

---


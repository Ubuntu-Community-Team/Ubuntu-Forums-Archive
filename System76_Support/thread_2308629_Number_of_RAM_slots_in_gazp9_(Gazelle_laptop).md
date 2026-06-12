---
title: "Number of RAM slots in gazp9 (Gazelle laptop)"
date: 2016-01-04
forum: System76 Support
---

### Post by softwaredoug on 2016-01-04
Hi, when I checked the number of RAM slots I had in hardware in Ubuntu 14.04 through dmidecode, it was reported I had 4 slots. Two of which were occupied by 8 GB DIMMS.

```
doug@76:~$ sudo dmidecode -t memory
# dmidecode 2.12
SMBIOS 2.7 present.


Handle 0x0018, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4


Handle 0x0019, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0018
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: Samsung
    Serial Number: 56201512
    Asset Tag: 9876543210
    Part Number: M471B1G73QH0-YK0  
    Rank: 2
    Configured Clock Speed: 1600 MHz


Handle 0x001B, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0018
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelA-DIMM1
    Bank Locator: BANK 1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown
    Configured Clock Speed: Unknown


Handle 0x001C, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0018
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelB-DIMM0
    Bank Locator: BANK 2
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: Samsung
    Serial Number: 56201550
    Asset Tag: 9876543210
    Part Number: M471B1G73QH0-YK0  
    Rank: 2
    Configured Clock Speed: 1600 MHz


Handle 0x001E, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0018
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelB-DIMM1
    Bank Locator: BANK 3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown
    Configured Clock Speed: Unknown

```

Opening up the back of the case, I can only find two slots. Are there expansion slots anywhere? (I'm trying to go from 16 GB->32GB)

---

### Post by Frank A on 2016-01-05
I think there are two slots under the keyboard.

---


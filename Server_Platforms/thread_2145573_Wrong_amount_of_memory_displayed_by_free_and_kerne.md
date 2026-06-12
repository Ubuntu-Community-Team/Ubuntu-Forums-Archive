---
title: "Wrong amount of memory displayed by free and kernel"
date: 2013-05-15
forum: Server Platforms
---

### Post by Nattereri on 2013-05-15
I have just discovered an inconsistancy in my new server setup. When I issue the free -m command the output states that I have 1993 total memory available when I know for a fact that this machine has 6GB installed. The kernel agrees with this number but dmidecode does not. I am posting the output of the commands to make my problem clearer. Is this a kernel bug?

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1993        287       1705          0         77        103
-/+ buffers/cache:        105       1887
Swap:         2181          0       2181
```

```
dmesg | grep Memory
[    0.000000] Memory: 2022324k/2088512k available (6820k kernel code, 456k absent, 65732k reserved, 6347k data, 948k init)
```

```
sudo dmidecode

Handle 0x0002, DMI type 2, 10 bytes
Base Board Information
        Manufacturer:  EVGA
        Product Name: 132-BL-E758
        Version: Tylersburg
        Serial Number:
        Asset Tag:
        Features:
                Board is a hosting board

Handle 0x0005, DMI type 5, 28 bytes
Memory Controller Information
        Error Detecting Method: 8-bit Parity
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 2048 MB
        Maximum Total Memory Size: 12288 MB
        Supported Speeds:
                Other
        Supported Memory Types:
                DIMM
        Memory Module Voltage: 5.0 V
        Associated Memory Slots: 6
                0x0006
                0x0007
                0x0008
                0x0009
                0x000A
                0x000B
        Enabled Error Correcting Capabilities:
                None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 0 1
        Current Speed: Unknown
        Type: DIMM
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: None
        Current Speed: Unknown
        Type: Unknown
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A2
        Bank Connections: 4 5
        Current Speed: Unknown
        Type: DIMM
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A3
        Bank Connections: None
        Current Speed: Unknown
        Type: Unknown
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A4
        Bank Connections: 8 9
        Current Speed: Unknown
        Type: DIMM
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A5
        Bank Connections: None
        Current Speed: Unknown
        Type: Unknown
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x0023, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 6 GB
        Error Information Handle: Not Provided
        Number Of Devices: 6

Handle 0x0024, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0023
        Error Information Handle: Not Provided
        Total Width: 1 bits
        Data Width: 65508 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: DDR2
        Type Detail: Synchronous
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0025, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0023
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A1
        Bank Locator: Bank2/3
        Type: Unknown
        Type Detail: Unknown
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0026, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0023
        Error Information Handle: Not Provided
        Total Width: 1 bits
        Data Width: 65508 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A2
        Bank Locator: Bank4/5
        Type: DDR2
        Type Detail: Synchronous
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0027, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0023
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A3
        Bank Locator: Bank6/7
        Type: Unknown
        Type Detail: Unknown
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0028, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0023
        Error Information Handle: Not Provided
        Total Width: 1 bits
        Data Width: 65508 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A4
        Bank Locator: Bank8/9
        Type: DDR2
        Type Detail: Synchronous
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0029, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0023
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A5
        Bank Locator: Bank10/11
        Type: Unknown
        Type Detail: Unknown
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x002A, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: Other
        Granularity: Other
        Operation: Other
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x002B, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0017FFFFFFF
        Range Size: 6 GB
        Physical Array Handle: 0x0024
        Partition Width: 1

Handle 0x002C, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0007FFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0025
        Memory Array Mapped Address Handle: 0x002B
        Partition Row Position: 1

Handle 0x002D, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000000003FF
        Range Size: 1 kB
        Physical Device Handle: 0x0026
        Memory Array Mapped Address Handle: 0x002B
        Partition Row Position: 1

Handle 0x002E, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00080000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0027
        Memory Array Mapped Address Handle: 0x002B
        Partition Row Position: 1

Handle 0x002F, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000000003FF
        Range Size: 1 kB
        Physical Device Handle: 0x0028
        Memory Array Mapped Address Handle: 0x002B
        Partition Row Position: 1

Handle 0x0030, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00100000000
        Ending Address: 0x0017FFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0029
        Memory Array Mapped Address Handle: 0x002B
        Partition Row Position: 1

Handle 0x0031, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000000003FF
        Range Size: 1 kB
        Physical Device Handle: 0x002A
        Memory Array Mapped Address Handle: 0x002B
        Partition Row Position: 1
```

---

### Post by bluefrog on 2013-05-16
what kernel are you using?

uname -a

---

### Post by CharlesA on 2013-05-16
Looks right for 2GB of ram, but not 6GB. free -m displays the memory free in megabytes, and dmesg is showing in kb.

If you have two or three sticks of memory and only one is being seen - check the bios to make sure it is seeing all the sticks, which is likely if lshw shows them.

What version of Ubuntu are you using?

What does top show?

---

### Post by Nattereri on 2013-05-16
Seems I should have started from the beginning and checked the BIOS first. #-o It was showing only 2GB of memory also, so I removed all the memory sticks and put them back in. Now everything is showing 6GB. At least now I can continue with the BTRFS experiment.

---


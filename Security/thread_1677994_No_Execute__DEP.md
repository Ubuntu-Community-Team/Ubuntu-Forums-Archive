---
title: "No Execute / DEP"
date: 2011-01-29
forum: Security
---

### Post by tigerking615 on 2011-01-29
I've been using X, but I tried logging into tty1 today and got a message saying my security wasn't adequate (see picture). I ran the check they told me to, and it seems that my computer supports this feature. I use Ubuntu 10.10 on a Sager notebook, with an InsydeH20 BIOS. I could not find any option to enable NX or anything like that in my BIOS.

1) Does enabling this feature mess with anything on Windows 7? I use both Ubuntu and Windows 7 on this laptop. 

2) How do I get into my BIOS advanced settings to change this setting? I saw on another thread that sometimes Ubuntu was giving a false flag for this, so if that's the case, I can just bypass the check, but I want to be sure that that's the case.

Thanks!

---

### Post by Jive Turkey on 2011-01-29
When you boot your computer there is a brief time when you can press a certain key to enter bios setup.  A message may appear saying what key to press.  On my Gigabyte mobo its Delete, on my intel mobo its F2 or maybe F10.  Check the documentation for your motherboard or watch for the message on the bios screen.  I have it enabled and Windows 7 is probably happier for it.

---

### Post by tigerking615 on 2011-01-30
I can get into my BIOS; it's F2. But when I'm there, there are very few options, so I'm thinking that maybe it's some sort of non-advanced mode. I need to know how to get into the more detailed options.

---

### Post by Jive Turkey on 2011-01-30
You'll likely need to find the manual for your motherboard/bios. You can get this info from the bios screen at startup (take a photo and post it if you need help figuring this out).

Make sure to investigate your bios thoroughly there may be some tab-like elements along the top of the screen that you can navigate with the right and left arrows. Otherwise, maybe try some of the function keys that don't appear to be mapped to anything, Most bios screens list what the keys do along the bottom (maybe one says "advanced mode"?) Then try some keys that aren't listed to see if it brings up more options.

---

### Post by tigerking615 on 2011-01-30
Attaching a picture of my bios (i'm on the security tab).

I tried all the unmapped F keys, but none did anything.

---

### Post by Jive Turkey on 2011-01-30
I was thinking of the initial BIOS screen that comes up before grub loads.
Have you tried googling up the manual (since you know who the vendor is)?

If you post the output from these command:
```
sudo biosdecode
```
and
```
sudo dmidecode
```
It might give us some clues.

---

### Post by tigerking615 on 2011-01-30
[http://www.google.com/url?sa=t&source=web&cd=11&ved=0CEUQFjAK&url=ftp%3A%2F%2F65.106.72.164%2FNotebook%2FCompal%2FNBLB2%2FManuals%2FService_Manual%2FNBLB2_Service_Manual_20100210_ver0.0.pdf&ei=HTtFTZGmOJGasAOpqvm7Cg&usg=AFQjCNHWv0ddDrKoCt3SB_BWnGEbqNJGIw&sig2=-Eu5jL5fk-UJ3LnoI0WSvQ](http://www.google.com/url?sa=t&source=web&cd=11&ved=0CEUQFjAK&url=ftp%3A%2F%2F65.106.72.164%2FNotebook%2FCompal%2FNBLB2%2FManuals%2FService_Manual%2FNBLB2_Service_Manual_20100210_ver0.0.pdf&ei=HTtFTZGmOJGasAOpqvm7Cg&usg=AFQjCNHWv0ddDrKoCt3SB_BWnGEbqNJGIw&sig2=-Eu5jL5fk-UJ3LnoI0WSvQ) is the manual... I didn't find anything about unlocking the BIOS or a No Execute option. Chapter 10 goes over the Security tab, and I didn't see the option. 

biosdecode output:
```

# biosdecode 2.9
ACPI 2.0 present.
	OEM Identifier: INTEL 
	RSD Table 32-bit Address: 0xBF7FE0AC
	XSD Table 64-bit Address: 0x00000000BF7FE120
PNP BIOS 1.0 present.
	Event Notification: Not Supported
	Real Mode 16-bit Code Address: F000:B9F1
	Real Mode 16-bit Data Address: 0040:0000
	16-bit Protected Mode Code Address: 0x000FB9FC
	16-bit Protected Mode Data Address: 0x00000400
	OEM Device Identifier: SST2400
SMBIOS 2.6 present.
	Structure Table Length: 2183 bytes
	Structure Table Address: 0x000EA010
	Number Of Structures: 50
	Maximum Structure Size: 226 bytes
PCI Interrupt Routing 1.0 present.
	Router ID: 00:1f.0
	Exclusive IRQs: None
	Compatible Router: 8086:122e
	Slot Entry 1: ID 02:00, on-board
	Slot Entry 2: ID 03:00, on-board
	Slot Entry 3: ID 01:00, on-board
	Slot Entry 4: ID 0b:00, on-board
	Slot Entry 5: ID 00:01, on-board
	Slot Entry 6: ID 00:02, on-board
	Slot Entry 7: ID 00:03, on-board
	Slot Entry 8: ID 00:04, on-board
	Slot Entry 9: ID 00:05, on-board
	Slot Entry 10: ID 00:06, on-board
	Slot Entry 11: ID 02:00, on-board
	Slot Entry 12: ID 03:00, on-board
	Slot Entry 13: ID 04:00, on-board
	Slot Entry 14: ID 05:00, on-board
	Slot Entry 15: ID 09:00, on-board
	Slot Entry 16: ID 0c:00, on-board
	Slot Entry 17: ID 0d:00, on-board
	Slot Entry 18: ID 0e:00, on-board
	Slot Entry 19: ID 00:16, on-board
	Slot Entry 20: ID 00:19, on-board
	Slot Entry 21: ID 00:1a, on-board
	Slot Entry 22: ID 00:1b, on-board
	Slot Entry 23: ID 00:1c, on-board
	Slot Entry 24: ID 00:1d, on-board
	Slot Entry 25: ID 00:1f, on-board
	Slot Entry 26: ID 06:00, slot number 1
	Slot Entry 27: ID 06:00, slot number 2
	Slot Entry 28: ID 06:05, slot number 3
```

```

# dmidecode 2.9
SMBIOS 2.6 present.
50 structures occupying 2183 bytes.
Table at 0x000EA010.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: INSYDE
	Version: F.05
	Release Date: 02/09/2010
	ROM Size: 1536 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 5.240

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Compal
	Product Name: NBLB2
	Version: F.00
	Serial Number: 123456789
	UUID: 42B4E716-4D77-11DF-81DD-705AB6E508D7
	Wake-up Type: Power Switch
	SKU Number: Calpella_Fab
	Family: Intel_Mobile

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: Compal
	Product Name: NBLB2
	Version: Base Board Version
	Serial Number: Base Board Serial Number
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
	Manufacturer: Compal
	Type: Notebook
	Lock: Not Present
	Version: Chassis Version
	Serial Number: Chassis Serial Number
	Asset Tag: Chassis Asset Tag
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 9, 17 bytes
System Slot Information
	Designation: J5C1
	Type: x16 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0005, DMI type 9, 17 bytes
System Slot Information
	Designation: J6C1
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0006, DMI type 9, 17 bytes
System Slot Information
	Designation: J6C2
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0007, DMI type 9, 17 bytes
System Slot Information
	Designation: J6D2
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0008, DMI type 9, 17 bytes
System Slot Information
	Designation: J7C1
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0009, DMI type 9, 17 bytes
System Slot Information
	Designation: J7D2
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x000A, DMI type 9, 17 bytes
System Slot Information
	Designation: J8C2
	Type: x16 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x000B, DMI type 9, 17 bytes
System Slot Information
	Designation: J8C1
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Other
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x000C, DMI type 11, 5 bytes
OEM Strings
	String 1: String1 for Original Equipment Manufacturer
	String 2: String2 for Original Equipment Manufacturer
	String 3: String3 for Original Equipment Manufacturer
	String 4: String4 for Original Equipment Manufacturer
	String 5: String5 for Original Equipment Manufacturer

Handle 0x000D, DMI type 12, 5 bytes
System Configuration Options
	Option 1: String1 for Type12 Equipment Manufacturer
	Option 2: String2 for Type12 Equipment Manufacturer
	Option 3: String3 for Type12 Equipment Manufacturer
	Option 4: String4 for Type12 Equipment Manufacturer

Handle 0x000E, DMI type 15, 29 bytes
System Event Log
	Area Length: 0 bytes
	Header Start Offset: 0x0000
	Data Start Offset: 0x0000
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x12345678
	Header Format: OEM-specific
	Supported Log Type Descriptors: 3
	Descriptor 1: POST memory resize
	Data Format 1: None
	Descriptor 2: POST error
	Data Format 2: POST results bitmap
	Descriptor 3: Log area reset/cleared
	Data Format 3: None

Handle 0x000F, DMI type 21, 7 bytes
Built-in Pointing Device
	Type: Touch Pad
	Interface: PS/2
	Buttons: 4

Handle 0x0010, DMI type 27, 14 bytes
Cooling Device
	Type: Fan
	Status: OK
	OEM-specific Information: 0x00000000
	Nominal Speed: 2000 rpm

Handle 0x0011, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0012, DMI type 39, 22 bytes
System Power Supply
	Location: OEM_Define0
	Name: OEM_Define1
	Manufacturer: OEM_Define2
	Serial Number: OEM_Define3
	Asset Tag: OEM_Define4
	Model Part Number: OEM_Define5
	Revision: OEM_Define6
	Max Power Capacity: 0.075 W
	Status: Present, OK
	Type: Regulator
	Input Voltage Range Switching: Auto-switch
	Plugged: No
	Hot Replaceable: No
	Cooling Device Handle: 0x0010

Handle 0x0013, DMI type 40, 18 bytes
Unknown Type
	Header and Data:
		28 12 13 00 02 06 04 00 05 01 AA 07 00 00 05 02
		DC 05
	Strings:
		PCIExpressx16
		Compiler Version: VC 9.0

Handle 0x0014, DMI type 41, 11 bytes
Unknown Type
	Header and Data:
		29 0B 14 00 01 85 01 00 00 00 01
	Strings:
		Hanksville Gbe Lan Connection

Handle 0x0015, DMI type 131, 5 bytes
OEM-specific Type
	Header and Data:
		83 05 15 00 50
	Strings:
		DJ

Handle 0x0016, DMI type 22, 26 bytes
Portable Battery
	Location: Fake
	Manufacturer: -Virtual Battery 0-
	Manufacture Date: 10/12/2007
	Serial Number: Battery 0
	Name: CRB Battery 0
	Chemistry: Lithium Ion
	Design Capacity: Unknown
	Design Voltage: Unknown
	SBDS Version: Not Specified
	Maximum Error: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0017, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 17 00 5A 5A

Handle 0x0018, DMI type 129, 8 bytes
OEM-specific Type
	Header and Data:
		81 08 18 00 01 01 02 01
	Strings:
		Intel_ASF
		Intel_ASF_001

Handle 0x0019, DMI type 130, 20 bytes
OEM-specific Type
	Header and Data:
		82 14 19 00 24 41 4D 54 01 01 01 01 01 A5 1F 02
		00 00 00 00

Handle 0x001A, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: No Error
	Number Of Devices: 2

Handle 0x001B, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: 0x001D
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK 0
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1067 MHz (0.9 ns)
	Manufacturer: Not Specified
	Serial Number: 000864EF
	Asset Tag: Unknown
	Part Number: JM1333KSU-2G      

Handle 0x001C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: None
	Current Speed: Unknown
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x001D, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x001E, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x001B
	Memory Array Mapped Address Handle: 0x002A
	Partition Row Position: Unknown
	Interleave Position: 1
	Interleaved Data Depth: 1

Handle 0x001F, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: Not Provided
	Total Width: 8 bits
	Data Width: 8 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK 1
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1067 MHz (0.9 ns)
	Manufacturer: Not Specified
	Serial Number: 00000000
	Asset Tag: Unknown
	Part Number: Not Specified

Handle 0x0020, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: None
	Current Speed: Unknown
	Type: DIMM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0021, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0022, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: 0x0024
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK 2
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1067 MHz (0.9 ns)
	Manufacturer: Not Specified
	Serial Number: 000864EF
	Asset Tag: Unknown
	Part Number: JM1333KSU-2G      

Handle 0x0023, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: None
	Current Speed: Unknown
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0024, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0025, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0022
	Memory Array Mapped Address Handle: 0x002A
	Partition Row Position: Unknown
	Interleave Position: 2
	Interleaved Data Depth: 1

Handle 0x0026, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: Not Provided
	Total Width: 8 bits
	Data Width: 8 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK 3
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1067 MHz (0.9 ns)
	Manufacturer: Not Specified
	Serial Number: 00000000
	Asset Tag: Unknown
	Part Number: Not Specified

Handle 0x0027, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM3
	Bank Connections: None
	Current Speed: Unknown
	Type: DIMM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0028, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0029, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x002A, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x001A
	Partition Width: 0

Handle 0x002B, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		Unknown
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 8192 MB
	Maximum Total Memory Size: 16384 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		Other
	Memory Module Voltage: Unknown
	Associated Memory Slots: 2
		0x001C
		0x0023
	Enabled Error Correcting Capabilities:
		None

Handle 0x002C, DMI type 4, 42 bytes
Processor Information
	Socket Designation: CPU
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel(R) Corporation
	ID: 52 06 02 00 FF FB EB BF
	Version: Intel(R) Core(TM) i7 CPU       M 620  @ 2.67GHz
	Voltage: 0.0 V
	External Clock: 1066 MHz
	Max Speed: 2666 MHz
	Current Speed: 2668 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0030
	L2 Cache Handle: 0x002F
	L3 Cache Handle: 0x002D
	Serial Number: Not Specified
	Asset Tag: FFFF
	Part Number: Not Specified
	Core Count: 2
	Core Enabled: 2
	Thread Count: 4
	Characteristics:
		64-bit capable

Handle 0x002D, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3 Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 4096 KB
	Maximum Size: 4096 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 16-way Set-associative

Handle 0x002E, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x002F, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0030, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 4-way Set-associative

Handle 0x0031, DMI type 127, 4 bytes
End Of Table


```

---

### Post by Jive Turkey on 2011-01-30
I googled about and found some others on different forums asking the same question as you.  They didn't have a solution either.

It looks like you are running BIOS version F05, I managed to locate what appears to be a later version of the bios and some other drivers here [http://ftp.compal.com/asp/driver_dnd/e_download.asp?M_path=/Download/NB/NBLB2/BIOS](http://ftp.compal.com/asp/driver_dnd/e_download.asp?M_path=/Download/NB/NBLB2/BIOS)   for the BIOS
and here: [http://ftp.compal.com/asp/driver_dnd/](http://ftp.compal.com/asp/driver_dnd/) for some drivers.  I can't vouch for the viability of those files but it may be that the advanced features are enabled in the F09 version of the BIOS.  

Your CPU does support DEP, but it looks like the feature isn't available in your BIOS.  You could brick the thing trying to flash the bios so do your homework if you choose to proceed with flashing.  Also, if you have been using the TPM function be sure to make an unencrypted backup of your data before flashing as the TPM chip will be cleared in the process.

You could ignore the warning and run with DEP disabled too.

---

### Post by CharlesA on 2011-01-30
I'd suggest contacting the manufacturer of the notebook and asking them about it.

If it's the one I am thinking of, their site is here: [http://www.sagernotebook.com/index.php?page=support](http://www.sagernotebook.com/index.php?page=support)

---

### Post by Jive Turkey on 2011-01-30
Try checking to see what's going on with DEP in windows 7 like in this screenshot (reference: [http://windows.microsoft.com/en-US/windows-vista/Change-Data-Execution-Prevention-settings](http://windows.microsoft.com/en-US/windows-vista/Change-Data-Execution-Prevention-settings))

Lastly, if the output of ```
:~$ grep ^flags /proc/cpuinfo | head -n1 | egrep --color=auto ' (pae|nx)          '
```
looks like this:```

flags           : fpu vme de pse tsc msr [COLOR="Red"]pae[/COLOR] mce cx8 apic sep mtrr pge mca cmov          pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall [COLOR="red"]nx[/COLOR] lm constant         _tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx          est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts tpr_shadow vnmi flexpriority
``` you should be able to disable the checking of the features outlined here: [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures) (assuming you can enable it in windows).

---

### Post by tigerking615 on 2011-01-30
Okay, I ran the grep in Ubuntu and pae is there, but nx is not. In Windows, the "Turn on DEP" button is selected but at the bottom it says "Your computer's processor does not support hardware-based DEP, but Windows can use DEP software to prevent some DEP attacks;" the first part doesn't make sense since the computer is less than a year old and has an i7 processor.

I'll call them tomorrow and ask about it; otherwise, I'll probably end up ignoring that warning rather than try to flash my bios which I know nothing about.

---

### Post by Jive Turkey on 2011-01-31
It looks like a serious issue with the InsydeH20 BIOS, it looks like one guy found a way around it on the lenovo forums here: [http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/s10-2-no-NX-bit/m-p/174434](http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/s10-2-no-NX-bit/m-p/174434)

...and then it was fixed by a bios update offered from Lenovo.  I would bug Sager until they provide an updated/fixed bios if I were you.

---


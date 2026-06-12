---
title: "this stupid dimming thing"
date: 2008-02-03
forum: System76 Support
---

### Post by fuscia on 2008-02-03
i've had some problems with my laptop dimming on me. it's hard to tell when it occurs, except for when i boot up. when i boot up, the intel logo comes on nice and brightly, then there's the beginning of the boot up gibberish and then it instantly dims at the same place, every time. i've had various screwball theories which i've mentioned before in other threads, but they were too #$^@ing stupid to regurgitate. i have a system76 pangolin laptop with xubuntu installed. someone please help/shoot me.

---

### Post by bufsabre666 on 2008-02-03
well i can really only see two differnt causes, 1) the screen plug is loose, or 2) the backlight is going

ive had both happen to me in the past =(

---

### Post by p_quarles on 2008-02-03
Moved to System76 Support, since there are a few reps from the company active here.

fuscia, if you'd rather this be in the hardware & laptops section, just let me know.

---

### Post by fuscia on 2008-02-03
well, as silly as it seems, it seems to be a lighting issue. the laptop is dim when i have a power saving lightbulb in the lamp, it fluctuates in outdoor lighting and it's fine with traditional overhead lighting. if this is the problem, how can i get the laptop to act as if every condition is traditional overhead lighting?

---

### Post by steveneddy on 2008-02-03
> **fuscia said:**
> someone please help/shoot me.

I vote for shooting.

Any luck covering up the light sensor? if there is such a thing?

---

### Post by fuscia on 2008-02-03
> **steveneddy said:**
> I vote for shooting.

Any luck covering up the light sensor? if there is such a thing?

light sensor?

so, when i dim the overhead light in the room, my screen gets dimmer. wtf is that?

---

### Post by fuscia on 2008-02-03
hold everything! wtf is this stupid little piece of crap??? (see attached pic) when i cover it up, the screen dims. if there's no light, shouldn't covering that thing up make the screen a blinding beacon? (good question there, steve.)

---

### Post by Anduu on 2008-02-04
Seems to me its a power saving feature...if you are in a dark room the backlight doesn't need to be so intense...

Maybe check for a setting in your bios for the sensor.

---

### Post by fuscia on 2008-02-04
> **Anduu said:**
> Seems to me its a power saving feature...if you are in a dark room the backlight doesn't need to be so intense...

Maybe check for a setting in your bios for the sensor.

what is a bios? (i'm just a humble end user.)

---

### Post by compholio on 2008-02-04
> **fuscia said:**
> what is a bios? (i'm just a humble end user.)

The BIOS is a special place for settings before you get to the operating system.  When you first turn on your computer there's usually a message like "Press <X> to Enter Setup" where <X> is usually one of the following keys:
Delete
Escape
F2
F10

---

### Post by thomasaaron on 2008-02-04
Fuscia,

First, the pic you posted... Is that a Pangolin? None of my shop pangolins have that. It looks like a lid latch, though. What is the model number on the bottom of the computer.

Second, there are a number of things that could be causing dimming. A loose a/c adapter might be fooling the computer into thinking it is switching to battery power, which could cause it to dim. It could also be a power management setting.

I'm not familiar with Xubuntu's power management, as we don't support Xubuntu, but in Gnome, it is located under System>Preferences> Power Management.

If covering that thing in the pic causes the screen to dim, it is DEFINITELY not a light sensor. It may be that jiggling the lcd is causing the problem, which might indicate a loose connection.

If that is a system76 computer, you can email me with your order#/name and we can work on it further.

---

### Post by tvrusso on 2008-02-04
The thumbnail Fuscia posted  looks suspiciously like the Asustek Z7100VP I have from a different  linux laptop vendor.  It does have a light sensor in that position (although on *mine* it does absolutely nothing).

Did System 76 ever sell that model of Asus laptop?  It's got a high res display and I recall reading in the post archives that some older models of System 76 laptops that are no longer available used to have a display of a similarly high resolution.

---

### Post by fuscia on 2008-02-04
thanks, thomas. i just sent an email to [email]support@system76.com[/email], attention you. in case it doesn't get to you, this is the meat of the email...

"my pangolin was purchased just before dapper came out. the model
number is z7100v61n0ag001674. that 'thing' in the picture i posted at
ubuntu forums (see attached pic) is not the lid latch. it's a glassy
looking piece of plastic that includes the microphone and what must be
a light sensor. when i cover it up, without making physical contact,
my screen dims. as soon as i uncover it, the brightness returns,
depending on the brightness of the room. there are too many consistent
instances of my screen dimming to be any kind of mechanical failure
(ie. it always dims at the same place in the boot up process, changing
the lighting in the room has a consistant effect, covering up the
suspected light sensor has a consistent effect). as this dimming
occurs almost immediately after booting up, i'm thinking DE choice has
little to do with it."

thanks

---

### Post by fuscia on 2008-02-04
> **tvrusso said:**
> Did System 76 ever sell that model of Asus laptop?  It's got a high res display and I recall reading in the post archives that some older models of System 76 laptops that are no longer available used to have a display of a similarly high resolution.

yes, this screen (when lit) is beautiful. it's the best thing about it.

---

### Post by fuscia on 2008-02-04
according to the user's manual (which i had forgotten about), it is indeed a light sensor.

---

### Post by thomasaaron on 2008-02-04
Indeed it is!

I sent you an email on this, but I'll post it on the forum for the benefit of others in the community.

What version of Ubuntu are you using? Gutsy? Point being: did this happen after upgrading? Can you try a previous kernel to see if the problem occurs there?

---

### Post by fuscia on 2008-02-04
> **thomasaaron said:**
> What version of Ubuntu are you using? Gutsy? Point being: did this happen after upgrading?

i don't recall it ever happening before gutsy.

> Can you try a previous kernel to see if the problem occurs there?

hahaha! that's well beyond me. my feeling is not that this is a problem, but a feature i don't want.

---

### Post by tvrusso on 2008-02-04
Since clearly System 76 once sold Pangolins which were based on this machine, and I have one from another vendor, the question I have is "Would installing System76's driver set on my non-System76 asus Z71000VP make anything work that wouldn't work out of the box with Gutsy?"  My daughter's laptop is a System76  (a newer vintage Pangolin, bought in November 2007), but mine was purchased long before I'd heard of System76.  That other vendor sold laptops with Linux installed, but as far as I can tell had no custom drivers at all.

---

### Post by tvrusso on 2008-02-04
Oh yeah, one other thing.  There's an Fn key that is supposed to disable the light sensor.  Since on my Asus Z71000 the light sensor does nothing, I had forgotten about it, but  since your light sensor works perhaps your "disable light sensor" key works, too.  I am not near my laptop, but as I recall it's on the same row of keys with the "Switch to external monitor" "dim screen" "brighten screen" etc. buttons, and looks like a rectangle with a squiggly line in it (a mountain seen through  a window, perhaps?).

---

### Post by thomasaaron on 2008-02-04
If it doesn't work, post the output of...

lsmod

...and maybe we can isolate which module controls it and disable it.

---

### Post by fuscia on 2008-02-04
> **thomasaaron said:**
> If it doesn't work, post the output of...

lsmod

...and maybe we can isolate which module controls it and disable it.

here it is...

Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  4 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  2 parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
pcmcia                 41388  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
ipw2200               149320  0 
snd_seq_oss            33152  0 
ieee80211              35656  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
yenta_socket           27532  2 
nvidia               6221648  26 
rsrc_nonstatic         14080  1 yenta_socket
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  4224  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
psmouse                39952  0 
i2c_core               26112  1 nvidia
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
intel_agp              25620  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  2 nvidia,intel_agp
evdev                  11136  2 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
skge                   43152  0 
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by thomasaaron on 2008-02-04
I looked at all those modules. I'm not seeing one that controls the ambient light sensor. However, Ubuntu community documentation says there is a setting in System>Preferences>Power Management that will disable it. Have you looked yet for the equivalent in Xubuntu?


Also, this is a *similar bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/137598](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/137598)
It suggests that you turn off all screen dimming functionality. Give that a try.

If none of this works, please describe your power management settings in Xubuntu. If you do not have them, this thread...
[http://ubuntuforums.org/showthread.php?t=344311](http://ubuntuforums.org/showthread.php?t=344311)
...suggests that you can install gnome-power-manager and control your screen-dimming features like so:
> 
Just

sudo apt-get install gnome-power-manager

Then add it to your Settings > Autostarted Applications as command "gnome-power-manager"

You can access the configuration file by typing

gnome-power-preferences

---

### Post by fuscia on 2008-02-05
thanks for your response, tom. unfortunately, it's looking like this is a matter of toggling the light sensor on/off. there were no options in gnome-power-manager that had any effect on the problem. as i have been beginning to understand the problem further, i'm realizing that the light sensor is active by default and one needs to make some extra steps to get fn+f3 functioning so that one can turn off the light sensor. it seems an "lssw" file is not present in /proc/acpi/asus. with a value of 0, in this file, the light sensor would be deactivated. (i don't really understand what i've just said. i pieced it together from various things i've read and also failed to understand.)

---

### Post by thomasaaron on 2008-02-05
Hmmm. Well, I don't know if you are correct or not, to be honest. But you can't create the kind of file you are talking about in /proc/acpi/asus. It is a protected directory and you can't write to it, even with sudo.

So, let's try another route. Run this from a command line:
sudo dmidecode

Somewhere in there, we should have some info on your ambient light sensor. Maybe a model number or manufacturer name. Then we can try googling something line: Gutsy <model of ambient sensor> broken

---

### Post by fuscia on 2008-02-05
> **thomasaaron said:**
> Hmmm. Well, I don't know if you are correct or not, to be honest. But you can't create the kind of file you are talking about in /proc/acpi/asus. It is a protected directory and you can't write to it, even with sudo.

i came across this site which gave me the impression that it was possible - [http://www.resonance.org/~josh/laptop.html](http://www.resonance.org/~josh/laptop.html) 
it is for another asus model, though. mine appears to be the a6u.

"Patch to asus_acpi module
I added some code to the asus_acpi module to support the Z71V hardware (the ACPI model identified is M7V). This patch adds support for the M7V model, including toggling the light sensor, setting its level, and switching the display between LCD and CRT (thanks to James Lademann for adding display switching support).

Go to the File Downloads section of this page for the M7V patches.

This patch adds the files "lssw" and "lslvl" to /proc/acpi/asus. Sending a 0 to lssw will disable the light sensor any other value will enable it. A value from 0 to 15 can be sent to lslvl to control the light sensor level.

UPDATE: The M7V patch has been merged with the acpi4asus project CVS. This means that future versions of acpi4asus, and eventually the Linux kernel, will contain support for the M7V model, making patching unnecessary. As of now (acpi4asus version 0.30 and Linux kernel 2.6.16) it is still necessary to patch things." 

So, let's try another route. Run this from a command line:
sudo dmidecode

Somewhere in there, we should have some info on your ambient light sensor. Maybe a model number or manufacturer name. Then we can try googling something line: Gutsy <model of ambient sensor> broken[/QUOTE]

output of *sudo dmidecode*


# dmidecode 2.9
SMBIOS 2.3 present.
37 structures occupying 1399 bytes.
Table at 0x000F96F0.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: American Megatrends Inc.
        Version: 0210                               
        Release Date: 08/31/2005
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 512 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/360 KB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
        Manufacturer: ASUSTeK Computer Inc.        
        Product Name: M7V       
        Version: 1.0       
        Serial Number: SSN12345678901234567
        UUID: 28CE5D8A-0000-0080-385D-0015F292F865
        Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
        Manufacturer: ASUSTeK Computer Inc.        
        Product Name: M7V       
        Version: 1.0       
        Serial Number: BSN12345678901234567

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
        Manufacturer: ASUSTeK Computer Inc.        
        Type: Notebook
        Lock: Present
        Version: 1.0       
        Serial Number: CSN12345678901234567
        Asset Tag: ATN12345678901234567
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Other
        Security Status: Other
        OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
        Socket Designation: Socket 478
        Type: Central Processor
        Family: Pentium M
        Manufacturer: Intel            
        ID: D8 06 00 00 FF FB E9 AF
        Signature: Type 0, Family 6, Model 13, Stepping 8
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
                CLFSH (CLFLUSH instruction supported)
                DS (Debug store)
                ACPI (ACPI supported)
                MMX (MMX technology supported)
                FXSR (Fast floating-point save and restore)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                SS (Self-snoop)
                TM (Thermal monitor supported)
                PBE (Pending break enabled)
        Version: Intel(R) Celeron(R) M processor         1.60GHz     
        Voltage: 1.5 V
        External Clock: 100 MHz
        Max Speed: 1600 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: Socket 478
        L1 Cache Handle: 0x0005
        L2 Cache Handle: 0x0006
        L3 Cache Handle: Not Provided
        Serial Number: PSN12345678901234567
        Asset Tag: PATN1234567890123456
        Part Number: PPN12345678901234567

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1-Cache
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Varies With Memory Address
        Location: Internal
        Installed Size: 32 KB
        Maximum Size: 32 KB
        Supported SRAM Types:
                Pipeline Burst
        Installed SRAM Type: Pipeline Burst
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2-cache
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Varies With Memory Address
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Pipeline Burst
        Installed SRAM Type: Pipeline Burst
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Unified
        Associativity: 4-way Set-associative

Handle 0x0007, DMI type 5, 20 bytes
Memory Controller Information
        Error Detecting Method: None
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 1024 MB
        Maximum Total Memory Size: 2048 MB
        Supported Speeds:
                Other
                70 ns
                60 ns
                50 ns
        Supported Memory Types:
                Standard
                DIMM
                SDRAM
        Memory Module Voltage: 3.3 V
        Associated Memory Slots: 2
                0x0008
                0x0009
        Enabled Error Correcting Capabilities:
                None

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM1
        Bank Connections: 0 1
        Current Speed: 10 ns
        Type: Standard DIMM SDRAM
        Installed Size: 1024 MB (Double-bank Connection)
        Enabled Size: 1024 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM2
        Bank Connections: 2 3
        Current Speed: 10 ns
        Type: Standard DIMM SDRAM
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON11
        Internal Connector Type: None
        External Reference Designator: USB1
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON11
        Internal Connector Type: None
        External Reference Designator: USB2
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON12
        Internal Connector Type: None
        External Reference Designator: USB3
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON12
        Internal Connector Type: None
        External Reference Designator: USB4
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON16
        Internal Connector Type: None
        External Reference Designator: USB5
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: BCON1
        Internal Connector Type: None
        External Reference Designator: 1394
        External Connector Type: IEEE 1394
        Port Type: Firewire (IEEE P1394)

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON14
        Internal Connector Type: None
        External Reference Designator: MODEM
        External Connector Type: RJ-11
        Port Type: Modem Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON13
        Internal Connector Type: None
        External Reference Designator: LAN
        External Connector Type: RJ-45
        Port Type: Network Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON25
        Internal Connector Type: None
        External Reference Designator: Audio Line In
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON26
        Internal Connector Type: None
        External Reference Designator: Audio Line Out
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON10
        Internal Connector Type: None
        External Reference Designator: Video
        External Connector Type: DB-15 female
        Port Type: Video Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON3
        Internal Connector Type: None
        External Reference Designator: SD/MS/XD
        External Connector Type: Other
        Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CON6
        Internal Connector Type: None
        External Reference Designator: CARD BUS
        External Connector Type: 68 Pin Dual Inline
        Port Type: Cardbus

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
        Designation: MiniPCI
        Type: 32-bit PCI
        Current Usage: Available
        Length: Long
        ID: 1
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x0018, DMI type 10, 6 bytes
On Board Device Information
        Type: Video
        Status: Enabled
        Description: AGP VGA controller

Handle 0x0019, DMI type 10, 6 bytes
On Board Device Information
        Type: Ethernet
        Status: Enabled
        Description: Ethernet controller

Handle 0x001A, DMI type 10, 6 bytes
On Board Device Information
        Type: Sound
        Status: Enabled
        Description: Audio controller

Handle 0x001B, DMI type 10, 6 bytes
On Board Device Information
        Type: Other
        Status: Enabled
        Description: Modem controller

Handle 0x001C, DMI type 13, 22 bytes
BIOS Language Information
        Installable Languages: 1
                enUS
        Currently Installed Language: enUS

Handle 0x001D, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: Bad Read
        Granularity: Device Level
        Operation: Read
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x001E, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: 0x001D
        Number Of Devices: 2

Handle 0x001F, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000400003FF
        Range Size: 1048577 kB
        Physical Array Handle: 0x001E
        Partition Width: 0

Handle 0x0020, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001E
        Error Information Handle: 0x001D
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM1
        Bank Locator: BANK0
        Type: SDRAM
        Type Detail: Synchronous
        Speed: Unknown
        Manufacturer: Manufacturer1
        Serial Number: SerNum1
        Asset Tag: AssetTagNum1
        Part Number: PartNum1

Handle 0x0021, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 1 GB
        Physical Device Handle: 0x0020
        Memory Array Mapped Address Handle: 0x001F
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x0022, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001E
        Error Information Handle: 0x001D
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: DIMM2
        Bank Locator: BANK1
        Type: Unknown
        Type Detail: Unknown
        Speed: Unknown
        Manufacturer: Manufacturer2
        Serial Number: SerNum2
        Asset Tag: AssetTagNum2
        Part Number: PartNum2

Handle 0x0023, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000000003FF
        Range Size: 1 kB
        Physical Device Handle: 0x0022
        Memory Array Mapped Address Handle: 0x001F
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x0024, DMI type 127, 4 bytes

---

### Post by thomasaaron on 2008-02-05
It is a kernel module patch that adds those files, though. It is not done manually.

Can you also please post the output of the following three commands:

```
ls /proc/acpi/asus
```
```
lspci
```
```
lsusb

```

---

### Post by fuscia on 2008-02-05
ls /proc/acpi/asus

*brn  disp  info  lcd  mled  wled*


lspci

[i]00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
03:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
03:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)[/i]


lsusb

[I]Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
[/I]

---

### Post by thomasaaron on 2008-02-06
OK, so I've looked at everything you've given me, and I'm not seeing the device!

Have you tried going into your BIOS menu and seeing if there is a way to turn it off? To go into the BIOS you should hit a key when you see the manufacturer's splash page. The key will **probably** be the Esc, F2 or Del key. 

Once you get to the BIOS menu, you will want to tab through the different categories throroughly and look for something like "Ambient Light Sensor".  If you find it, there should be an option to enable/disable it.

There's no guarantee it's in there. But the alternative is moving back to a previous version of Ubuntu. Speaking of which, if you hit your escape key when you see the little countdown "Grub...3....2...1" when booting, you should be presented with a boot menu. What options are on that menu?

---

### Post by fuscia on 2008-02-06
getting into the bios was the trick, tom. there was an option to disable dimming (who tf would want to dim their screen? i don't get that). all it nice and bright and shiny now. thanks very much for all your patient help. phew!

:guitar::guitar::guitar:

---

### Post by dicecca112 on 2008-02-06
> **fuscia said:**
> getting into the bios was the trick, tom. there was an option to disable dimming (who tf would want to dim their screen? i don't get that). all it nice and bright and shiny now. thanks very much for all your patient help. phew!
 
:guitar::guitar::guitar:
 
it would save the battery.  I have mine dimmed when on battery, full brightness when on Ac

---

### Post by thomasaaron on 2008-02-06
And a "Thank You" goes out to Anduu on that one. He mentioned that earlier too. Think of how many pages of posts we would've saved if only...

---

### Post by tvrusso on 2008-02-06
It's funny, Fuscia:  you question why anyone would want their laptop to dim, and I used this thread to figure out how to get *my* Asus Z7100VP to do what yours did, because I've been wanting that ambient light sensor to work ever since I bought the laptop. From following this thread and a little googling, I figured it out.

For whatever reason, when *my* laptop booted it loaded the "asus_acpi" module, which does not support the light sensor.  That module has apparently become deprecated and replaced by the "asus_laptop" module.  I don't know why asus_acpi was being loaded, but by adding asus_acpi to /etc/modprobe.d/blacklist and adding asus_laptop to /etc/modules I forced the issue.  Now I get the screen dimming when the ambient light drops.

I want that, because if I'm working in a darkened room I want the screen to be less bright so it isn't so glaring, but if the lights come on I want it to brighten up so I can see it better.  I use my laptop in low ambient light a lot, and having it very bright in that environment is unpleasant to me and hurts my eyes.

The Fn-F3 key still doesn't disable the light sensor for me, but I'm not so concerned with that as you are.  I'll keep in mind that there's a BIOS option to turn it off, and I'll also remember that I can always undo the /etc/modules and /etc/modprobe.d/blacklist changes to revert to my old behavior (which existed because the Z7100VP's ACPI isn't supported fully by the older module).

Perhaps by blaclkisting asus_laptop and forcing asus_acpi on *your* system you could get the opposite effect that you want?  But asus_acpi is supposed to be phased out, so it's not a long term solution.

---

### Post by fuscia on 2008-02-07
> **tvrusso said:**
> II want that, because if I'm working in a darkened room I want the screen to be less bright so it isn't so glaring, but if the lights come on I want it to brighten up so I can see it better.  I use my laptop in low ambient light a lot, and having it very bright in that environment is unpleasant to me and hurts my eyes.

i use mine in the dark, at times. certainly a matter of preference here. i have absolutely no feel for your preference. i guess we must be at opposite ends of that spectrum. glad it worked out for you, though.

---

### Post by lavinog on 2008-06-09
I found this in the gconf-editor:
```

Key name: /apps/gnome-power-manager/ambient/enable
Key owner: /apps/gnome-power-manager/ambient/enable

Short Description: Change the brightness automatically using the ambient light sensors.
Long Description: If the screen brightness should be changed automatically using the ambient light sensors.

```
This may be how you should turn off the autodim

---


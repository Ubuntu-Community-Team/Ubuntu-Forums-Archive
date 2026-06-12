---
title: "ubuntu usb stick does not boot on netbook"
date: 2013-11-20
forum: System76 Support
---

### Post by jsusanka on 2013-11-20
I have a system 76 netbook and trying to boot 11.10 via a usb stick I made from a downloaded iso using the ubuntu startup disk created on the ubuntu LTS version.

 when I boot to the usb drive it fails after showing ubuntu and the dots underneath and takes me to a busy box prompt telling to type init = boot args

 would like to run the latest ubuntu on this netbook so any help would be appreciated. 

Everytime I need to reinstall the os on this computer I have to start with 10.04 since that is the only distro that will boot from a usb key. 

It is a star1 and I am using the 32 bit ubuntu.  

Is there a kernel module missing or is there some way I can manually make the usb stick boot on this netbook?  

I would like to do a clean install every now and then and would like to use a usb stick since that is the most economical and environmental friendly.

---

### Post by sudodus on 2013-11-20
It is hard for me to think that you have to start with 10.04 since that is the only distro that will boot from a usb key. But I don't know the details about the computer.

You already gave us the brand name: System 76 netbook. Please add also

- model (Star 1?)
- cpu
- ram (size)
- graphics chip/card

How did you make the USB stick? See this link for tips about several methods and tools

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by jsusanka on 2013-11-20
I have made the stick from the ubuntu startup disk creator. 

I have tried numerous sticks and all have worked on other computers but when I try this netbook I get the same result except for version 10.04

cpu is an intel atom dual core. 
 cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 28
model name      : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping        : 2
microcode       : 0x208
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm dtherm
bogomips        : 3192.08
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 32 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 28
model name      : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping        : 2
microcode       : 0x208
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm dtherm
bogomips        : 3192.08
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 32 bits virtual
power management:
2 gig of ram 
intel graphics VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)

Starling NetBook ( star1 ) 
 
# dmidecode 2.12
SMBIOS 2.4 present.
31 structures occupying 1501 bytes.
Table at 0x000E91E0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: INSYDE
        Version: Q3F21
        Release Date: 05/19/2009
        ROM Size: 1024 kB
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
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: Quanta
        Product Name: UW1
        Version: 04
        Serial Number: UW1TFCTM09294539
        UUID: 7F5BB985-44CA-532E-5B2D-A2CB2F7F6B31
        Wake-up Type: Power Switch
        SKU Number: Napa_Fab5
        Family: Intel_Mobile
                PAT (Page attribute table)
                CLFSH (CLFLUSH instruction supported)
                DS (Debug store)
                ACPI (ACPI supported)
                MMX (MMX technology supported)
                FXSR (FXSAVE and FXSTOR instructions supported)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                SS (Self-snoop)
                HTT (Multi-threading)
                TM (Thermal monitor supported)
                PBE (Pending break enabled)
        Version: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
        Voltage: 1.6 V
        External Clock: 533 MHz
        Max Speed: 1600 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: Socket 478
        L1 Cache Handle: 0x001D
        L2 Cache Handle: 0x001C
        L3 Cache Handle: Not Provided
        Serial Number: Not Specified
        Asset Tag: FFFF
        Part Number: Not Specified

Handle 0x001C, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 512 kB
        Maximum Size: 512 kB
        Supported SRAM Types:
                Synchronous
        Installed SRAM Type: Synchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Unified
        Associativity: 8-way Set-associative

Handle 0x001D, DMI type 7, 19 bytes
Cache Information
        Socket Designation: Unknown
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 32 kB
        Maximum Size: 32 kB
        Supported SRAM Types:
                Synchronous
        Installed SRAM Type: Synchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Instruction
        Associativity: 8-way Set-associative

Handle 0x001E, DMI type 127, 4 bytes
End Of Table

---

### Post by sudodus on 2013-11-20
atom cpu
2 gig of ram 
intel graphics VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)

This should be OK with newer versions of Ubuntu flavours. It is possible that standard Ubuntu with Unity needs more horsepower, but Xubuntu 12.04 LTS or the newest Lubuntu or Xubuntu, 13.10, should work.

Sometimes a particular stick does not cooperate with a particular computer (or USB hardware/firmware). Have you tried to install another version into the USB stick, which works with Ubuntu 10.04 LTS? Try for example Xubuntu 12.04 LTS (32 bit alias i386) in that same stick :-)

See also this link [Ubuntu Wiki - FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

With 2 GB ram there should be no problem to run live from the desktop iso (installed to that USB stick). Do not try to make a persistent drive at this moment. If you still have problems, it might work better if you clone the iso file using mkusb described in this link [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by jsusanka on 2013-12-02
Still have this problem tried xubuntu, ubuntu, kubuntu, gnome-ubuntu all versions take me to the busy box prompt after showing the logo for a few seconds.  

I tried fedora and centos and both work fine and I can run the live desktop off the usb stick.  I have tried three different usb sticks and have tried numerous ways of making the usb stick and every time I get the same result. 

It is funny the version of the Linux this laptop shipped with does not work but other versions that the laptops don't ship with work fine.

---

### Post by sudodus on 2013-12-03
Which versions did you try? 12.04 LTS, 12.10,  13.04 or 13.10? I think you should try both 12.04 LTS and 13.10.

Did you try any boot option? See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You might have problems with the wifi. Can it be switched off (with a mechanical switch or a setting in a bios menu)?

But sometimes there just isn't good matching between the hardware and software, so try some other software.

Finally, did you ask System 76 for help? There should be support for their product also after the end of life of the  original version of the operating system.

---

### Post by jsusanka on 2013-12-04
Okay I have finally solved this. 

I had a SD card in the card reader slot that I use to back stuff up on and when that is in the slot the usb stick does not boot and goes to the busy box prompt.  When I take this card out the usb stick boots normally and it installs and runs without a problem. 

Weird stuff - wonder why Fedora, and Centos worked when that card was in the slot.  Thanks for the help sometimes it just helps typing this stuff out to figure things out.

---

### Post by sudodus on 2013-12-04
I agree it is weird, and I have learned that there is another question to be asked when trouble-shooting problems with booting: '*Remove other USB devices, they might confuse the system*'.

I have seen systems that can tell different USB mass storage devices apart at boot, and let you select among them, and I have seen systems that see only one of the USB devices (and there is no obvious reason why that one is selected).

Thanks for sharing your solution :-)

---


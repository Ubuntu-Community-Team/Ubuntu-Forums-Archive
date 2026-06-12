---
title: "Installing Ubuntu in a ULTRA 45"
date: 2007-09-20
forum: Sun Sparc Users
---

### Post by djcrash1981 on 2007-09-20
Ok, where's the trouble:
I've been trying to install Ubuntu recently in a brand new Ultra 45 Sparc Station, I've tried to install it in diferents ways al each of one gives me diferent kind of errors which are:
[LIST]Cold boot (giving a stop-a interrupt at the begining) installing Ubuntu 6.04 dapper drake:
[LIST]
[*]It runs fine but right after it start loading the kernel it sends the next message:
[B]Neither SBUS nor PCI found.
Program terminated[/B]
[/LIST]
[/LIST]
[LIST] Cold boot (giving a stop-a interrupt at the begining) installing Ubuntu 7.04 Feisty fawn:
It starts the installation process and it just hangs in the part of booting linux. [/LIST]
[LIST]Normal boot, init 0, prompt ok, installing Ubuntu 7.04 Feisty Fawn: 
Allocated 8 megs of memory
Loaded kernel version 2.6.20
Loading initial ramdisk
**ERROR: Last trap: Illegal Instruction**
The same happends for the Dapper Drake install.
[/LIST]

The version of the OpenBoot is *4.22.19*

What can i do????

Thanks in advance for the help.

---

### Post by djcrash1981 on 2007-09-20
Here are some of the specs of the Workstation:
System Configuration: Sun Microsystems  sun4u Sun Ultra 45 Workstation
System clock frequency: 200 MHZ
Memory size: 1GB        

========= CPUs ==============
               E$          CPU                    CPU
CPU  Freq      Size        Implementation         Mask    Status      Location
---  --------  ----------  ---------------------  -----   ------      --------
0    1600 MHz  1MB         SUNW,UltraSPARC-IIIi    3.4    on-line     MB/0

========= IO Devices===========
Bus     Freq  Slot +      Name +
Type    MHz   Status      Path                          Model
------  ----  ----------  ----------------------------  --------------------
pci     200   MB          pci10b9,5455 (sound)                             
              okay        /pci@1e,600000/pci@0/pci@1/pci@0/sound

pci     200   MB          pci10b9,5229 (ide)                               
              okay        /pci@1e,600000/pci@0/pci@1/pci@0/ide

pci     200   MB          pci14e4,1678 (network)                           
              okay        /pci@1e,600000/pci@0/pci@2/pci@0/network@4

pci     200   MB          pci14e4,1678 (network)                           
              okay        /pci@1e,600000/pci@0/pci@2/pci@0/network

pci     200   MB          scsi-pci1000,50 (scsi-2)      LSI,1064           
              okay        /pci@1e,600000/pci@0/pci@9/pci@0/scsi@1

pciex   200   MB/PCIE2    SUNW,XVR-300 (display)        SUNW,375-3458      
              okay        /pci@1f,700000/SUNW,XVR-300@0


========= Memory Configuration =========
Segment Table:
-----------------------------------------------------------------------
Base Address       Size       Interleave Factor  Contains
-----------------------------------------------------------------------
0x200000000        1GB               1           BankIDs 0

Bank Table:
-----------------------------------------------------------
           Physical Location
ID       ControllerID  GroupID   Size       Interleave Way
-----------------------------------------------------------
0        0             1         1GB             0

Memory Module Groups:
--------------------------------------------------
ControllerID   GroupID  Labels         Status
--------------------------------------------------
0              1        MB/DIMM2       
0              1        MB/DIMM0       

========= usb Devices =========

Name          Port#
------------  -----
mouse           1
hub             2

========= hub#2 Devices =========

Name          Port#
------------  -----
keyboard        4

========= usb Devices =========

Name          Port#
------------  -----
hub             7

========= Environmental Status =========
Fan Status:
-------------------------------------------
Location             Sensor          Status
-------------------------------------------
F0                   cpu0-fan        okay
F2                   pci-fan         okay
F3                   system-fan3     okay
F4                   system-fan4     okay

Temperature sensors:
-----------------------------------------
Location       Sensor              Status
-----------------------------------------
MB/0           cpu0-sensor         okay 
MB             mb-sensor           okay 
MB             adt7462-sensor      okay 
MB             lm95221-sensor      okay 
MB             fire-sensor         okay 
MB             lsi1064-sensor      okay 
FIOB           front_panel-sensor  okay 
MB             psu-sensor          okay 

========= HW Revisions =========
ASIC Revisions:
-------------------------------------------------------------------
Path                   Device           Status             Revision
-------------------------------------------------------------------
/pci@1e,600000         pciex108e,80f0   okay               3   
/pci@1f,700000         pciex108e,80f0   okay               3   

System PROM revisions:
----------------------
OBP 4.22.19 2006/09/06 23:42 Sun Ultra 45 Workstation
POST 4.22.19 2006/09/07 00:06

Please, help me :'(

---

### Post by jfrogg10 on 2007-09-27
I've been struggling with pretty much the same thing on my Ultra25 for a little while, but I think I found the problem.  The whole thing has been a real PITA.

Basically, the frame buffer support in the kernel (maybe it's the Radeon driver?) is screwing up.  "boot net -p forcepromconsole" didn't make it work either.  But... I was able to build a sparc64 kernel without frame buffer support, and it finally boots!  I just built a custom debian netboot installer based on my kernel, and was actually able to install debian on my Ultra25.

So, you probably need to either build your own ubuntu installer with a custom kernel.  If you're interested trying out debian using my custom netboot installer, just send me a message and let me know where to upload it.

---


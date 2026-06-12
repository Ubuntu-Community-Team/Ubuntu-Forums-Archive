---
title: "smart-notifier not run prioritary on startup"
date: 2017-09-08
forum: Ubuntu/Debian BASED
---

### Post by henrique-rj on 2017-09-08
Hi

I suspect smart-notifier run after smartd after reboot my system.

When I put " -M test " in /etc/smartd.conf and reboot the system ( in inicialization ) the popup alert test not show in my desktop ( this is so after reinstallation smartmontools and smart-notifier two or three times ).

Any idea to run smart-notifier before the smartd when startup the system ?

Thanks

---

### Post by henrique-rj on 2017-09-09
someone ?

---

### Post by henrique-rj on 2017-09-11
I modified boot sequence of smartmontools and the popup alert test of smart-notifier yet not show.

I do not know yet why the popup alert test does not appear in boot system.

.

---

### Post by vasa1 on 2017-09-11
You can tell people more about your system by installing *inxi* and posting the output of```
inxi -Fxzc0
```here.

---

### Post by henrique-rj on 2017-09-11
Computer
********


Summary
-------

-Computer-
Processor        : AMD Processor model unknown
Memory        : 1983MB (829MB used)
Operating System        : Kaiana 14.04 (Trusty)
User Name        : henrique (Henrique)
Date/Time        : Seg 11 Set 2017 09:01:16 BRT
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : VIA8237 - VIA 8237
-Input Devices-
 Power Button
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 ImPS/2 Generic Wheel Mouse
-Printers (CUPS)-
Canon_BJC-240
Canon_MG3600_series
-SCSI Disks-
ATA Maxtor 6L080L0
HL-DT-ST DVD-RAM GH22NP20

Operating System
----------------

-Version-
Kernel        : Linux 3.13.0-129-generic (x86_64)
Compiled        : #178-Ubuntu SMP Fri Aug 11 12:48:20 UTC 2017
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
Distribution        : Kaiana 14.04 (Trusty)
-Current Session-
Computer Name        : henrique-desktop
User Name        : henrique (Henrique)
Home Directory        : /home/henrique
-Misc-
Uptime        : 1 hour, 36 minutes
Load Average        : 0.51, 0.49, 0.43

Kernel Modules
--------------

-Loaded Modules-
zram        : Compressed RAM Block Device
snd_via82xx        : VIA VT82xx audio
snd_mpu401_uart        : Routines for control of MPU-401 in UART mode
snd_ac97_codec        : Universal interface for Audio Codec &apos;97
ac97_bus
gameport        : Generic gameport layer
snd_pcm        : Midlevel PCM code for ALSA.
snd_page_alloc        : Memory allocator for ALSA system.
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_seq_device        : ALSA sequencer device management
snd_timer        : ALSA timer interface
rfcomm        : Bluetooth RFCOMM ver 1.11
snd        : Advanced Linux Sound Architecture driver for soundcards.
bnep        : Bluetooth BNEP ver 1.3
bluetooth        : Bluetooth Core ver 2.17
serio_raw        : Raw serio driver
edac_core        : Core library routines for EDAC reporting
k8temp        : AMD K8 core temperature monitor
edac_mce_amd        : AMD MCE decoder
binfmt_misc
soundcore        : Core sound module
i2c_viapro        : vt82c596 SMBus driver
shpchp        : Standard Hot Plug PCI Controller Driver
mac_hid
parport_pc        : PC-style parallel port driver
ppdev
it87        : IT8705F/IT871xF/IT872xF hardware monitoring driver
hwmon_vid        : hwmon-vid driver
lp
parport
btrfs
xor
raid6_pq        : RAID6 Q-syndrome calculations
libcrc32c        : CRC32c (Castagnoli) calculations
hid_generic        : HID generic driver
pata_acpi        : SCSI low-level driver for ATA in ACPI mode
usbhid        : USB HID core driver
hid
psmouse        : PS/2 mouse driver
via_rhine        : VIA Rhine PCI Fast Ethernet driver
mii        : MII hardware support library
pata_via        : low-level driver for VIA PATA
sata_via        : SCSI low-level driver for VIA SATA controllers
floppy

Boots
-----

-Boots-
Mon Sep 11 07:25        : 3.13.0-129-gener|-
Mon Sep 11 07:18        : 3.13.0-129-gener|-
Mon Sep 11 06:09        : 3.13.0-129-gener|-
Mon Sep 11 03:27        : 3.13.0-129-gener|-
Sun Sep 10 17:55        : 3.13.0-129-gener|-
Sun Sep 10 17:12        : 3.13.0-129-gener|-
Sun Sep 10 17:04        : 3.13.0-129-gener|-
Sun Sep 10 16:56        : 3.13.0-129-gener|-
Sun Sep 10 16:37        : 3.13.0-129-gener|-
Sun Sep 10 05:38        : 3.13.0-129-gener|-
Sat Sep 9 07:39        : 3.13.0-129-gener|-
Sat Sep 9 07:26        : 3.13.0-129-gener|-
Fri Sep 8 19:56        : 3.13.0-129-gener|-
Fri Sep 8 09:23        : 3.13.0-129-gener|-
Fri Sep 8 09:20        : 3.13.0-129-gener|-
Fri Sep 8 09:17        : 3.13.0-129-gener|-
Fri Sep 8 09:12        : 3.13.0-129-gener|-
Fri Sep 8 09:09        : 3.13.0-129-gener|-
Fri Sep 8 05:20        : 3.13.0-129-gener|-
Fri Sep 8 05:14        : 3.13.0-129-gener|-
Fri Sep 8 05:04        : 3.13.0-129-gener|-
Thu Sep 7 19:12        : 3.13.0-129-gener|-
Thu Sep 7 19:03        : 3.13.0-129-gener|-
Thu Sep 7 18:20        : 3.13.0-129-gener|-
Thu Sep 7 18:16        : 3.13.0-129-gener|-
Thu Sep 7 18:12        : 3.13.0-129-gener|-
Thu Sep 7 18:06        : 3.13.0-129-gener|-
Thu Sep 7 18:00        : 3.13.0-129-gener|-
Thu Sep 7 17:54        : 3.13.0-129-gener|-
Thu Sep 7 17:50        : 3.13.0-129-gener|-
Thu Sep 7 10:05        : 3.13.0-129-gener|-
Thu Sep 7 08:00        : 3.13.0-129-gener|-
Thu Sep 7 06:28        : 3.13.0-129-gener|-
Wed Sep 6 09:36        : 3.13.0-129-gener|-
Wed Sep 6 05:33        : 3.13.0-129-gener|-
Tue Sep 5 10:34        : 3.13.0-129-gener|-
Tue Sep 5 07:36        : 3.13.0-129-gener|-
Tue Sep 5 07:30        : 3.13.0-129-gener|-
Tue Sep 5 07:24        : 3.13.0-129-gener|-
Tue Sep 5 07:19        : 3.13.0-129-gener|-
Tue Sep 5 06:50        : 3.13.0-129-gener|-
Tue Sep 5 05:41        : 3.13.0-129-gener|-
Tue Sep 5 05:35        : 3.13.0-129-gener|-
Mon Sep 4 23:21        : 3.13.0-129-gener|-
Mon Sep 4 23:17        : 3.13.0-129-gener|-
Mon Sep 4 22:23        : 3.13.0-129-gener|-
Mon Sep 4 21:25        : 3.13.0-129-gener|-
Mon Sep 4 21:18        : 3.13.0-129-gener|-
Mon Sep 4 20:03        : 3.13.0-129-gener|-
Mon Sep 4 19:52        : 3.13.0-129-gener|-
Mon Sep 4 19:41        : 3.13.0-129-gener|-
Mon Sep 4 19:32        : 3.13.0-129-gener|-
Mon Sep 4 19:18        : 3.13.0-129-gener|-
Mon Sep 4 18:50        : 3.13.0-129-gener|-
Mon Sep 4 06:03        : 3.13.0-129-gener|-
Sun Sep 3 06:45        : 3.13.0-129-gener|-
Sun Sep 3 05:27        : 3.13.0-129-gener|-
Sat Sep 2 16:24        : 3.13.0-129-gener|-

Languages
---------

-Available Languages-
en_AG        : English language locale for Antigua and Barbuda
en_AG.utf8        : English language locale for Antigua and Barbuda
en_AU.utf8        : English locale for Australia
en_BW.utf8        : English locale for Botswana
en_CA.utf8        : English locale for Canada
en_DK.utf8        : English locale for Denmark
en_GB.utf8        : English locale for Britain
en_HK.utf8        : English locale for Hong Kong
en_IE.utf8        : English locale for Ireland
en_IN        : English language locale for India
en_IN.utf8        : English language locale for India
en_NG        : English locale for Nigeria
en_NG.utf8        : English locale for Nigeria
en_NZ.utf8        : English locale for New Zealand
en_PH.utf8        : English language locale for Philippines
en_SG.utf8        : English language locale for Singapore
en_US.utf8        : English locale for the USA
en_ZA.utf8        : English locale for South Africa
en_ZM        : English locale for Zambia
en_ZM.utf8        : English locale for Zambia
en_ZW.utf8        : English locale for Zimbabwe
pt_BR.utf8        : Portuguese locale for Brasil
pt_PT.utf8        : Portuguese locale for Portugal

Filesystems
-----------

-Mounted File Systems-
/dev/sda5    /    39.67 % (17.8 GiB of 29.5 GiB)    
none    /sys/fs/cgroup    0.00 % (4.0 KiB of 4.0 KiB)    
udev    /dev    0.00 % (953.1 MiB of 953.1 MiB)    
tmpfs    /run    0.63 % (192.5 MiB of 193.7 MiB)    
none    /run/lock    0.08 % (5.0 MiB of 5.0 MiB)    
none    /run/shm    0.01 % (968.3 MiB of 968.4 MiB)    
none    /run/user    0.02 % (100.0 MiB of 100.0 MiB)    
/dev/sda1    /media/sda1    7.64 % (323.3 MiB of 350.0 MiB)    
/dev/sda2    /media/sda2    43.22 % (25.0 GiB of 44.0 GiB)    
/dev/sda5    /media/sda5    39.67 % (17.8 GiB of 29.5 GiB)    

Display
-------

-Display-
Resolution        : 1024x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.15.1
-Monitors-
Monitor 0        : 1024x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
DRI3
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : VMware, Inc.
Renderer        : Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
Version        : 3.0 Mesa 11.0.4
Direct Rendering        : Yes

Environment Variables
---------------------

-Environment Variables-
KDE_FULL_SESSION        : true
GS_LIB        : /home/henrique/.fonts
GNOME_KEYRING_PID        : 1847
USER        : henrique
LANGUAGE        : pt_BR:pt:en
UPSTART_INSTANCE
XDG_SEAT        : seat0
SESSION        : kde-plasma
SHLVL        : 1
HOME        : /home/henrique
OLDPWD        : /home/henrique
DESKTOP_SESSION        : kde-plasma
GTK_RC_FILES        : /etc/gtk/gtkrc:/home/henrique/.gtkrc:/home/henrique/.kde/share/config/gtkrc
XDG_SEAT_PATH        : /org/freedesktop/DisplayManager/Seat0
KDE_SESSION_VERSION        : 4
KDE_IS_PRELINKED        : 1
INSTANCE
DBUS_SESSION_BUS_ADDRESS        : unix:abstract=/tmp/dbus-dYqqwYaYoJ
GNOME_KEYRING_CONTROL        : /run/user/1000/keyring-R1Vhqi
MANDATORY_PATH        : /usr/share/gconf/kde-plasma.mandatory.path
SESSIONTYPE
UPSTART_JOB        : startkde
LOGNAME        : henrique
_        : /usr/bin/python3
DEFAULTS_PATH        : /usr/share/gconf/kde-plasma.default.path
XDG_SESSION_ID        : c1
GTK2_RC_FILES        : /etc/gtk-2.0/gtkrc:/home/henrique/.gtkrc-2.0:/home/henrique/.kde/share/config/gtkrc-2.0
PATH        : /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
SELINUX_INIT        : YES
SESSION_MANAGER        : local/henrique-desktop:@/tmp/.ICE-unix/2747,unix/henrique-desktop:/tmp/.ICE-unix/2747
GDM_LANG        : pt_BR
XDG_SESSION_PATH        : /org/freedesktop/DisplayManager/Session0
OOO_FORCE_DESKTOP        : gnome
XCURSOR_THEME        : Oxygen_White
XDG_RUNTIME_DIR        : /run/user/1000
DISPLAY        : :0
LANG        : pt_BR.UTF-8
XDG_CURRENT_DESKTOP        : KDE
XAUTHORITY        : /tmp/kde-henrique/xauth-1000-_0
XDG_GREETER_DATA_DIR        : /var/lib/lightdm-data/henrique
SSH_AUTH_SOCK        : /run/user/1000/keyring-R1Vhqi/ssh
SHELL        : /bin/bash
QT_NO_GLIB        : 1
GDMSESSION        : kde-plasma
UPSTART_EVENTS        : started xsession
KDE_MULTIHEAD        : false
GPG_AGENT_INFO        : /tmp/gpg-G01v2J/S.gpg-agent:1872:1
UPSTART_SESSION        : unix:abstract=/com/ubuntu/upstart-session/1000/1752
XDG_VTNR        : 7
PWD        : /usr/share/kcenter
XDG_CONFIG_DIRS        : /etc/xdg/xdg-kde-plasma:/usr/share/upstart/xdg:/etc/xdg
XDG_DATA_DIRS        : /usr/share:/usr/share/kde-plasma:/usr/local/share/:/usr/share/
KDE_SESSION_UID        : 1000
KDE_MALLOC        : 1
QT_PLUGIN_PATH        : /home/henrique/.kde/lib/kde4/plugins/:/usr/lib/kde4/plugins/
JOB        : dbus

Users
-----

-Users-
root        : root
daemon        : daemon
bin        : bin
sys        : sys
sync        : sync
games        : games
man        : man
lp        : lp
mail        : mail
news        : news
uucp        : uucp
proxy        : proxy
www-data        : www-data
backup        : backup
list        : Mailing List Manager
irc        : ircd
gnats        : Gnats Bug-Reporting System (admin)
nobody        : nobody
libuuid
syslog
messagebus
avahi-autoipd        : Avahi autoip daemon
usbmux        : usbmux daemon
dnsmasq        : dnsmasq
pulse        : PulseAudio daemon
lightdm        : Light Display Manager
avahi        : Avahi mDNS daemon
hplip        : HPLIP system user
henrique        : Henrique
postfix
debian-spamd
clamav

Devices
*******


Processor
---------

-Processor-
Name        : AMD Processor model unknown
Family, model, stepping        : 15, 127, 1 (AMD Opteron/Athlon64/FX)
Vendor        : AuthenticAMD
-Configuration-
Cache Size        : 256kb
Frequency        : 2000.00MHz
BogoMIPS        : 3999.46
Byte Order        : Little Endian
-Features-
FDIV Bug        : no
HLT Bug        : no
F00F Bug        : no
Coma Bug        : no
Has FPU        : yes
-Cache-
Level 1 (Data)        : 2-way set-associative, 512 sets, 64KB size
Level 1 (Instruction)        : 2-way set-associative, 512 sets, 64KB size
Level 2 (Unified)        : 16-way set-associative, 256 sets, 256KB size
-Capabilities-
fpu        : Floating Point Unit
vme        : Virtual 86 Mode Extension
de        : Debug Extensions - I/O breakpoints
pse        : Page Size Extensions (4MB pages)
tsc        : Time Stamp Counter and RDTSC instruction
msr        : Model Specific Registers
pae        : Physical Address Extensions
mce        : Machine Check Architeture
cx8        : CMPXCHG8 instruction
apic        : Advanced Programmable Interrupt Controller
sep        : Fast System Call (SYSENTER/SYSEXIT)
mtrr        : Memory Type Range Registers
pge        : Page Global Enable
mca        : Machine Check Architecture
cmov        : Conditional Move instruction
pat        : Page Attribute Table
pse36        : 36bit Page Size Extensions
clflush        : Cache Line Flush instruction
mmx        : MMX technology
fxsr        : FXSAVE and FXRSTOR instructions
sse        : SSE instructions
sse2        : SSE2 (WNI) instructions
syscall        : SYSCALL and SYSEXIT instructions
nx        : No-execute Page Protection
mmxext        : Extended MMX Technology
fxsr_opt
rdtscp        : RDTSCP
lm        : LAHF/SAHF in long mode
3dnowext        : Extended 3DNow! Technology
3dnow        : 3DNow! Technology
rep_good        : rep microcode works well on this CPU
nopl
extd_apicid
pni        : Streaming SIMD Extension 3 (Prescott New Instruction)
cx16        : CMPXCHG16B instruction
lahf_lm        : LAHF/SAHF in long mode
extapic
cr8_legacy
3dnowprefetch
vmmcall

Memory
------

-Memory-
Total Memory        : 1983200 kB
Free Memory        : 84592 kB
Buffers        : 45272 kB
Cached        : 1069004 kB
Cached Swap        : 0 kB
Active        : 675628 kB
Inactive        : 1096048 kB
Active(anon)        : 355140 kB
Inactive(anon)        : 318452 kB
Active(file)        : 320488 kB
Inactive(file)        : 777596 kB
Unevictable        : 0 kB
Mlocked        : 0 kB
Virtual Memory        : 2539880 kB
Free Virtual Memory        : 2539880 kB
Dirty        : 88 kB
Writeback        : 0 kB
AnonPages        : 657488 kB
Mapped        : 201176 kB
Shmem        : 16192 kB
Slab        : 62968 kB
SReclaimable        : 42136 kB
SUnreclaim        : 20832 kB
KernelStack        : 2744 kB
PageTables        : 33336 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 3531480 kB
Committed_AS        : 2034080 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 13396 kB
VmallocChunk        : 34359718752 kB
HardwareCorrupted        : 0 kB
AnonHugePages        : 143360 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 41856 kB
DirectMap2M        : 1988608 kB

PCI Devices
-----------

-PCI Devices-
Host bridge        : VIA Technologies, Inc. K8M800 Host Bridge
Host bridge        : VIA Technologies, Inc. K8M800 Host Bridge
Host bridge        : VIA Technologies, Inc. K8M800 Host Bridge
Host bridge        : VIA Technologies, Inc. K8M800 Host Bridge
Host bridge        : VIA Technologies, Inc. K8M800 Host Bridge
Host bridge        : VIA Technologies, Inc. K8M800 Host Bridge
PCI bridge        : VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South] (prog-if 00 [Normal decode])
IDE interface        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
IDE interface        : VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
USB controller        : VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
USB controller        : VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
USB controller        : VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
USB controller        : VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
USB controller        : VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
ISA bridge        : VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
Multimedia audio controller        : VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
Ethernet controller        : VIA Technologies, Inc. VT6102/VT6103 [Rhine-II] (rev 78)
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
VGA compatible controller        : VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01) (prog-if 00 [VGA controller])

USB Devices
-----------


Printers
--------

-Printers (CUPS)-
Canon_BJC-240
Canon_MG3600_series

Battery
-------

-UPS Status-
Status        : TRIM ONLINE
Time Left        : 28.1 Minutes
Line Voltage        : 130.0 Volts
Load Percent        : 17.0 Percent Load Capacity
-UPS Battery Information-
Battery Voltage        : 13.7 Volts
Battery Charge        : 100.0 Percent
Battery Date        : 2015-12-05
-UPS Information-
Model        : (null)
Firmware Version        : 876.Q1j.D USB FW:Q1
Serial Number        : 5B1025T22775
UPS Mode        : Stand Alone
Cable        : USB Cable
UPS Name        : BE600N-BR
-UPS Nominal Values-
Voltage        : 115 Volts
Battery Voltage        : 12.0 Volts
Power        : 600 Watts

Sensors
-------


Input Devices
-------------

-Input Devices-
 Power Button
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 ImPS/2 Generic Wheel Mouse

Storage
-------

-SCSI Disks-
ATA Maxtor 6L080L0
HL-DT-ST DVD-RAM GH22NP20

DMI
---

-BIOS-
Date        : 12/29/2006
Vendor        : Phoenix Technologies, LTD ([www.phoenix.com](www.phoenix.com))
Version        : 6.00 PG
-Board-
Name        : K8M800-8237
Vendor

Resources
---------

-I/O Ports-
<tt>0000-0000 </tt>        : PCI Bus #00
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>      0000-0000 </tt>        : IT8705F/IT871xF/IT872xF hardware monitoring driver
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
<tt>  0000-0000 </tt>        : VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
<tt>    0000-0000 </tt>        : SCSI low-level driver for VIA SATA controllers
-Memory-
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>  00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>  00000000-00000000 </tt>        : reserved
<tt>  00000000-00000000 </tt>        : reserved
<tt>  00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>00000000-00000000 </tt>        : PCI Bus #00
<tt>  00000000-00000000 </tt>        : reserved
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>  00000000-00000000 </tt>        : reserved
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>  00000000-00000000 </tt>        : reserved
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>  00000000-00000000 </tt>        : reserved
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>  00000000-00000000 </tt>        : reserved
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>  00000000-00000000 </tt>        : reserved
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>    00000000-00000000 </tt>        : pnp 00:00
<tt>    00000000-00000000 </tt>        : pnp 00:00
-DMA-
<tt> 2</tt>        : floppy
<tt> 4</tt>        : cascade

---

### Post by henrique-rj on 2017-09-12
nothing ?

---

### Post by henrique-rj on 2017-09-13
Examining the components of smart-notifier I noticed that it makes use of 3 or more scripts until its popup is shown. As the  system boot involves running multiple processes at the same time, some  of these smart-notifier scripts end up being interupted. This ends up not displaying the alert popup because its execution has been aborted. 

Is there any way to solve this situation?

Smart-notifier developers already warn that the alert popup might not work.

---

### Post by henrique-rj on 2017-09-14
Is smart-notifier loading late at boot system and not show popup alert test ?

---

### Post by henrique-rj on 2017-09-14
In my conception are two possibility 

One is the some script of smart-notifier not work on smartd started. Other, smart-notifier start after smartd.

One these two possibility has not show popup alert test in startup sistem.

Someone ?

---

### Post by henrique-rj on 2017-09-15
I was able to solve ...

I had to edit the script ( in root with Dolphin manager and Kate editor ), smartmontools, in /etc/init.de and just put " sleep 20 " as the first instruction and it was enough to delay loading the smartd in 20 seconds at system startup which gave time for the smart-notifier to load and then yes to show the test popup alert.

Searching realized that it was possible to use this "sleep" command in shell script and was just testing.

I now get the smart-notifier popup visual alerts on boot.

> #!/bin/sh -e
# 
# smartmontools init.d startup script
#
# (C) 2003,04,07 Guido Günther <agx@sigxcpu.org>
# 
# loosely based on the init script that comes with smartmontools which is
# copyrighted 2002 by Bruce Allen <smartmontools-support@lists.sourceforge.net>
#
### BEGIN INIT INFO
# Provides:          smartmontools
# Required-Start:    $syslog $remote_fs
# Required-Stop:     $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      1
# Short-Description: SMART monitoring daemon
### END INIT INFO
sleep 20
SMARTCTL=/usr/sbin/smartctl
DAEMON=/usr/sbin/smartd
PIDFILE=/var/run/smartd.pid

.

---


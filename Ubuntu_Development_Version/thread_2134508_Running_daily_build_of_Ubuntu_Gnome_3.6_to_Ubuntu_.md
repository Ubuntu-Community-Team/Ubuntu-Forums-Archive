---
title: "Running daily build of Ubuntu Gnome 3.6 to Ubuntu Gnome 3.8 via PPA. Faliure"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by FiremanEd on 2013-04-11
I am running Ubuntu Gnome 13.04 daily builds updated daily with zsync.  I wanted to install Gnome 3.8 via the "Gnome 3 Team" PPA's but upon installation it will boot to the point of the multi blue curtain with no gdm login and hang there with no further options.  Upon some minor troubleshooting it appears that when trying logout of the stuck multi blue no login with gdm that it seems to be logged into Gnome display Manager. This appears when I try to log it out via command prompt.  Unity I found sluggish like computing through clay.

Here is the hard copy of my system..
______________________________________________________________________________________________________________________________________________________________________________________________________________________________
```
Computer
********


Summary
-------

-Computer-
Processor		: 2x Intel(R) Pentium(R) CPU G620 @ 2.60GHz
Memory		: 5960MB (1254MB used)
Operating System		: Ubuntu Raring Ringtail (development branch)
User Name		: ed (Ed ******)
Date/Time		: Thu 11 Apr 2013 11:02:07 AM EDT
-Display-
Resolution		: 1920x1080 pixels
OpenGL Renderer		: Unknown
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA Intel PCH
-Input Devices-
 Power Button
 Power Button
 Logitech USB Optical Mouse
 Dell Dell USB Keyboard Hub
 Dell Dell USB Keyboard Hub
 HDA Intel PCH HDMI/DP,pcm		: 3=
 HDA Intel PCH Line
 HDA Intel PCH Rear Mic
 HDA Intel PCH Front Mic
 HDA Intel PCH Front Headphone
 HDA Intel PCH Line Out
-Printers-
No printers found
-SCSI Disks-
ATA ST31000528AS
Optiarc DVD RW AD-7250H
Maxtor OneTouch II
Generic STORAGE DEVICE
Generic STORAGE DEVICE
Generic STORAGE DEVICE
Generic STORAGE DEVICE

Operating System
----------------

-Version-
Kernel		: Linux 3.8.0-17-generic (x86_64)
Compiled		: #27-Ubuntu SMP Sun Apr 7 19:39:35 UTC 2013
C Library		: Unknown
Default C Compiler		: GNU C Compiler version 4.7.3 (Ubuntu/Linaro 4.7.2-23ubuntu2) 
Distribution		: Ubuntu Raring Ringtail (development branch)
-Current Session-
Computer Name		: ed-ubuntu-pc
User Name		: ed (Ed *******)
Home Directory		: /home/ed
Desktop Environment		: GNOME (gnome)
-Misc-
Uptime		: 2 hours, 41 minutes
Load Average		: 0.25, 0.32, 0.31

Kernel Modules
--------------

-Loaded Modules-
bnep		: Bluetooth BNEP ver 1.3
rfcomm		: Bluetooth RFCOMM ver 1.11
bluetooth		: Bluetooth Core ver 2.16
parport_pc		: PC-style parallel port driver
ppdev
usblp		: USB Printer Device Class driver
joydev		: Joystick device interfaces
snd_hda_codec_hdmi		: HDMI HD-audio codec
snd_hda_codec_realtek		: Realtek HD-audio codec
coretemp		: Intel Core temperature monitor
kvm_intel
kvm
snd_hda_intel		: Intel HDA driver
snd_hda_codec		: HDA codec core
snd_hwdep		: Hardware dependent layer
snd_pcm		: Midlevel PCM code for ALSA.
snd_page_alloc		: Memory allocator for ALSA system.
snd_seq_midi		: Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event		: MIDI byte &lt;-&gt; sequencer event coder
snd_rawmidi		: Midlevel RawMidi code for ALSA.
ghash_clmulni_intel		: GHASH Message Digest Algorithm, acclerated by PCLMULQDQ-NI
snd_seq		: Advanced Linux Sound Architecture sequencer.
i915		: Intel Graphics
snd_seq_device		: ALSA sequencer device management
snd_timer		: ALSA timer interface
cryptd		: Software async crypto daemon
gpio_ich		: GPIO interface for Intel ICH series
video		: ACPI Video Driver
snd		: Advanced Linux Sound Architecture driver for soundcards.
drm_kms_helper		: DRM KMS helper
drm		: DRM shared core routines
lpc_ich		: LPC interface for Intel ICH
soundcore		: Core sound module
microcode		: Microcode Update Driver
i2c_algo_bit		: I2C-Bus bit-banging algorithm
psmouse		: PS/2 mouse driver
mac_hid
serio_raw		: Raw serio driver
mei		: Intel(R) Management Engine Interface
lp
parport
usb_storage		: USB Mass Storage driver for Linux
hid_generic		: HID generic driver
usbhid		: USB HID core driver
hid
ahci		: AHCI SATA low-level driver
libahci		: Common AHCI SATA low-level routines
e1000e		: Intel(R) PRO/1000 Network Driver

Boots
-----

-Boots-
Thu Apr 11 08:20		: 33..8.0-17-generic|-
Wed Apr 10 13:28		: 33..8.0-17-generic|-
Wed Apr 10 11:57		: 33..8.0-17-generic|-
Wed Apr 10 11:46		: 33..8.0-17-generic|-

Languages
---------

-Available Languages-
en_AG		: English language locale for Antigua and Barbuda
en_AG.utf8		: English language locale for Antigua and Barbuda
en_AU.utf8		: English locale for Australia
en_BW.utf8		: English locale for Botswana
en_CA.utf8		: English locale for Canada
en_DK.utf8		: English locale for Denmark
en_GB.utf8		: English locale for Britain
en_HK.utf8		: English locale for Hong Kong
en_IE.utf8		: English locale for Ireland
en_IN		: English language locale for India
en_IN.utf8		: English language locale for India
en_NG		: English locale for Nigeria
en_NG.utf8		: English locale for Nigeria
en_NZ.utf8		: English locale for New Zealand
en_PH.utf8		: English language locale for Philippines
en_SG.utf8		: English language locale for Singapore
en_US.utf8		: English locale for the USA
en_ZA.utf8		: English locale for South Africa
en_ZM		: English locale for Zambia
en_ZM.utf8		: English locale for Zambia
en_ZW.utf8		: English locale for Zimbabwe

Filesystems
-----------

-Mounted File Systems-
/dev/sda1	/	5.86 % (857.6 GiB of 911.0 GiB)	
none	/sys/fs/cgroup	0.00 % (4.0 KiB of 4.0 KiB)	
udev	/dev	0.00 % (2.8 GiB of 2.8 GiB)	
tmpfs	/run	0.19 % (581.0 MiB of 582.1 MiB)	
none	/run/lock	0.00 % (5.0 MiB of 5.0 MiB)	
none	/run/shm	0.04 % (2.8 GiB of 2.8 GiB)	
none	/run/user	0.05 % (100.0 MiB of 100.0 MiB)	

Display
-------

-Display-
Resolution		: 1920x1080 pixels
Vendor		: The X.Org Foundation
Version		: 1.13.3
-Monitors-
Monitor 0		: 1920x1080 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
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
Vendor		: Unknown
Renderer		: Unknown
Version		: Unknown
Direct Rendering		: No

Environment Variables
---------------------

-Environment Variables-
SSH_AGENT_PID		: 1942
GPG_AGENT_INFO		: /run/user/ed/keyring-WCEuMR/gpg:0:1
TERM		: xterm
SHELL		: /bin/bash
XDG_SESSION_COOKIE		: f496fd8838926aa6ea7979ad51658956-1365682847.610111-1075819552
GJS_DEBUG_OUTPUT		: stderr
WINDOWID		: 16777221
GNOME_KEYRING_CONTROL		: /run/user/ed/keyring-WCEuMR
GJS_DEBUG_TOPICS		: JS ERROR;JS LOG
USER		: ed
LS_COLORS		: rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK		: /run/user/ed/keyring-WCEuMR/ssh
SESSION_MANAGER		: local/ed-ubuntu-pc:@/tmp/.ICE-unix/1892,unix/ed-ubuntu-pc:/tmp/.ICE-unix/1892
USERNAME		: ed
DEFAULTS_PATH		: /usr/share/gconf/gnome.default.path
XDG_CONFIG_DIRS		: /etc/xdg/xdg-gnome:/etc/xdg
PATH		: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
DESKTOP_SESSION		: gnome
PWD		: /home/ed
GNOME_KEYRING_PID		: 1873
LANG		: en_US.UTF-8
GDM_LANG		: en_US
MANDATORY_PATH		: /usr/share/gconf/gnome.mandatory.path
GDMSESSION		: gnome
SHLVL		: 1
HOME		: /home/ed
GNOME_DESKTOP_SESSION_ID		: this-is-deprecated
LOGNAME		: ed
XDG_DATA_DIRS		: /usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS		: unix:abstract=/tmp/dbus-TDjGfhYld5,guid=024772627a89cad6be6617de5166aa9f
LESSOPEN		: | /usr/bin/lesspipe %s
TEXTDOMAIN		: im-config
WINDOWPATH		: 7
XDG_RUNTIME_DIR		: /run/user/ed
DISPLAY		: :0
XDG_CURRENT_DESKTOP		: GNOME
LESSCLOSE		: /usr/bin/lesspipe %s %s
TEXTDOMAINDIR		: /usr/share/locale/
COLORTERM		: gnome-terminal
XAUTHORITY		: /run/gdm/auth-for-ed-13eAxU/database
_		: /usr/bin/hardinfo

Users
-----

-Users-
root		: root
daemon		: daemon
bin		: bin
sys		: sys
sync		: sync
games		: games
man		: man
lp		: lp
mail		: mail
news		: news
uucp		: uucp
proxy		: proxy
www-data		: www-data
backup		: backup
list		: Mailing List Manager
irc		: ircd
gnats		: Gnats Bug-Reporting System (admin)
nobody		: nobody
libuuid
syslog
messagebus
avahi-autoipd		: Avahi autoip daemon
usbmux		: usbmux daemon
dnsmasq		: dnsmasq
whoopsie
kernoops		: Kernel Oops Tracking Daemon
rtkit		: RealtimeKit
speech-dispatcher		: Speech Dispatcher
avahi		: Avahi mDNS daemon
colord		: colord colour management daemon
pulse		: PulseAudio daemon
hplip		: HPLIP system user
gdm		: Gnome Display Manager
saned
debian-spamd
ed		: Ed *******

Devices
*******


Processor
---------

-Processors-
Intel(R) Pentium(R) CPU G620 @ 2.60GHz		: 2600.00MHz
Intel(R) Pentium(R) CPU G620 @ 2.60GHz		: 2600.00MHz

Memory
------

-Memory-
Total Memory		: 5960568 kB
Free Memory		: 1786008 kB
Buffers		: 63460 kB
Cached		: 2923424 kB
Cached Swap		: 0 kB
Active		: 3140788 kB
Inactive		: 805012 kB
Active(anon)		: 761968 kB
Inactive(anon)		: 522016 kB
Active(file)		: 2378820 kB
Inactive(file)		: 282996 kB
Unevictable		: 48 kB
Mlocked		: 48 kB
Virtual Memory		: 6134780 kB
Free Virtual Memory		: 6134780 kB
Dirty		: 8 kB
Writeback		: 0 kB
AnonPages		: 958964 kB
Mapped		: 268908 kB
Shmem		: 325068 kB
Slab		: 136608 kB
SReclaimable		: 113228 kB
SUnreclaim		: 23380 kB
KernelStack		: 3432 kB
PageTables		: 26300 kB
NFS_Unstable		: 0 kB
Bounce		: 0 kB
WritebackTmp		: 0 kB
CommitLimit		: 9115064 kB
Committed_AS		: 3632408 kB
VmallocTotal		: 34359738367 kB
VmallocUsed		: 556256 kB
VmallocChunk		: 34359177816 kB
HardwareCorrupted		: 0 kB
AnonHugePages		: 0 kB
HugePages_Total		: 0
HugePages_Free		: 0
HugePages_Rsvd		: 0
HugePages_Surp		: 0
Hugepagesize		: 2048 kB
DirectMap4k		: 47104 kB
DirectMap2M		: 6094848 kB

PCI Devices
-----------

-PCI Devices-
Host bridge		: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
VGA compatible controller		: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
Communication controller		: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
Ethernet controller		: Intel Corporation 82579V Gigabit Network Connection (rev 05)
USB controller		: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
Audio device		: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
USB controller		: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
ISA bridge		: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
SATA controller		: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
SMBus		: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)

USB Devices
-----------


Printers
--------

-Printers-
No printers found

Battery
-------

-No batteries-
No batteries found on this system

Sensors
-------

-Cooling Fans-
-Temperatures-
temp1		: 37.00°C
temp2		: 37.00°C
temp3		: 36.00°C
-Voltage Values-

Input Devices
-------------

-Input Devices-
 Power Button
 Power Button
 Logitech USB Optical Mouse
 Dell Dell USB Keyboard Hub
 Dell Dell USB Keyboard Hub
 HDA Intel PCH HDMI/DP,pcm		: 3=
 HDA Intel PCH Line
 HDA Intel PCH Rear Mic
 HDA Intel PCH Front Mic
 HDA Intel PCH Front Headphone
 HDA Intel PCH Line Out

Storage
-------

-SCSI Disks-
ATA ST31000528AS
Optiarc DVD RW AD-7250H
Maxtor OneTouch II
Generic STORAGE DEVICE
Generic STORAGE DEVICE
Generic STORAGE DEVICE
Generic STORAGE DEVICE

DMI
---

-BIOS-
Date		: 02/25/2011
Vendor		: LENOVO
Version		: DPKT15A
-Board-
Name		: To be filled by O.E.M.
Vendor		: LENOVO

Resources
---------

-I/O Ports-
<tt>0000-0cf7 </tt>		: PCI Bus 0000:00
<tt>  0000-001f </tt>		: dma1
<tt>  0020-0021 </tt>		: pic1
<tt>  0040-0043 </tt>		: timer0
<tt>  0050-0053 </tt>		: timer1
<tt>  0060-0060 </tt>		: keyboard
<tt>  0064-0064 </tt>		: keyboard
<tt>  0070-0071 </tt>		: rtc0
<tt>  0080-008f </tt>		: dma page reg
<tt>  00a0-00a1 </tt>		: pic2
<tt>  00c0-00df </tt>		: dma2
<tt>  00f0-00ff </tt>		: fpu
<tt>  0400-0453 </tt>		: pnp 00:07
<tt>    0400-0403 </tt>		: ACPI PM1a_EVT_BLK
<tt>    0404-0405 </tt>		: ACPI PM1a_CNT_BLK
<tt>    0408-040b </tt>		: ACPI PM_TMR
<tt>    0410-0415 </tt>		: ACPI CPU throttle
<tt>    0420-042f </tt>		: ACPI GPE0_BLK
<tt>      0428-042f </tt>		: GPIO interface for Intel ICH series
<tt>    0430-0433 </tt>		: iTCO_wdt
<tt>    0450-0450 </tt>		: ACPI PM2_CNT_BLK
<tt>  0454-0457 </tt>		: pnp 00:08
<tt>  0458-047f </tt>		: pnp 00:07
<tt>    0460-047f </tt>		: iTCO_wdt
<tt>  04d0-04d1 </tt>		: pnp 00:06
<tt>  0500-057f </tt>		: GPIO interface for Intel ICH series
<tt>    0500-057f </tt>		: pnp 00:07
<tt>      0500-052f </tt>		: GPIO interface for Intel ICH series
<tt>      0530-053f </tt>		: GPIO interface for Intel ICH series
<tt>      0540-054f </tt>		: GPIO interface for Intel ICH series
<tt>  0a00-0a1f </tt>		: pnp 00:01
<tt>0cf8-0cff </tt>		: PCI conf1
<tt>0d00-ffff </tt>		: PCI Bus 0000:00
<tt>  1180-119f </tt>		: pnp 00:07
<tt>  f000-f03f </tt>		: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
<tt>  f040-f05f </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
<tt>  f060-f07f </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
<tt>    f060-f07f </tt>		: AHCI SATA low-level driver
<tt>  f080-f09f </tt>		: Intel Corporation 82579V Gigabit Network Connection (rev 05)
<tt>  f0a0-f0a3 </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
<tt>    f0a0-f0a3 </tt>		: AHCI SATA low-level driver
<tt>  f0b0-f0b7 </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
<tt>    f0b0-f0b7 </tt>		: AHCI SATA low-level driver
<tt>  f0c0-f0c3 </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
<tt>    f0c0-f0c3 </tt>		: AHCI SATA low-level driver
<tt>  f0d0-f0d7 </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
<tt>    f0d0-f0d7 </tt>		: AHCI SATA low-level driver
-Memory-
<tt>00000000-0000ffff </tt>		: reserved
<tt>00010000-0009abff </tt>		: System RAM
<tt>0009ac00-0009ffff </tt>		: reserved
<tt>000a0000-000bffff </tt>		: PCI Bus 0000:00
<tt>000c0000-000cd9ff </tt>		: Video ROM
<tt>000e0000-000fffff </tt>		: reserved
<tt>  000f0000-000fffff </tt>		: System ROM
<tt>00100000-1fffffff </tt>		: System RAM
<tt>  01000000-016d79e7 </tt>		: Kernel code
<tt>  016d79e8-01cef2bf </tt>		: Kernel data
<tt>  01df0000-01f27fff </tt>		: Kernel bss
<tt>20000000-201fffff </tt>		: reserved
<tt>20200000-3fffffff </tt>		: System RAM
<tt>40000000-401fffff </tt>		: reserved
<tt>40200000-b6d5bfff </tt>		: System RAM
<tt>b6d5c000-b6daafff </tt>		: ACPI Non-volatile Storage
<tt>b6dab000-b6dcbfff </tt>		: reserved
<tt>b6dcc000-b6dcdfff </tt>		: System RAM
<tt>b6dce000-b6deefff </tt>		: ACPI Non-volatile Storage
<tt>b6def000-b6dfcfff </tt>		: reserved
<tt>b6dfd000-b6e09fff </tt>		: ACPI Non-volatile Storage
<tt>b6e0a000-b6e43fff </tt>		: reserved
<tt>b6e44000-b6e86fff </tt>		: ACPI Non-volatile Storage
<tt>b6e87000-b6ffffff </tt>		: System RAM
<tt>b7000000-b77fffff </tt>		: RAM buffer
<tt>b7800000-bf9fffff </tt>		: reserved
<tt>bfa00000-ffffffff </tt>		: PCI Bus 0000:00
<tt>  d0000000-dfffffff </tt>		: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
<tt>  e0000000-efffffff </tt>		: PCI MMCONFIG 0000 [bus 00-ff]
<tt>    e0000000-efffffff </tt>		: pnp 00:00
<tt>  fe000000-fe3fffff </tt>		: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
<tt>  fe400000-fe41ffff </tt>		: Intel Corporation 82579V Gigabit Network Connection (rev 05)
<tt>    fe400000-fe41ffff </tt>		: Intel(R) PRO/1000 Network Driver
<tt>  fe420000-fe423fff </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
<tt>    fe420000-fe423fff </tt>		: ICH HD audio
<tt>  fe424000-fe4240ff </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
<tt>  fe425000-fe4257ff </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
<tt>    fe425000-fe4257ff </tt>		: AHCI SATA low-level driver
<tt>  fe426000-fe4263ff </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
<tt>    fe426000-fe4263ff </tt>		: ehci_hcd
<tt>  fe427000-fe4273ff </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
<tt>    fe427000-fe4273ff </tt>		: ehci_hcd
<tt>  fe428000-fe428fff </tt>		: Intel Corporation 82579V Gigabit Network Connection (rev 05)
<tt>    fe428000-fe428fff </tt>		: Intel(R) PRO/1000 Network Driver
<tt>  fe429000-fe42900f </tt>		: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
<tt>    fe429000-fe42900f </tt>		: Intel(R) Management Engine Interface
<tt>  fec00000-fec003ff </tt>		: IOAPIC 0
<tt>  fed00000-fed003ff </tt>		: HPET 0
<tt>  fed08000-fed08fff </tt>		: pnp 00:07
<tt>  fed10000-fed19fff </tt>		: pnp 00:00
<tt>  fed1c000-fed1ffff </tt>		: reserved
<tt>    fed1c000-fed1ffff </tt>		: pnp 00:07
<tt>      fed1f410-fed1f414 </tt>		: iTCO_wdt
<tt>  fed20000-fed3ffff </tt>		: pnp 00:00
<tt>  fed40000-fed44fff </tt>		: pnp 00:06
<tt>  fed90000-fed93fff </tt>		: pnp 00:00
<tt>  fee00000-fee0ffff </tt>		: pnp 00:00
<tt>    fee00000-fee00fff </tt>		: Local APIC
<tt>  ff000000-ffffffff </tt>		: reserved
<tt>    ff000000-ffffffff </tt>		: pnp 00:07
<tt>100000000-1bfdfffff </tt>		: System RAM
<tt>1bfe00000-1bfffffff </tt>		: RAM buffer
-DMA-
<tt> 4</tt>		: cascade

Network
*******


Interfaces
----------

-Network Interfaces-
eth0	202.50MiB	11.36MiB	192.168.2.107	
lo	0.18MiB	0.18MiB	127.0.0.1	

IP Connections
--------------

-Connections-
0.0.0.0:139	LISTEN	0.0.0.0:*	tcp	
127.0.1.1:53		0.0.0.0:*	udp	
127.0.0.1:631	LISTEN	0.0.0.0:*	tcp	
0.0.0.0:445	LISTEN	0.0.0.0:*	tcp	
192.168.2.107:52131	ESTABLISHED	74.125.130.125:5222	tcp	
192.168.2.107:34101	CLOSE_WAIT	98.137.200.255:80	tcp	
192.168.2.107:38577	CLOSE_WAIT	173.194.37.51:443	tcp	
192.168.2.107:37322	ESTABLISHED	131.247.45.251:8002	tcp	
192.168.2.107:60380	CLOSE_WAIT	78.141.177.70:80	tcp	
192.168.2.107:43280	CLOSE_WAIT	83.15.78.94:80	tcp	
192.168.2.107:37876	CLOSE_WAIT	173.194.37.50:443	tcp	
192.168.2.107:37812	ESTABLISHED	91.189.89.76:443	tcp	
192.168.2.107:37877	CLOSE_WAIT	173.194.37.50:443	tcp	
:::139	LISTEN	:::*	tcp6	
::1:631	LISTEN	:::*	tcp6	
:::445	LISTEN	:::*	tcp6	
0.0.0.0:5353		0.0.0.0:*	udp	
0.0.0.0:60419		0.0.0.0:*	udp	
0.0.0.0:3825		0.0.0.0:*	udp	
127.0.1.1:53		0.0.0.0:*	udp	
0.0.0.0:68		0.0.0.0:*	udp	
192.168.2.255:137		0.0.0.0:*	udp	
192.168.2.107:137		0.0.0.0:*	udp	
0.0.0.0:137		0.0.0.0:*	udp	
192.168.2.255:138		0.0.0.0:*	udp	
192.168.2.107:138		0.0.0.0:*	udp	
0.0.0.0:138		0.0.0.0:*	udp	
127.0.0.1:33058	ESTABLISHED	127.0.1.1:53	udp	
:::61890		:::*	udp6	
:::5353		:::*	udp6	
:::41120		:::*	udp6	

Routing Table
-------------

-IP routing table-
0.0.0.0 / 192.168.2.1	0.0.0.0	UG	eth0	
169.254.0.0 / 0.0.0.0	255.255.0.0	U	eth0	
192.168.2.0 / 0.0.0.0	255.255.255.0	U	eth0	

ARP Table
---------

-ARP Table-
192.168.2.100	00:24:8c:47:56:da	eth0	
192.168.2.1	00:0f:66:53:d6:f5	eth0	

DNS Servers
-----------

-Name servers-
127.0.1.1

Statistics
----------

-IP-
185974		: Total packets received
0		: Incoming packets discarded
0		: Incoming packets discarded
185972		: Incoming packets delivered
123717		: Requests sent out
4		: Outgoing packets dropped
-ICMP-
8		: ICMP messages received
0		: ICMP messages failed
214		: ICMP messages sent
0		: ICMP messages failed
-ICMPMSG-
-TCP-
1042		: Active connections openings
50		: Passive connection openings
5		: Failed connection attempts
22		: Connection resets received
3		: Connections established
182633		: Segments received
120509		: Segments send out
51		: Segments retransmited
4		: Bad segments received.
881		: Resets sent
-UDP-
3153		: Packets received
214		: Packets to unknown port received.
0		: Packet receive errors
3010		: Packets sent
-UDPLITE-
-TCPEXT-
2		: Congestion windows fully recovered without slow start
429		: TCP sockets finished time wait in fast timer
47316		: Delayed acks sent
2		: Congestion windows fully recovered without slow start
2347		: Packets directly queued to recvmsg prequeue.
3863838		: Bytes directly received in process context from prequeue
128167		: Packet headers predicted
2344		: Packets header predicted and directly queued to user
2559		: Acknowledgments not containing data payload received
2138		: Predicted acknowledgments
3		: Fast retransmits
2		: Congestion windows fully recovered without slow start
1		: Connections reset due to early user close
6		: Packets collapsed in receive queue due to low socket buffer
14		: Congestion windows recovered without slow start after partial ack
3		: Fast retransmits
1		: Connections reset due to early user close
28		: Other TCP timeouts
6		: Packets collapsed in receive queue due to low socket buffer
18		: DSACKs sent for old packets
21		: DSACKs received
190		: Connections reset due to unexpected data
1		: Connections reset due to early user close
-IPEXT-

Shared Directories
------------------

-SAMBA-
-NFS-

Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>	2600 MHz	7.651	
Intel(R) Celeron(R) M processor         1.50GHz	(null)	26.1876862	
PowerPC 740/750 (280.00MHz)	(null)	172.816713	

CPU CryptoHash
--------------

-CPU CryptoHash-
<big><b>This Machine</b></big>	2600 MHz	208.284	

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>	2600 MHz	2.020	
Intel(R) Celeron(R) M processor         1.50GHz	(null)	8.1375674	
PowerPC 740/750 (280.00MHz)	(null)	58.07682	

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>	2600 MHz	6.442	

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>	2600 MHz	2.698	

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>	2600 MHz	14.988	
Intel(R) Celeron(R) M processor         1.50GHz	(null)	40.8816714	
PowerPC 740/750 (280.00MHz)	(null)	161.312647
```	
_____________________________________________________________________________________________________________________________________________________________________________________________________________________________

I am quite happy with the speed and functionality of gnome 3.6 but would love to expeience the 3.8 gnome experience.  Any thoughts, appreciated.  Is it a matter of waiting for the PPA's to mature or should I just stick with this wonderful, fast non-unity user experience I am enjoying?

FiremanEd

---

### Post by Hewjr100 on 2013-04-11
I had the same problem, in my case it was simply doing the following in terminal:  "sudo apt-get dist-upgrade" after installing the PPA.  On my first attempt I did a normal update/upgrade.

Henry

PS Don't include the quotes.

---


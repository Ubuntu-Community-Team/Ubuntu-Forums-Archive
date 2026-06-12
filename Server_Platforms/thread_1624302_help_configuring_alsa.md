---
title: "help configuring alsa?"
date: 2010-11-17
forum: Server Platforms
---

### Post by bluerabbit4210 on 2010-11-17
Hi all, hopefully someone here can give me a hand with this.

I installed alsa-base and alsa-tools from aptitude, added my user to the 'audio' group and...no sound from `speaker-test -Dhw:0,0`

It seems like I'm probably missing something obvious, so I'll post some outputs here and hopefully someone can spot it real quick!

uname -a
```
Linux $SERVERNAME 2.6.35-22-server #35-Ubuntu SMP Sat Oct 16 22:02:33 UTC 2010 x86_64 GNU/Linux
```

lspci -vvv
```

...
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: IBM Device 02d8
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at 3000 [size=256]
        Region 1: I/O ports at 3400 [size=64]
        Region 2: Memory at d5300800 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at d5300400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
...

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lsmod | grep snd
```

snd_intel8x0           31307  0 
snd_ac97_codec        125227  1 snd_intel8x0
ac97_bus                1474  1 snd_ac97_codec
snd_pcm                88118  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            5932  0 
snd_rawmidi            21775  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57032  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23518  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    63620  7 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_intel8x0,snd_pcm

```

[alsa-info.sh]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Nov 17 20:51:23 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      IBM
Product Name:      8143A6U


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-server
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 1014:02d8


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : (null)
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : (null)
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x1014
PCI Subsys Device: 0x02d8

Flags: 10
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 48000Hz
PCM ADC          : 48000Hz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 8787
0:04 = 8686
0:06 = 8008
0:08 = 0000
0:0a = 0000
0:0c = 8007
0:0e = 8006
0:10 = 8686
0:12 = 8686
0:14 = 0000
0:16 = 8787
0:18 = 8686
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0031
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0008
0:74 = 1001
0:76 = 2010
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116, 10 Nov 17 12:33 /dev/snd/controlC0
crw-rw---- 1 root audio 116,  9 Nov 17 12:33 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116,  8 Nov 17 12:50 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116,  7 Nov 17 12:33 /dev/snd/pcmC0D1c
crw-rw---- 1 root audio 116,  6 Nov 17 12:33 /dev/snd/pcmC0D2c
crw-rw---- 1 root audio 116,  5 Nov 17 12:33 /dev/snd/pcmC0D3c
crw-rw---- 1 root audio 116,  4 Nov 17 12:33 /dev/snd/pcmC0D4p
crw-rw---- 1 root audio 116,  3 Nov 17 12:33 /dev/snd/seq
crw-rw---- 1 root audio 116,  2 Nov 17 12:33 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Nov 17 12:33 .
drwxr-xr-x 3 root root 240 Nov 17 12:33 ..
lrwxrwxrwx 1 root root  12 Nov 17 12:33 pci-0000:00:1e.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1981B at irq 17'
  Mixer name	: 'Analog Devices AD1981B'
  Components	: 'AC97a:41445374'
  Controls      : 28
  Simple ctrls  : 20
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 24 [77%] [-10.50dB] [off]
  Front Right: Playback 24 [77%] [-10.50dB] [off]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [-12.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [off]
  Front Right: Playback 25 [81%] [-9.00dB] [off]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [off]
  Front Right: Playback 25 [81%] [3.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [off] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [off] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [3.00dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 24 [77%] [1.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 24 [77%] [1.50dB] [off] Capture [off]
  Front Right: Playback 24 [77%] [1.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 false
		value.1 false
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 24
		value.1 24
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 25
		value.1 25
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 23
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 24
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 25
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 25
		value.1 25
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 false
		value.1 false
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 false
		value.1 false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 24
		value.1 24
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 false
		value.1 false
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 25
		value.1 25
	}
	control.20 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Stereo Mic'
		value false
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value false
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value false
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nfsd
exportfs
nfs
lockd
fscache
nfs_acl
auth_rpcgss
sunrpc
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
nouveau
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
ttm
snd_seq
snd_timer
snd_seq_device
drm_kms_helper
ppdev
parport_pc
snd
drm
lp
psmouse
i2c_algo_bit
intel_agp
soundcore
snd_page_alloc
parport
serio_raw
usblp
usbhid
hid
usb_storage
tg3
floppy


!!ALSA/HDA dmesg
!!------------------

[alsa-info.sh crashes at this point]


```
alsa-info.sh exits with the error:
```

pcilib: sysfs_read_vpd: read failed: Connection timed out

```
As far as I can tell, the correct module (snd_intel8x0) is being loaded, alsamixer gives me pretty levels to adjust, etc, but no joy.  Tried plugging the speakers into everywhere the plug would fit ;)

Booting into a live cd of LinuxMint 9 (based on ubuntu 10.04) gives me sound from pulseaudio, so my hardware isn't broken.

I'm pretty new to the inner workings of alsa, especially from a shell prompt.  Thanks in advance to whoever can help me.  Let me know if there's any info i've left out.

also, ive been using `speaker-test -Dhw:0,0 -c2` to test this, as well as MOC (mocp).  Pretty new to MOC as well, instead of 'Master' the mixer is displayed as 'PCM', if that's even relevant.

---

### Post by NathanBC on 2010-11-19
Did you unmute the channel you expect to hear sound on?  Mute can be toggled in alsamixer by pressing the m key.

---


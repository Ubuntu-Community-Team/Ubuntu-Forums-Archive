---
title: "jack server is not running or cannot be started.??"
date: 2012-02-03
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-02-03
Recap:
[U][I][B]
EQUIPMENT:[/B][/I][/U]
Dell Optiplex 330 dual core, 4 gig mem, desktop
**Xonar DG soundcard **in PCI slot.
nvidia GeForce 8400 

*_**OS:**_*
Ubuntu 11.10  w. nvidia drivers, dual screens working.

_***SOFTWARE:***_
Jack cntrl
Patchage
Ardour
Hydrogen
Guitarix
Rackarrack

alsamixer
Gnome alsamixer

This is my first successful install of all these things:
[U][I][B]
First run of Jack control:[/B][/I][/U]

- error no startup:
[COLOR=Navy]*   jjack server is not running or cannot be started*[/COLOR]


tried disabling onboard soundcard in BIOS:


- **same error, **only more error msgs - See below:

I'm so close to getting things working:
I previously had the Xonar card working with playback only, in the last install, 
but that crashed when attempting to install dual screens.

Card shows up as follows:
 
```


~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DG [Xonar DG], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 ~# 

~# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@ben-OptiPlex-330:~# 


```There seems to be something wrong with the JACK program attempting to write to disk?
Here is the JACK msg/error output on startup:

```
    [COLOR=#999999]07:04:37.903 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]07:04:37.915 Statistics reset.[/COLOR]
 [COLOR=#cccc99]07:04:37.962 ALSA connection change.[/COLOR]
 [COLOR=#999999]07:04:38.281 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]07:04:38.290 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]07:05:12.105 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: driver "alsa" selected
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Fri Feb  3 07:05:11 2012: Starting jack server...
 Fri Feb  3 07:05:11 2012: JACK server starting in realtime mode with priority 10
 Fri Feb  3 07:05:12 2012: control device hw:0
 Fri Feb  3 07:05:12 2012: control device hw:0
 Fri Feb  3 07:05:12 2012: Acquired audio card Audio0
 Fri Feb  3 07:05:12 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|1|0|nomon|swmeter|-|32bit
 Fri Feb  3 07:05:12 2012: control device hw:0
 Fri Feb  3 07:05:12 2012: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 Fri Feb  3 07:05:12 2012: ALSA: final selected sample format for capture: 32bit integer little-endian
 Fri Feb  3 07:05:12 2012: [1m[31mERROR: ALSA: cannot set channel count to 1 for capture[0m
 Fri Feb  3 07:05:12 2012: [1m[31mERROR: ALSA: cannot configure capture channel[0m
 Fri Feb  3 07:05:12 2012: [1m[31mERROR: Cannot initialize driver[0m
 Fri Feb  3 07:05:12 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Fri Feb  3 07:05:12 2012: [1m[31mERROR: Failed to open server[0m
 [COLOR=#ff0000]07:05:32.425 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```

PS: 

 Banshee player plays mp3s to the soundcard no problem, when JACKis NOT running.

---

### Post by nazaroo2 on 2012-02-03
I looked in the sticky thread, 
and I ran the script to fetch ALSA information.
I hope this helps, in trying to figure out how to get JACK working properly.


[My System ALSA info]("http://www.alsa-project.org/db/?f=83d3454bd7e19b22148a27640af9a59ec9b29d3b")

```
!!################################ !!ALSA Information Script v 0.4.60 !!################################  !!Script ran on: Fri Feb  3 15:00:55 UTC 2012   !!Linux Distribution !!------------------  Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"   !!DMI Information !!---------------  Manufacturer:      Dell Inc. Product Name:      OptiPlex 330                  Product Version:      !!Kernel Information !!------------------  Kernel release:    3.0.0-15-generic-pae Operating System:  GNU/Linux Architecture:      i686 Processor:         i686 SMP Enabled:       Yes   !!ALSA Version !!------------  Driver version:     1.0.24 Library version:    1.0.24.1 Utilities version:  1.0.24.2   !!Loaded ALSA modules !!-------------------  snd_oxygen   !!Sound Servers on this system !!----------------------------  Pulseaudio:       Installed - Yes (/usr/bin/pulseaudio)       Running - No  ESound Daemon:       Installed - Yes (/usr/bin/esd)       Running - No  Jack:       Installed - Yes (/usr/bin/jackd)       Running - No   !!Soundcards recognised by ALSA !!-----------------------------   0 [DG             ]: CMI8786 - Xonar DG                       C-Media Oxygen HD Audio at 0xcc00, irq 18   !!PCI Soundcards installed in the system !!--------------------------------------  03:02.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]   !!Advanced information - PCI Vendor/Device/Subsystem ID's !!--------------------------------------------------------  03:02.0 0401: 13f6:8788 	Subsystem: 1043:8467   !!Modprobe options (Sound related) !!--------------------------------  snd-atiixp-modem: index=-2 snd-intel8x0m: index=-2 snd-via82xx-modem: index=-2 snd-usb-audio: index=-2 snd-usb-caiaq: index=-2 snd-usb-ua101: index=-2 snd-usb-us122l: index=-2 snd-usb-usx2y: index=-2 snd-cmipci: mpu_port=0x330 fm_port=0x388 snd-pcsp: index=-2 snd-usb-audio: index=-2   !!Loaded sound module options !!--------------------------  !!Module: snd_oxygen 	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y 	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null) 	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1   !!ALSA Device nodes !!-----------------  crw-rw----  1 root audio 116,  5 Feb  3 07:03 /dev/snd/controlC0 crw-rw----  1 root audio 116,  4 Feb  3 07:03 /dev/snd/pcmC0D0c crw-rw----  1 root audio 116,  3 Feb  3 08:02 /dev/snd/pcmC0D0p crw-rw----  1 root audio 116,  2 Feb  3 07:03 /dev/snd/pcmC0D1p crw-rw----  1 root audio 116,  1 Feb  3 07:03 /dev/snd/seq crw-rw----  1 root audio 116, 33 Feb  3 07:03 /dev/snd/timer  /dev/snd/by-path: total 0 drwxr-xr-x 2 root root  60 Feb  3 07:03 . drwxr-xr-x 3 root root 180 Feb  3 07:03 .. lrwxrwxrwx 1 root root  12 Feb  3 07:03 pci-0000:03:02.0 -> ../controlC0   !!Aplay/Arecord output !!------------  APLAY  **** List of PLAYBACK Hardware Devices **** card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]   Subdevices: 0/1   Subdevice #0: subdevice #0 card 0: DG [Xonar DG], device 1: Digital [Digital]   Subdevices: 1/1   Subdevice #0: subdevice #0  ARECORD  **** List of CAPTURE Hardware Devices **** card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]   Subdevices: 1/1   Subdevice #0: subdevice #0  !!Amixer output !!-------------  !!-------Mixer controls for card 0 [DG]  Card hw:0 'DG'/'C-Media Oxygen HD Audio at 0xcc00, irq 18'   Mixer name	: 'CMI8786'   Components	: 'CS4245 CMI8786'   Controls      : 15   Simple ctrls  : 10 Simple mixer control 'Headphones Impedance',0   Capabilities: penum   Items: '< 64 ohms' '64-150 ohms' '150-300 ohms'   Item0: '< 64 ohms' Simple mixer control 'Front Mic',0   Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum   Capture exclusive group: 0   Capture channels: Front Left - Front Right   Limits: Capture -24 - 24   Front Left: Capture -24 [0%] [off]   Front Right: Capture -24 [0%] [off] Simple mixer control 'Line',0   Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum   Capture exclusive group: 0   Capture channels: Front Left - Front Right   Limits: Capture -24 - 24   Front Left: Capture -24 [0%] [off]   Front Right: Capture -24 [0%] [off] Simple mixer control 'Mic',0   Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum   Capture exclusive group: 0   Capture channels: Front Left - Front Right   Limits: Capture -24 - 24   Front Left: Capture 0 [50%] [on]   Front Right: Capture 0 [50%] [on] Simple mixer control 'IEC958',0   Capabilities: pswitch pswitch-joined penum   Playback channels: Mono   Mono: Playback [on] Simple mixer control 'Aux',0   Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum   Capture exclusive group: 0   Capture channels: Front Left - Front Right   Limits: Capture -24 - 24   Front Left: Capture -24 [0%] [off]   Front Right: Capture -24 [0%] [off] Simple mixer control 'ADC High-pass Filter',0   Capabilities: cenum   Items: 'Active' 'Frozen'   Item0: 'Active' Simple mixer control 'Analog Input Monitor',0   Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum   Playback channels: Mono   Limits: Playback 0 - 1   Mono: Playback 0 [0%] [-6.00dB] [on] Simple mixer control 'Analog Output',0   Capabilities: penum   Items: 'Speakers' 'Headphones' 'FP Headphones'   Item0: 'Speakers' Simple mixer control 'Stereo Upmixing',0   Capabilities: enum   Items: 'Front' 'Front Surround'   Item0: 'Front Surround'   !!Alsactl output !!-------------  --startcollapse-- state.DG { 	control.1 { 		iface MIXER 		name 'Stereo Upmixing' 		value Front Surround 		comment { 			access 'read write' 			type ENUMERATED 			count 1 			item.0 Front 			item.1 Front Surround 		} 	} 	control.2 { 		iface MIXER 		name 'IEC958 Playback Switch' 		value true 		comment { 			access 'read write' 			type BOOLEAN 			count 1 		} 	} 	control.3 { 		iface PCM 		device 1 		name 'IEC958 Playback Default' 		value '0482000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 		comment { 			access 'read write' 			type IEC958 			count 1 		} 	} 	control.4 { 		iface PCM 		device 1 		name 'IEC958 Playback Con Mask' 		value '3eff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 		comment { 			access read 			type IEC958 			count 1 		} 	} 	control.5 { 		iface PCM 		device 1 		name 'IEC958 Playback PCM Stream' 		value '0482000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 		comment { 			access 'read write inactive' 			type IEC958 			count 1 		} 	} 	control.6 { 		iface MIXER 		name 'Analog Input Monitor Playback Switch' 		value true 		comment { 			access 'read write' 			type BOOLEAN 			count 1 		} 	} 	control.7 { 		iface MIXER 		name 'Analog Input Monitor Playback Volume' 		value 0 		comment { 			access 'read write' 			type INTEGER 			count 1 			range '0 - 1' 			dbmin -600 			dbmax 0 			dbvalue.0 -600 		} 	} 	control.8 { 		iface MIXER 		name 'Analog Output Playback Enum' 		value Speakers 		comment { 			access 'read write' 			type ENUMERATED 			count 1 			item.0 Speakers 			item.1 Headphones 			item.2 'FP Headphones' 		} 	} 	control.9 { 		iface MIXER 		name 'Headphones Impedance Playback Enum' 		value '< 64 ohms' 		comment { 			access 'read write' 			type ENUMERATED 			count 1 			item.0 '< 64 ohms' 			item.1 '64-150 ohms' 			item.2 '150-300 ohms' 		} 	} 	control.10 { 		iface MIXER 		name 'Mic Capture Volume' 		value.0 0 		value.1 0 		comment { 			access 'read write' 			type INTEGER 			count 2 			range '-24 - 24' 		} 	} 	control.11 { 		iface MIXER 		name 'Aux Capture Volume' 		value.0 -24 		value.1 -24 		comment { 			access 'read write' 			type INTEGER 			count 2 			range '-24 - 24' 		} 	} 	control.12 { 		iface MIXER 		name 'Front Mic Capture Volume' 		value.0 -24 		value.1 -24 		comment { 			access 'read write' 			type INTEGER 			count 2 			range '-24 - 24' 		} 	} 	control.13 { 		iface MIXER 		name 'Line Capture Volume' 		value.0 -24 		value.1 -24 		comment { 			access 'read write' 			type INTEGER 			count 2 			range '-24 - 24' 		} 	} 	control.14 { 		iface MIXER 		name 'Capture Source' 		value Mic 		comment { 			access 'read write' 			type ENUMERATED 			count 1 			item.0 Mic 			item.1 Aux 			item.2 'Front Mic' 			item.3 Line 		} 	} 	control.15 { 		iface MIXER 		name 'ADC High-pass Filter Capture Enum' 		value Active 		comment { 			access 'read write' 			type ENUMERATED 			count 1 			item.0 Active 			item.1 Frozen 		} 	} } --endcollapse--   !!All Loaded Modules !!------------------  Module snd_seq_dummy vesafb bnep rfcomm bluetooth binfmt_misc nvidia ppdev joydev dcdbas snd_oxygen snd_oxygen_lib snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse serio_raw snd parport_pc soundcore lp parport usbhid hid ahci libahci tg3   !!ALSA/HDA dmesg !!------------------    
```

---

### Post by mjhouska on 2012-02-04
been here and done that. the answer is Ubuntu studio 10.04 LTS with the rt kernel. haven't tried optimizing jack yet, but it works and I'm doing stuff.  disregard.  I forgot that this might be card specific. but 10.04 was a lot nicer to me.

---

### Post by CivilizationII on 2012-02-20
Assuming your xonar card is working (i do not have one, can't help here), the best is to modify jack hardware selector via qjackctl setup panel.

Stop jackd

Change 'Interface' from 'default' to HW0 (if bios have motherboard sound chipset disabled) or HW1 if your running the two sound cards (xonar and motherboard's one).

Then restart jackd. Should solve the problem.

If the problem is not solved at this point, type command:

sudo alsamixer> sudo alsamixer

Use < F6 > key to force the hardware selection, then choose '0' or '1' whatever number is pointing to your Xonar card (the name of the card is wrote beside the number)

Then in qjackctl, whatever was the number choose to point on Xonar, select the same for Interface: HW0 or HW1

---


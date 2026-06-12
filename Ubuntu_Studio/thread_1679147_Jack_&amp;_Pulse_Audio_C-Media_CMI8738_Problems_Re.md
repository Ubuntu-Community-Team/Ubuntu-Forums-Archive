---
title: "Jack &amp; Pulse Audio C-Media CMI8738 Problems Recording 10.10"
date: 2011-01-31
forum: Ubuntu Studio
---

### Post by Thebighat99 on 2011-01-31
Hi,
I am getting more confused every time I read something. I tried killing Pulseaudi from terminal pulseaudi -k. It din't like that. I tried changing some of settings in Jack setup no luck. Its funny because hydrogen drum works fine, Ardour works but just cant record from the line-in (capture_2 least that is what I think Line-in is) I know capture_1 works with microphone. I have recorded from Line-in on this sound card with Windows & audacity. Best I could get from Line-in was very bad static bass note. I am very new to all this so please talk in baby Linux language :))

Thank you for your time and any help in advance. 

:This is all my Information that I could put together. Sorry if its over kill.:

Problem: No line-in
Problem: Can not open Rakarrack
Problem: I think something is hogging the sound card but can not find it less it 
         is Pulseaudi. 

Ubuntu-studio 10.10(Maverick Meerkat) installed
PC (Intel x86) alternate install DVD

Processor
Model : AMD Athlon(tm) XP 2000+
Speed : 1.68GHz
Cores per Processor : 1 Unit(s)
Threads per Core : 1 Unit(s)
Integrated Data Cache : 64kB, Synchronous, Write-Back, 2-way, 64 byte line size
L2 On-board Cache : 256kB, ECC, Synchronous, Write-Back, 16-way, 64 byte line size

Computer
Mainboard : Gigabyte Technology Co., LTD GA-7DX+
BIOS : Award (Phoenix) 6.00 PG 05/22/2002
Bus(es) : ISA AGP PCI IMB USB i2c/SMBus
Multi-Processor (MP) Support : No
Multi-Processor Advanced PIC (APIC) : Yes
Total Memory : 1.25GB DDR

Chipset
Model : AMD AMD-761 CPU to PCI Bridge
Front Side Bus Speed : 2x 134MHz (268MHz)
Total Memory : 1.25GB DDR
Memory Bus Speed : 2x 134MHz (268MHz)

Video System
Video Adapter : NVIDIA GeForce3 Ti 200 (PS1.1, VS1.1, AGP 2.00)

Logical Storage Devices
Hard Disk (C:) : 24GB (NTFS) @ Seagate ST340823A (40GB, ATA100, 3.5", 512kB Cache)
New Volume (D:) : 14GB (NTFS) @ QUANTUM FIREBALLlct15 15 15GB (ATA66, 418kB Cache)
Optical Drive (E:) : N/A @ CRD-8483B (ATA33, 128kB Cache)
Optical Drive (F:) : N/A @ LITE-ON COMBO SOHC-4836K (ATA44, DVD+-R, CD-RW, 2MB Cache)
3.5" 1.44MB (A:) : N/A

Peripherals
LPC Hub Controller 1 : VIA VT82C686/A PCI to ISA Bridge
Audio Device : C-Media Electronics CMI8738/C3DX PCI Audio Device
Audio Codec : Gammagraphx 0000h
Audio Codec : Gammagraphx 0000h
Disk Controller : VIA VT82Cxxxx EIDE Controller (All VIA Chipsets)
USB Controller 1 : First International Computer VIA Rev 0 USB UHCI Controller
USB Controller 2 : First International Computer VIA Rev 0 USB UHCI Controller
SMBus/i2c Controller 1 : VIA PX5 SMBus

Network Services
Network Adapter : Linksys LNE100TX Fast Ethernet Adapter(LNE100TX v4) - Packet Scheduler Miniport (Ethernet, 100Mbps)

chris@Chrisroom1:~$ ulimit -r

99

chris@Chrisroom1:~$ ulimit -l

unlimited

chris@Chrisroom1:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

chris@Chrisroom1:~$ lspci -v

00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
    Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at e400 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: C-Media PCI
    Kernel modules: snd-cmipci

chris@Chrisroom1:~$ sudo modinfo soundcore

filename:       /lib/modules/2.6.35-25-generic/kernel/sound/soundcore.ko
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     EF16BDAFD00EF5D7A386369
depends:        
vermagic:       2.6.35-25-generic SMP mod_unload modversions 686 

chris@Chrisroom1:~$ cat /proc/interrupts
           CPU0       
  0:         46   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  6:          2   IO-APIC-edge      floppy
  8:          0   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 10:       8384   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb2
 12:          4   IO-APIC-edge      i8042
 14:       9853   IO-APIC-edge      pata_via
 15:       2572   IO-APIC-edge      pata_via
 16:       1065   IO-APIC-fasteoi   eth0
 19:        633   IO-APIC-fasteoi   CMI8738-MC6
NMI:          0   Non-maskable interrupts
LOC:      23742   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          2   Machine check polls
ERR:          0
MIS:          0

chris@Chrisroom1:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: raw midi
  5: [ 0- 2]: digital audio playback
  6: [ 0- 2]: digital audio capture
  7: [ 0- 1]: digital audio playback
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0- 0]: hardware dependent
 11: [ 0]   : control

chris@Chrisroom1:~$ lsmod |grep snd
snd_cmipci             30469  3 
gameport                9327  1 snd_cmipci
snd_pcm                71475  2 snd_cmipci
snd_page_alloc          7120  1 snd_pcm
snd_opl3_lib            8850  1 snd_cmipci
snd_hwdep               5040  1 snd_opl3_lib
snd_mpu401_uart         5661  1 snd_cmipci
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          5744  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  14 snd_cmipci,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd

lsmod |grep snd_cmipci
snd_cmipci             30469  3 
gameport                9327  1 snd_cmipci
snd_pcm                71475  2 snd_cmipci
snd_opl3_lib            8850  1 snd_cmipci
snd_mpu401_uart         5661  1 snd_cmipci
snd                    49038  14 snd_cmipci,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


sudo grep cmipci /var/log/syslog :this log was very long only thing that changed
                                  was the number so i dint post the hole 
                                  thing if i need to let me know.

oppy tulip pata_via
Jan 26 10:56:09 Chrisroom1 kernel: [   18.416844] Modules linked in: snd_cmipci gameport nouveau(+) snd_pcm snd_page_alloc snd_opl3_lib snd_hwdep snd_mpu401_uart snd_seq_midi ttm snd_rawmidi drm_kms_helper snd_seq_midi_event snd_seq ppdev snd_timer snd_seq_device drm psmouse snd joydev serio_raw i2c_algo_bit amd_k7_agp parport_pc via686a soundcore shpchp i2c_viapro agpgart lp parport usbhid hid floppy tulip pata_via


:Before clicking on jack:

chris@Chrisroom1:~$ ls /dev/snd

by-path    hwC0D0    pcmC0D0c  pcmC0D1p  pcmC0D2p  timer
controlC0  midiC0D0  pcmC0D0p  pcmC0D2c  seq

chris@Chrisroom1:~$ lsof /dev/snd/*

COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pulseaudi 2019 chris  mem    CHR  116,8          7074 /dev/snd/pcmC0D0p
pulseaudi 2019 chris   20u   CHR 116,11      0t0 7077 /dev/snd/controlC0
pulseaudi 2019 chris   26u   CHR 116,11      0t0 7077 /dev/snd/controlC0
pulseaudi 2019 chris   39u   CHR  116,8      0t0 7074 /dev/snd/pcmC0D0p

chris@Chrisroom1:~$ fuser /dev/snd/*

/dev/snd/controlC0:   2019
/dev/snd/pcmC0D0p:    2019m

:After clicking on Jack this infromation in message - Jack Audio Connection Kit:

13:05:45.426 Patchbay deactivated.
13:05:45.428 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
13:05:45.673 ALSA connection graph change.
13:05:45.861 ALSA connection change.


:After clicking on Jack opening program:

chris@Chrisroom1:~$ ls /dev/snd

by-path    hwC0D0    pcmC0D0c  pcmC0D1p  pcmC0D2p  timer
controlC0  midiC0D0  pcmC0D0p  pcmC0D2c  seq

chris@Chrisroom1:~$ lsof /dev/snd/*

COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pulseaudi 2019 chris  mem    CHR  116,8          7074 /dev/snd/pcmC0D0p
pulseaudi 2019 chris   20u   CHR 116,11      0t0 7077 /dev/snd/controlC0
pulseaudi 2019 chris   26u   CHR 116,11      0t0 7077 /dev/snd/controlC0
pulseaudi 2019 chris   39u   CHR  116,8      0t0 7074 /dev/snd/pcmC0D0p
qjackctl  2164 chris   23u   CHR  116,3      0t0 6921 /dev/snd/seq

chris@Chrisroom1:~$ fuser /dev/snd/*
/dev/snd/controlC0:   2019
/dev/snd/pcmC0D0p:    2019m
/dev/snd/seq:         2198


:After Starting Jack this information in message - Jack Audio Connection Kit:

13:07:24.010 Startup script...
13:07:24.011 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
13:07:24.416 Startup script terminated with exit status=32512.
13:07:24.418 JACK is starting...
13:07:24.422 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p256 -n2 -D -Cplughw:0
no message buffer overruns
13:07:24.540 JACK was started with PID=2062.
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|plughw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver CMI8738-MC6 running on card 0 - C-Media CMI8738 (model 55) at 0xe400, irq 19
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit float little-endian
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
13:07:26.672 Server configuration saved to "/home/chris/.jackdrc".
13:07:26.673 Statistics reset.
13:07:26.703 Client activated.
13:07:26.706 JACK connection change.
13:07:26.725 JACK connection graph change.


:After Starting Jack:

chris@Chrisroom1:~$ ls /dev/snd

by-path    hwC0D0    pcmC0D0c  pcmC0D1p  pcmC0D2p  timer
controlC0  midiC0D0  pcmC0D0p  pcmC0D2c  seq

chris@Chrisroom1:~$ lsof /dev/snd/*

COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pulseaudi 2019 chris   20u   CHR 116,11      0t0 7077 /dev/snd/controlC0
pulseaudi 2019 chris   26u   CHR 116,11      0t0 7077 /dev/snd/controlC0
qjackctl  2164 chris   23u   CHR  116,3      0t0 6921 /dev/snd/seq
jackd     2174 chris  mem    CHR  116,8          7074 /dev/snd/pcmC0D0p
jackd     2174 chris  mem    CHR  116,9          7075 /dev/snd/pcmC0D0c
jackd     2174 chris    6u   CHR 116,11      0t0 7077 /dev/snd/controlC0
jackd     2174 chris    8u   CHR  116,8      0t0 7074 /dev/snd/pcmC0D0p
jackd     2174 chris    9u   CHR  116,9      0t0 7075 /dev/snd/pcmC0D0c

chris@Chrisroom1:~$ fuser /dev/snd/*

/dev/snd/controlC0:   2019  2209
/dev/snd/pcmC0D0c:    2209m
/dev/snd/pcmC0D0p:    2209m
/dev/snd/seq:         2198

:Trying to start Rakarrack:

chris@Chrisroom1:~$ sudo rakarrack

rakarrack 0.5.8_Equinox - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|plughw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver CMI8738-MC6 running on card 0 - C-Media CMI8738 (model 55) at 0xe400, irq 19
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
JackTemporaryException : now quits...
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
Cannot make a jack client, is jackd running?
Usage: rakarrack [OPTION]

  -h ,     --help              display command-line help and exit
  -n ,     --no-gui              disable GUI
  -l File, --load=File              loads preset
  -b File, --bank=File              loads bank
  -p #,    --preset=#              set preset
  -x, --dump-preset-names          prints bank of preset names and IDs

FLTK options are:

  -bg2 color
  -bg color
  -di[splay] host:n.n
  -dn[d]
  -fg color
  -g[eometry] WxH+X+Y
  -i[conic]
  -k[bd]
  -na[me] classname
  -nod[nd]
  -nok[bd]
  -not[ooltips]
  -s[cheme] scheme (plastic,none,gtk+)
  -ti[tle] windowtitle
  -to[oltips]

:Stoping Jack:

Messages - JACK Audio Connection Kit

17:57:08.686 JACK is stopping...
jack main caught signal 15
Released audio card Audio0
audio_reservation_finish
17:57:08.922 JACK was stopped successfully.
17:57:08.923 Post-shutdown script...
17:57:08.924 killall jackd
jackd: no process found
17:57:09.353 Post-shutdown script terminated with exit status=256.

:Boot log:

fsck from util-linux-ng 2.17.2
/dev/sda5: clean, 219110/610800 files, 1211376/2441472 blocks (check in 5 mounts)
 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
 [33m*[39;49m PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Enabling additional executable binary formats binfmt-support       [80G 
[74G[ OK ]
 * Checking battery state...       [80G 

:Syslog.1: this was over and over agin in my log?

6:01 Chrisroom1 anacron[836]: Job `cron.daily' terminated
Jan 29 11:26:01 Chrisroom1 anacron[836]: Normal exit (1 job run)
Jan 29 11:49:10 Chrisroom1 pulseaudio[1445]: alsa-sink.c: Error opening PCM device iec958:0: Device or resource busy
Jan 29 11:49:10 Chrisroom1 pulseaudio[1445]: sink-input.c: Failed to create sink input: sink is suspended.

:user.log:

Jan 30 11:42:40 Chrisroom1 pulseaudio[2730]: pid.c: Daemon already running.
Jan 30 11:42:40 Chrisroom1 pulseaudio[2731]: pid.c: Daemon already running.

:user.log1: There is lot of this in the log just like this.

Jan 29 11:49:10 Chrisroom1 pulseaudio[1445]: alsa-sink.c: Error opening PCM device iec958:0: Device or resource busy
Jan 29 11:49:10 Chrisroom1 pulseaudio[1445]: sink-input.c: Failed to create sink input: sink is suspended.
Jan 29 11:49:10 Chrisroom1 pulseaudio[1445]: alsa-sink.c: Error opening PCM device iec958:0: Device or resource busy
Jan 29 11:49:10 Chrisroom1 pulseaudio[1445]: sink-input.c: Failed to create sink input: sink is suspended.

---

### Post by Pablo_F on 2011-01-31
Hi, 

You have to run rakarrack without sudo, as a user so, just *rakarrack*. 

Make jack use hw:0 instead of plughw:0 (Interface field of qjackctl).

Append -S to the jackd command (/usr/bin/jackd -S). Synchronous mode seems to work better in jackd2.

Don't demand a very low latency. Well, maybe you can work at 256 frames / period, but try to start conservative, if needed, decrease it. 

Afaik, some cheap soundcards work better at 48 KHz (I don't know if this is the case with yours).

I don't see anything wrong with the rest of your system (although I haven't read nor understood every single line).

Cheers, Pablo

---

### Post by Thebighat99 on 2011-02-01
Howdy :p
I tried running rakarrack without sudo but it did nothing. I mean the screen did not even flicker and in terminal it just put a blank return.  The only line in jack that changed was[COLOR=#cc9966] 09:09:34.734 JACK connection graph change.[/COLOR] So to try and see what was going on I ran it with sudo. I tried what you said to do but it is still not working.

---

### Post by Pablo_F on 2011-02-01
Weird. Anyway, rakarrack _must_ be run as the same user that runs jackd. If you run rakarrack with sudo, the rakarrack user is "root" instead of "your_username", who is running jackd.

I suggest you create a sourceforge account and ask in their forums: [http://sourceforge.net/projects/rakarrack/forums](http://sourceforge.net/projects/rakarrack/forums)

They have a mailing list aswell: [http://sourceforge.net/mail/?group_id=215888](http://sourceforge.net/mail/?group_id=215888)

Cheers! Pablo

---


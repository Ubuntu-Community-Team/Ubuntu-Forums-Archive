---
title: "Stuck on audio/Presonus audigy 2 zs"
date: 2010-01-17
forum: Ubuntu Studio
---

### Post by caddyjoe77 on 2010-01-17
I have been messing with this for a few weeks now and have basically run out of options as far as i know.  

I received a presonus firebox for Christams, and I used to be able to get it to feed into ardour and record, but since i have been trying to get my sound to play on my speakers i plugged in an XLR cable from the headphone jack to the audigy 2.  I made some irq changes, because the way it appears to me; i have an alsa/jack problem.  I hope this is a common problem :)   My ultimate goal is to get the firebox output into the SB audigy 2 ZS input so i can hear myself when i play my bass.   Below is what i have done to try and get this to work, but in the process i have severely hosed myself.  

So, i have followed the instructions, and i am in the audio and video group.  That worked as it was supposed to with ardour and i could record but not hear anything because when i would start jack using qjackctl it would kill my speaker output.  I thought that perhaps i could fix the issue by updating the sound drivers from here: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)  I installed all the drivers: [[PCI]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-PCI") [[ANALOGio]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-ANALOGio") [[MIDIio]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-MIDIio") [[48kHz]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-48kHz") [[Wavetable]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-Wavetable") [[HWMIX]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-HWMIX") .  That part at least made my PC recognize that it was a sound blaster audigy.  

Then i went to the store and picked up an XLR cable to feed from the headphone jack on the presonus to the input on the creative but i get nothing.  

Then i did some research and made some changes to the IRQ settings using the rtirq script from here: [http://www.rncbc.org/jack/](http://www.rncbc.org/jack/)  This made sense to me, because if the irq's were fighting iwould have thought this should have fixed it.  

Now, my PC has no idea that i even have a sound card anymore.  At least through the sound control panel.  No input/output or hardware is shown anymore.  

jackd stays running via qjackctl only if i leave it at the following settings(I still get many xruns though) 
[IMG]http://i216.photobucket.com/albums/cc132/thevegashotgolfer/Screenshot-Setup-JACKAudioConnectio.png[/IMG]  
If i change it from freebob to firewire it immediately crashes.  Also, if i change the devices jack crashes as well.  

here is my /etc/default.jackd file:
```
cat jackd
# Set to "yes" to start jackd at boot
START_DAEMON=yes

# The jackd process will run under this user
USER=root

# Options to pass to jackd
OPTIONS="-R -d alsa -d hw"
```I have also tried using audacity, for the sake of simplicity(i think?) here is what it reports me as having:
```
==============================
Default capture device number: 17
Default playback device number: 17
==============================
Device ID: 0
Device name: ALSA: SB Audigy 2 ZS [SB0360]: ADC Capture/Standard PCM Playback (hw:0,0)
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 1
Device name: ALSA: SB Audigy 2 ZS [SB0360]: Mic Capture (hw:0,1)
Input channels: 2
Output channels: 0
Low Input Latency: 0.064000
Low Output Latency: -1.000000
High Input Latency: 0.256000
High Output Latency: -1.000000
Supported Rates:
==============================
Device ID: 2
Device name: ALSA: SB Audigy 2 ZS [SB0360]: Multichannel Capture/PT Playback (hw:0,2)
Input channels: 16
Output channels: 0
Low Input Latency: 0.010667
Low Output Latency: -1.000000
High Input Latency: 0.042667
High Output Latency: -1.000000
Supported Rates:
==============================
Device ID: 3
Device name: ALSA: SB Audigy 2 ZS [SB0360]: Multichannel Playback (hw:0,3)
Input channels: 0
Output channels: 16
Low Input Latency: -1.000000
Low Output Latency: 0.010667
High Input Latency: -1.000000
High Output Latency: 0.042667
Supported Rates:
    48000
==============================
Device ID: 4
Device name: ALSA: SB Audigy 2 ZS [SB0360]: p16v (hw:0,4)
Input channels: 2
Output channels: 8
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
    192000
==============================
Device ID: 5
Device name: ALSA: front
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 6
Device name: ALSA: rear
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 7
Device name: ALSA: center_lfe
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 8
Device name: ALSA: side
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 9
Device name: ALSA: surround40
Input channels: 0
Output channels: 4
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 10
Device name: ALSA: surround41
Input channels: 0
Output channels: 128
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 11
Device name: ALSA: surround50
Input channels: 0
Output channels: 128
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 12
Device name: ALSA: surround51
Input channels: 0
Output channels: 6
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 13
Device name: ALSA: surround71
Input channels: 0
Output channels: 8
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 14
Device name: ALSA: iec958
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 15
Device name: ALSA: spdif
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
==============================
Device ID: 16
Device name: ALSA: pulse
Input channels: 32
Output channels: 32
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
    192000
==============================
Device ID: 17
Device name: ALSA: default
Input channels: 32
Output channels: 32
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
    192000
==============================
Device ID: 18
Device name: OSS: /dev/dsp
Input channels: 0
Output channels: 16
Low Input Latency: 0.000000
Low Output Latency: 0.011610
High Input Latency: 0.000000
High Output Latency: 0.046440
Supported Rates:
==============================
Device ID: 19
Device name: JACK Audio Connection Kit: system
Input channels: 6
Output channels: 8
Low Input Latency: 0.023220
Low Output Latency: 0.046440
High Input Latency: 0.023220
High Output Latency: 0.046440
Supported Rates:
    44100
==============================
Selected capture device: 17 - 
Selected playback device: 17 - 
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
    192000
==============================
Available mixers:
==============================
Available capture sources:
==============================
Available playback volumes:
0 - Master:0
1 - Bass:0
2 - Treble:0
3 - 3D Control Sigmatel - Depth:0
4 - PCM:0
5 - PCM Center:0
6 - PCM Front:0
7 - PCM LFE:0
8 - PCM Side:0
9 - PCM Surround:0
10 - Front:0
11 - Surround:0
12 - Center:0
13 - LFE:0
14 - Side:0
15 - Synth:0
16 - Line:0
17 - Line2:0
18 - CD:0
19 - Mic:0
20 - Phone:0
21 - IEC958 Optical:0
22 - Aux:0
23 - Aux2:0
24 - Analog Mix:0
25 - Audigy CD:0
26 - Beep:0
27 - HD Analog Center/LFE:0
28 - HD Analog Front:0
29 - HD Analog Rear:0
30 - HD Analog Side:0
31 - HD SPDIF Center/LFE:0
32 - HD SPDIF Front:0
33 - HD SPDIF Rear:0
34 - HD SPDIF Side:0
==============================
Capture volume is emulated
Playback volume is native
```i have attached a rudimentary drawing of what i was trying to accomplish, i hope that it helps

Anything you all can do to help would be greatly appreciated.  Thanks in advance

---

### Post by AutoStatic on 2010-01-18
Hello caddyjoe77,

You can not use two driver backends (FFADO or Freebob for your Presonus and ALSA for your Audigy) at the same time with JACK, at least not with the version of JACK that comes with =< 9.10. Maybe it can be done with jack2, not sure. Or I'm totally wrong and it can be done but in a way I'm not aware of.

---

